# Evidencias de la unidad 4
### [Set-Seek](https://www.notion.so/Simulaci-n-Para-Sistemas-Interactivos-25f42dfbaef680c4bd7ff48838e1f94c?source=copy_link)
## Explicación conceptual de la obra
### Introducción:
>Esta obra simula un cardumen de peces que interactúa dinámicamente con anzuelos en un entorno visual y reactivo. Cada pez se mueve de manera orgánica gracias a fuerzas naturales simuladas, como el Perlin noise y la aceleración basada en Motion 101. Los anzuelos actúan como elementos de interacción que modifican el comportamiento de los peces mediante fuerzas de atracción y efectos de péndulo o resorte, permitiendo al usuario explorar cómo los principios físicos y algorítmicos influyen en un sistema vivo simulado.
* ¿Qué concepto de la unidad 4 y cómo lo aplicaste en la obra?
> En mi simulación, el anzuelo inicialmente se mueve como un péndulo, usando ángulo, velocidad y aceleración angular. Cuando el usuario arrastra el anzuelo con el mouse, se activa el modo resorte, usando la Ley de Hooke para que se comporte como un hilo elástico. Esto hace que el anzuelo se mueva de manera fluida e interactiva, aunque en la vida real no se comporta exactamente así.
* ¿Qué concepto de la unidad 3 y cómo lo aplicaste en la obra?
> Cada pez calcula la fuerza de atracción hacia el anzuelo, usando la fórmula <img width="100" height="25" alt="image" src="https://github.com/user-attachments/assets/008c6afb-6b56-4c80-aba9-f4c2e181e589" />
.Esta fuerza se aplica sobre la aceleración de cada pez, haciendo que sean atraídos de manera natural. Si se aplica velocidad tangencial, algunos peces incluso pueden orbitar alrededor del anzuelo, simulando un comportamiento más realista.
* ¿Qué concepto de la unidad 2 y cómo lo aplicaste en la obra?
> Cada pez tiene aceleración, velocidad y posición. La aceleración se suma a la velocidad y esta a la posición (vel.add(acc) → pos.add(vel)), integrando las fuerzas y generando movimiento fluido. El Perlin noise también actúa como una fuerza adicional que hace que el nado se vea orgánico cuando no hay anzuelos.
* ¿Qué concepto de la unidad 1 y cómo lo aplicaste en la obra?
> Para la generación inicial, los peces se crean en 4 grupos distintos usando random y sus posiciones alrededor del centro se calculan con random gaussiano, creando dispersión natural. También se usa random gaussiano para los colores de cada pez y Perlin noise para su movimiento natural, evitando que todos los peces se muevan igual.
## ¿Cómo resolviste la interacción?
> La interacción con el usuario se implementa así:
> - Tecla A: crea un nuevo anzuelo en la posición actual del mouse; se pueden crear varios anzuelos.
> - Tecla D: elimina el último anzuelo creado; los peces cercanos dejan de sentir su atracción y se alejan según su velocidad acumulada.
> - Tecla X: elimina todos los anzuelos, liberando a todos los peces al instante.
> - Mouse: si se arrastra un anzuelo, este se comporta como un resorte; al soltarlo vuelve a su movimiento de péndulo

## Enlace a la obra en el editor de p5.js

