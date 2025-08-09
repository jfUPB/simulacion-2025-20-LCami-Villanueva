# Unidad 2


## 🛠 Fase: Apply
- Describe el concepto de tu obra generativa.
  >Mi obra generativa simulara el recorrido de granos de café en distintas etapas de maduración, representadas mediante un cambio progresivo de color conforme avanzan en el espacio. El movimiento de cada grano está basado en principios de motion 101, aplicando vectores de posición, velocidad y aceleración.
Incorporaré un algoritmo de aceleración basado en ruido Perlin, para hacer trayectorias suaves y orgánicas. Para que los granos se desplacen de forma fluida pero única, reforzando la sensación de un proceso natural. 

- ¿Cómo piensas aplicar el marco MOTION 101 y por qué?
  > Mi obra generativa aplicará el marco MOTION 101 a través del uso de vectores de posición, velocidad y aceleración para controlar el movimiento de cada grano de café. Cada partícula se representará como un objeto autónomo que actualiza su estado en cada cuadro.
Esto permitirá simular un movimiento coherente y continuo en el tiempo, lo cual es esencial para representar procesos orgánicos como el desplazamiento y transformación de los granos.
  
- ¿Qué algoritmo de aceleración vas a utilizar? ¿Por qué?
  > En esta obra generativa, implementaré un algoritmo de aceleración basado en ruido Perlin (Perlin noise). Este algoritmo permitirá generar variaciones suaves y continuas en la aceleración de cada grano de café, a diferencia de la aleatoriedad abrupta. El ruido Perlin producirá un movimiento más orgánico, fluido y natural.

  > Decidí utilizar este algoritmo porque, a diferencia de las aceleraciones constantes o aleatorias, el ruido Perlin permite una variabilidad controlada. Esto me da la posibilidad de introducir complejidad en el     comportamiento de las partículas sin perder coherencia visual, y genera trayectorias impredecibles pero suaves, lo cual enriquece la estética del sistema.

- El contenido generado debe ser interactivo. Puedes utilizar mouse, teclado, cámara, micrófono, etc, para variar los parámetros del algoritmo en tiempo real.
  > **Interactividad:***
  >   - Mouse: Si el cursor se acerca a un grano, este se “infecta”: se vuelve negro, se reduce de tamaño y ya no cambia de color al avanzar de etapa.
  >   - v: Aumenta la velocidad horizontal (velocity.x) de todos los granos en un 25%, de forma acumulativa.
  >   - a: Activa la aceleración basada en ruido Perlin, haciendo que la velocidad de los granos crezca suavemente con variaciones orgánicas.
  >   - s: Desactiva el Perlin y reinicia la aceleración, deteniendo el crecimiento de la velocidad.
  >   - p: Pausa o reanuda la creación automática de nuevos granos desde el borde izquierdo de la pantalla.
  
