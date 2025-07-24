# Unidad 1

## 🛠 Fase: Apply

- **Concepto  obra generativa**

  Esta obra representa un sistema de hojas vivas que nacen, crecen y se dispersan en un ciclo orgánico que remite a la dinámica de las estaciones del año. Cada hoja es generada de forma aleatoria, como ocurre en la naturaleza, y su vida está determinada por un tiempo finito que simboliza el paso del tiempo.

  El entorno se puede enriquecer como si se abonara el suelo: nacen más hojas, viven más tiempo, evocando un crecimiento acelerado producto del cuidado. Sin embargo, el viento tambien se hace presente. Las hojas, entonces, responden al movimiento del aire, desplazándose de manera orgánica, como si el soplo del espectador fuera parte del ecosistema.

  La obra alterna entre dos estaciones: primavera y otoño. Al hacer clic, las hojas cambian de color, transformando la atmósfera y mostrando cómo el mismo entorno puede adquirir matices distintos a lo largo del ciclo natural. Así, esta pieza busca capturar la belleza de lo efímero, la interacción entre el azar y el entorno, y la constante transformación de la naturaleza.

- **Código**
  - Presiona la tecla "G" para nutrir el ecosistema: verás cómo las hojas crecen y se multiplican, como si recibieran un abono.
  - Haz clic en el lienzo para cambiar de estación: las hojas cambiarán de color, reflejando el paso del tiempo y las estaciones.
  - Mueve el cursor por la pantalla y observa cómo el viento dispersa las hojas, entre el caos y la armonía.
```
let leaves = [];
let maxLeaves = 100;
let lifeTime = 180;
let season = "spring";
let spawnRadius = 60;

function setup() {
  createCanvas(700, 500);
  noStroke();
  angleMode(RADIANS);
}

function draw() {
  background(220);

  if (leaves.length < maxLeaves) {
    leaves.push(new Leaf());
  }

  for (let i = leaves.length - 1; i >= 0; i--) {
    leaves[i].update();
    leaves[i].display();
    if (leaves[i].age > leaves[i].maxAge) {
      leaves.splice(i, 1);
    }
  }
}

function keyPressed() {
  if (key === 'g' || key === 'G') {
    maxLeaves += int(random(10, 100));
    lifeTime += int(random(20, 80));
    spawnRadius += int(random(10, 60));
  }
}

function mousePressed() {
  season = season === "spring" ? "autumn" : "spring";
  for (let leaf of leaves) {
    leaf.color = leaf.getColor();
  }
}

class Leaf {
  constructor() {
    let r = random(1);
    let angle, radius;

    if (r < 0.95) {
      angle = random(TWO_PI);
      radius = random(20, 30);
      let cx = width / 2;
      let cy = height / 2;
      this.origin = createVector(cx + cos(angle) * radius, cy + sin(angle) * radius);
    } else {
      this.origin = createVector(random(width), random(height));
    }

    this.pos = this.origin.copy();
    this.vel = p5.Vector.random2D().mult(0.5);
    this.angle = random(-PI / 6, PI / 6);
    this.color = this.getColor();
    this.age = 0;
    this.maxAge = lifeTime + random(-30, 30);
    this.rotationSpeed = random(-0.01, 0.01);
    this.noiseOffset = random(1000);
  }

  getColor() {
    if (season === "spring") {
      let g = constrain(randomGaussian(200, 15), 150, 255);
      let r = constrain(randomGaussian(120, 10), 80, 160);
      let b = constrain(randomGaussian(130, 10), 90, 170);
      return color(r, g, b);
    } else {
      let r = constrain(randomGaussian(220, 15), 180, 255);
      let g = constrain(randomGaussian(120, 15), 80, 160);
      let b = constrain(randomGaussian(60, 10), 30, 100);
      return color(r, g, b);
    }
  }

  update() {
    let inside = mouseX >= 0 && mouseX <= width && mouseY >= 0 && mouseY <= height;

    if (inside) {
      // Movimiento afectado por ruido y mouse
      let windX = map(noise(this.noiseOffset), 0, 1, -1, 1);
      let windY = map(noise(this.noiseOffset + 1000), 0, 1, -1, 1);
      this.noiseOffset += 0.01;
      let wind = createVector(windX, windY).mult(0.5);
      this.vel.add(wind);

      let mouseRepel = p5.Vector.sub(this.pos, createVector(mouseX, mouseY));
      let dist = mouseRepel.mag();
      if (dist < 200) {
        mouseRepel.setMag(map(200 - dist, 0, 200, 0, 1.5));
        this.vel.add(mouseRepel);
      }

    } else {
      // Movimiento radial desde el centro
      let center = createVector(width / 2, height / 2);
      let direction = p5.Vector.sub(this.pos, center);
      direction.normalize();
      direction.mult(0.7);
      this.vel.add(direction);
    }

    this.vel.limit(2);
    this.pos.add(this.vel);
    this.angle += this.rotationSpeed;
    this.age++;
  }

  display() {
    push();
    translate(this.pos.x, this.pos.y);
    rotate(this.angle);
    fill(this.color);
    beginShape();
    vertex(0, 0);
    bezierVertex(5, -5, 5, -15, 0, -20);
    bezierVertex(-5, -15, -5, -5, 0, 0);
    endShape(CLOSE);
    pop();
  }
}
```

- En el código se implemneta:
  - **Distribución normal (gaussiana):** Se utiliza para generar variaciones realistas en los colores de las hojas, especialmente en el canal verde durante la primavera y naranjas en el otoño. Esto hace que la mayoría de valores estén cerca del promedio (Verde o naranjas), pero con desviaciones naturales:

  - **Ruido Perlin:** Se implementa para simular el movimiento orgánico del viento que afecta a las hojas. 

  - **Distribución uniforme:** Se usa en varias partes del código para generar posiciones iniciales y colores de forma aleatoria uniforme, es decir, con igual probabilidad en todo el rango. Por ejemplo:

  - **Salto de Lévy** Se presente en la forma en que algunas hojas aparecen en lugares alejados del centro, rompiendo el patrón de expansión habitual. Aunque la mayoría de las hojas surgen cerca del origen, unas   pocas lo hacen en puntos lejanos, como si hubieran sido transportadas repentinamente por una ráfaga fuerte o un cambio inesperado.
    
- Enlace al sketch: https://editor.p5js.org/LCami-Villanueva/sketches/IKPo4EmKU
  
- Captura sketch.

https://github.com/user-attachments/assets/9fd08ffe-0da3-42f2-af6a-8732868d4d8f



