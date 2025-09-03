# Evidencias de la unidad 4
### set-Seek https://www.notion.so/Simulaci-n-Para-Sistemas-Interactivos-25f42dfbaef680c4bd7ff48838e1f94c?source=copy_link
## Explicación conceptual de la obra

* ¿Qué concepto de la unidad 4 y cómo lo aplicaste en la obra?
> Apliqué el concepto de pendulo, que es el movimiento original con el que se mueve el anzuelo al aparecer, además cuando lo mueves por el agua este la cuerda de este tiene comportamiento de resorte para hacerlo aun más interesante e intwractivo

* ¿Qué concepto de la unidad 3 y cómo lo aplicaste en la obra?
> De la unidad 3 aplique el concepto de atracción graviatcional, que el la fueza que ejerce el anzuelo sobre los peces haciendo que estos se sientan atraidos hacia el 

* ¿Qué concepto de la unidad 2 y cómo lo aplicaste en la obra?
> De la unidad 2 use el motion 101, aplicando velocidad y acdeleración ak movimeintod de los peces

* ¿Qué concepto de la unidad 1 y cómo lo aplicaste en la obra?
> De la unidad 1 apliqué el concepto de aleatoriedad gauseana en la manera en comos e crwean los grupos de peces, y ademas en colo se cambian los colores en

## ¿Cómo resolviste la interacción?
> La interacción se hace de varias maneras:
> - Al presioanr la tecla a se crea un anzuelo nuevo (Varias vees varios anzuelos) además estos e crean el la posición en que este el  mouse en ese momento.
> - Al presionar la tecla d el anzuelo desaparece y se esparcen lso ppeces que estaban a su alrededor
> - Al presionar la tecla X, todos lso anzuelos desaprecen y por tanto todos los peces son liberados 

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
    this.updateColor();
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
  updateColor() {
    switch (colorMode) {
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
    this.angulo = PI / 4;
    this.velocidadAngular = 0;
    this.aceleracionAngular = 0;
    this.gravedad = 0.4;
    this.arrastre = 0.99;
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
<img width="874" height="795" alt="image" src="https://github.com/user-attachments/assets/900988ae-1b0b-4974-9c65-e4397264b118" />