[Aquí está mi obra](https://editor.p5js.org/LCami-Villanueva/sketches/xY2GllbPz)

## Código de la obra 

``` js
// --- Variables Globales ---
let peces = []; // Array para almacenar los objetos Pez
let anzuelos = []; // Array para almacenar los objetos Anzuelo
let numPeces = 200; // Número de peces en el cardumen
let perlinNoiseOffset = 0;
let colorMode = 0; // 0: Cálidos, 1: Fríos, 2: Mixtos, 3: Blancos

// --- Clases ---
class Pez {
  constructor(x, y) {
    this.pos = createVector(x, y);
    this.vel = createVector(0, 0);
    this.acc = createVector(0, 0);
    this.size = random(2, 4);
    this.colorModeInicial = floor(random(0, 4)); 
    this.updateColor(this.colorModeInicial);
  }

  // Aplica una fuerza al pez
  applyForce(force) {
    this.acc.add(force);
  }

  // Actualiza la posición y velocidad del pez
  update() {
    // Movimiento con Perlin noise para un efecto de nado natural
    let noiseVel = createVector(
      map(noise(this.pos.x * 0.01, this.pos.y * 0.01, frameCount * 0.005), 0, 1, -1, 1),
      map(noise(this.pos.y * 0.01, this.pos.x * 0.01, frameCount * 0.005), 0, 1, -1, 1)
    );
    this.applyForce(noiseVel.mult(0.1));

    // Moverse según la velocidad y aceleración
    this.vel.add(this.acc);
    this.pos.add(this.vel);
    this.acc.mult(0); // Reinicia la aceleración

    // Limita la velocidad
    this.vel.limit(2);

    // Evita que los peces salgan de la pantalla
    if (this.pos.x > width) this.pos.x = 0;
    if (this.pos.x < 0) this.pos.x = width;
    if (this.pos.y > height) this.pos.y = 0;
    if (this.pos.y < 0) this.pos.y = height;
  }

  // Dibuja el pez en el lienzo
  display() {
    noStroke();
    fill(this.color);
    ellipse(this.pos.x, this.pos.y, this.size, this.size);
  }

  // Asigna un color al pez según el modo de color global
  
   updateColor(modo = colorMode) { 
      let cm = modo;
      switch (cm) {
      case 0: // Cálidos
        this.color = color(
          constrain(randomGaussian(230, 15), 200, 255),
          constrain(randomGaussian(80, 20), 0, 120),
          constrain(randomGaussian(60, 20), 0, 120),
          150
        );
        break;

      case 1: // Fríos
        this.color = color(
          constrain(randomGaussian(60, 20), 0, 120),
          constrain(randomGaussian(200, 20), 150, 255),
          constrain(randomGaussian(230, 15), 180, 255),
          150
        );
        break;

      case 2: // Mezclados
        this.color = color(
          constrain(randomGaussian(128, 80), 0, 255),
          constrain(randomGaussian(128, 80), 0, 255),
          constrain(randomGaussian(128, 80), 0, 255),
          150
        );
        break;

      case 3: // Blancos
        this.color = color(
          constrain(randomGaussian(255, 10), 230, 255),
          constrain(randomGaussian(255, 10), 230, 255),
          constrain(randomGaussian(255, 10), 230, 255),
          150
        );
        break;
    }
  }

}

class Anzuelo {
  constructor(x, y) {
    this.pos = createVector(x, y);
    this.longitud = 150;
    this.angulo = PI / 3;
    this.velocidadAngular = 0;
    this.aceleracionAngular = 0;
    this.gravedad = 0.4;
    this.arrastre = 0.9;
    this.target = createVector(x, y);
    this.isSpring = false;
    this.k = 0.05; // Constante del resorte
    this.reposo = 150; // Longitud del resorte en reposo
    this.caidaFrame = frameCount; // Guarda el frame en el que cae el anzuelo
  }

  // Actualiza la posición del anzuelo
  update() {
    if (!this.isSpring) {
      // Movimiento de péndulo
      this.aceleracionAngular = (-this.gravedad / this.longitud) * sin(this.angulo);
      this.velocidadAngular += this.aceleracionAngular;
      this.velocidadAngular *= this.arrastre;
      this.angulo += this.velocidadAngular;
      this.pos.x = this.target.x + this.longitud * sin(this.angulo);
      this.pos.y = this.target.y + this.longitud * cos(this.angulo);
    } else {
      // Movimiento de resorte (Ley de Hooke)
      let desplazamiento = this.pos.dist(this.target) - this.reposo;
      let fuerzaResorte = createVector(this.target.x - this.pos.x, this.target.y - this.pos.y);
      fuerzaResorte.normalize();
      fuerzaResorte.mult(this.k * desplazamiento);
      this.pos.add(fuerzaResorte);
    }
  }

  // Dibuja el anzuelo
  display() {
    noFill();
    stroke(150, 150, 150, 150); // Color tenue para no distraer
    strokeWeight(1);
    line(this.target.x, this.target.y, this.pos.x, this.pos.y);
    fill(150, 150, 150, 200);
    ellipse(this.pos.x, this.pos.y, 10, 10);
  }

  // Mueve el punto de pivote del anzuelo
  moveTarget(x, y) {
    this.target.set(x, y);
  }
}

// --- Funciones P5.js ---

function setup() {
  createCanvas(890, 830);
  background(0, 0, 50);
  randomSeed(1);
  crearCardumenes();
}

function draw() {
  background(0, 0, 50, 50); // Fondo azul oscuro con trazo para efecto de rastro
  perlinNoiseOffset += 0.005;

  // Actualiza y dibuja cada anzuelo
  for (let anzuelo of anzuelos) {
    anzuelo.update();
    anzuelo.display();
  }

  // Actualiza y dibuja cada pez
  for (let pez of peces) {
    // Acumula las fuerzas de todos los anzuelos en cada pez
    for (let anzuelo of anzuelos) {
      let d = dist(pez.pos.x, pez.pos.y, anzuelo.pos.x, anzuelo.pos.y);
      let fuerzaAnzuelo;

      // Fuerza de repulsión inicial al "caer" el anzuelo
      if (frameCount - anzuelo.caidaFrame < 150) {
        fuerzaAnzuelo = p5.Vector.sub(pez.pos, anzuelo.pos);
        fuerzaAnzuelo.normalize();
        fuerzaAnzuelo.mult(500 / (d * d));
      } else {
        // Lógica de Atracción Gravitacional
        let fuerzaAtraccion = p5.Vector.sub(anzuelo.pos, pez.pos);
        let distancia = fuerzaAtraccion.mag();

        distancia = constrain(distancia, 5, 100);
        fuerzaAtraccion.normalize();

        let G = 1;
        let m1 = 1;
        let m2 = 50;
        let fuerza = (G * m1 * m2) / (distancia * distancia);
        fuerzaAtraccion.mult(fuerza);
        fuerzaAnzuelo = fuerzaAtraccion;

        // --------- NUEVA LÓGICA DE ORBITA ---------
        // Vector radial hacia el anzuelo
        let radial = p5.Vector.sub(anzuelo.pos, pez.pos);
        // Vector tangencial perpendicular
        let tangencial = createVector(-radial.y, radial.x);
        tangencial.normalize();

        // Aplicar velocidad tangencial solo una vez
        if (!pez.tieneTangencial) {
          tangencial.mult(2); // Ajusta intensidad de la órbita
          pez.vel.add(tangencial);
          pez.tieneTangencial = true;
        }
        // ------------------------------------------
      }

      pez.applyForce(fuerzaAnzuelo);
    }

    pez.update();
    pez.display();
  }
}


// --- Interacción con el usuario ---

function keyPressed() {
  if (key === 'a' || key === 'A') {
    // Crea un nuevo anzuelo en la posición del mouse
    anzuelos.push(new Anzuelo(mouseX, mouseY));
  }
  if (key === 'd' || key === 'D') {
    // Elimina el último anzuelo creado
    if (anzuelos.length > 0) {
      anzuelos.pop();
    }
  }
  if (key === 'x' || key === 'X') {
    // Elimina todos los anzuelos
    anzuelos = [];
  }
  if (key === 'c' || key === 'C') {
    // Cambia el modo de color
    colorMode = (colorMode + 1) % 4;
    for (let pez of peces) {
      pez.updateColor();
    }
  }
}

function mousePressed() {
  // Activa el modo resorte si el mouse está cerca del último anzuelo
  if (anzuelos.length > 0) {
    let ultimoAnzuelo = anzuelos[anzuelos.length - 1];
    if (dist(mouseX, mouseY, ultimoAnzuelo.pos.x, ultimoAnzuelo.pos.y) < 20) {
      ultimoAnzuelo.isSpring = true;
    }
  }
}

function mouseDragged() {
  if (anzuelos.length > 0) {
    let ultimoAnzuelo = anzuelos[anzuelos.length - 1];
    if (ultimoAnzuelo.isSpring) {
      ultimoAnzuelo.moveTarget(mouseX, mouseY);
    }
  }
}

function mouseReleased() {
  if (anzuelos.length > 0) {
    let ultimoAnzuelo = anzuelos[anzuelos.length - 1];
    ultimoAnzuelo.isSpring = false;
  }
}

// --- Funciones de apoyo ---

function crearCardumenes() {
  // Posiciones para los centros de los cardúmenes
  let centros = [
    createVector(width * 0.25, height * 0.25),
    createVector(width * 0.75, height * 0.75),
    createVector(width * 0.25, height * 0.75),
    createVector(width * 0.75, height * 0.25),
  ];

  for (let i = 0; i < numPeces; i++) {
    let centro = random(centros);
    let x = randomGaussian(centro.x, 100);
    let y = randomGaussian(centro.y, 100);
    peces.push(new Pez(x, y));
  }
}
```

## Captura de pantalla representativa
<img width="887" height="830" alt="image" src="https://github.com/user-attachments/assets/537f83fe-9cb0-4148-bb58-f439eefcd0e2" />