- El código de la aplicación.
``` javascript
       let grains = [];
let margin = 20;
let minDistance = 12;
let autoAdd = true;
let usePerlinAcceleration = false;

class CoffeeGrain {
  constructor(x, y, angle, stageColorFns) {
    this.position = createVector(x, y);
    this.velocity = createVector(0.3, 0);
    this.acceleration = createVector(0, 0);
    this.angle = angle;
    this.stage = 0;
    this.colors = stageColorFns.map(fn => fn());
    this.currentColor = this.colors[this.stage];
    this.originalColors = [...this.colors];
    this.infected = false;
    this.size = { w: 10, h: 6 };
    this.noiseOffset = random(1000); // Para variar el Perlin
  }

  update() {
    if (usePerlinAcceleration) {
      // Calcula aceleración Perlin y la aplica solo en X
      let ax = map(noise(this.noiseOffset), 0, 1, 0, 0.05); // aceleración suave
      this.acceleration.x = ax;
      this.noiseOffset += 0.01; // Avanza el ruido con el tiempo
    }

    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);

    if (!this.infected) {
      if (this.position.x > 150 && this.stage === 0) {
        this.stage = 1;
        this.currentColor = this.colors[this.stage];
      }
      if (this.position.x > 300 && this.stage === 1) {
        this.stage = 2;
        this.currentColor = this.colors[this.stage];
      }
      if (this.position.x > 450 && this.stage === 2) {
        this.stage = 3;
        this.currentColor = this.colors[this.stage];
      }
    }
  }

  checkHover() {
    if (this.infected) return;

    let d = dist(mouseX, mouseY, this.position.x, this.position.y);
    if (d < 15) {
      this.infected = true;
      this.currentColor = color(20, 20, 20);
      this.size = { w: 6, h: 4 };
    }
  }

  show() {
    fill(this.currentColor);
    noStroke();
    push();
    translate(this.position.x, this.position.y);
    rotate(this.angle);
    ellipse(0, 0, this.size.w, this.size.h);
    pop();
  }
}

function setup() {
  createCanvas(600, 400);
  background(255);

  for (let i = 0; i < 400; i++) {
    createGrain(random(-200, width), random(margin, height - margin));
  }
}

function draw() {
  background(255);

  if (autoAdd) {
    for (let i = 0; i < 2; i++) {
      tryToAddGrain();
    }
  }

  for (let grain of grains) {
    grain.update();
    grain.checkHover();
    grain.show();
  }
}

function keyPressed() {
  // Aumentar velocidad de todos los granos
  if (key === 'v' || key === 'V') {
    for (let grain of grains) {
      grain.velocity.x *= 1.25;
    }
  }

  // Activar aceleración Perlin
  if (key === 'a' || key === 'A') {
    usePerlinAcceleration = true;
  }

  // Detener aceleración (reset)
  if (key === 's' || key === 'S') {
    usePerlinAcceleration = false;
    for (let grain of grains) {
      grain.acceleration.set(0, 0);
    }
  }

  // Pausar/reanudar creación automática de granos
  if (key === 'p' || key === 'P') {
    autoAdd = !autoAdd;
  }
}

function tryToAddGrain() {
  let x = random(-100, 0);
  let y = random(margin, height - margin);

  for (let grain of grains) {
    if (dist(x, y, grain.position.x, grain.position.y) < minDistance) {
      return;
    }
  }

  createGrain(x, y);
}

function createGrain(x, y) {
  let angle = noise(frameCount * 0.01 + y * 0.1) * TWO_PI;
  let stageColorFns = [greenTone, redTone, beigeTone, brownTone];
  grains.push(new CoffeeGrain(x, y, angle, stageColorFns));
}

// === COLORES ===

function greenTone() {
  return color(
    constrain(randomGaussian(50, 30), 0, 120),
    constrain(randomGaussian(160, 30), 80, 220),
    constrain(randomGaussian(60, 20), 0, 120)
  );
}

function redTone() {
  return color(
    constrain(randomGaussian(200, 30), 100, 255),
    constrain(randomGaussian(60, 25), 0, 100),
    constrain(randomGaussian(60, 25), 0, 100)
  );
}

function beigeTone() {
  return color(
    constrain(randomGaussian(230, 10), 210, 250),
    constrain(randomGaussian(210, 10), 190, 230),
    constrain(randomGaussian(170, 10), 160, 200)
  );
}

function brownTone() {
  let r = constrain(randomGaussian(120, 20), 90, 160);
  let g = constrain(randomGaussian(80, 15), 60, 110);
  let b = constrain(randomGaussian(50, 15), 30, 90);
  return color(r, g, b);
}
```
  
- Un enlace al proyecto en el editor de p5.js.
  > https://editor.p5js.org/LCami-Villanueva/sketches/vq6OD-2aq
- Una captura de pantalla representativa de tu pieza de arte generativo.
  <img width="922" height="613" alt="image" src="https://github.com/user-attachments/assets/cddf0ed1-4063-4a71-bf6d-4ca4ab69fea8" />
