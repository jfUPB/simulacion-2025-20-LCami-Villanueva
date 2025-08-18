# Unidad 3

## 🔎 Fase: Set + Seek

### Actividad 09
**Inventa tres obras generativas interactivas, uno para cada una de las siguientes fuerzas:**

- Fricción.
    - Explica cómo modelaste la fuerza.
      > Para modelar la fuerza de fricción en mi obra generativa, me basé en el concepto de que la fricción es una fuerza que siempre apunta en dirección opuesta al movimiento de un objeto: hace que la energía cinética se reduzca con el tiempo. En el código, cada espiral tiene una propiedad de velocidad que representa su energía de movimiento. La fricción se aplica disminuyendo esa velocidad con cada frame usando la fórmula <img width="83" height="25" alt="image" src="https://github.com/user-attachments/assets/d9e54680-975b-4259-8657-e710d629770a" />  la dirección opuesta al movimiento. Además, la fricción también hace que las espirales se desvanezcan gradualmente, reduciendo el valor de alpha, lo que simula visualmente cómo se disipa la energía.
    - Conceptualmente cómo se relaciona la fuerza con la obra generativa.
      >La relación entre la fuerza y la obra generativa es directa: cada espiral funciona como un objeto que se mueve con cierta energía y la fricción hace que esa energía se disminuya con el tiempo. Esto hace que las espirales se desaceleren, cambien su opacidad y luego desaparezcan, representando la disipación de energía. Así, la obra refleja de manera visual cómo actúa la fricción: la dirección opuesta al movimiento frena las espirales y el efecto disipativo es un desvanecimiento gradual, haciendo que el fenómeno físico sea perceptible en términos artísticos y generativos. 
    - Copia el enlace a tu ejemplo en p5.js.   
      https://editor.p5js.org/LCami-Villanueva/sketches/qoG6ms7y7
    - Copia el código.
``` Javascript
      let espirales = [];
let mu = 0.03;  // coeficiente de fricción
let N = 1;      // fuerza normal
let numInicial = 80; // más espirales
let distanciaMin = 20; // mínima distancia entre espirales

function setup() {
  createCanvas(500, 500);
  angleMode(DEGREES);

  // Crear espirales iniciales sin sobreposición
  let intentos = 0;
  while (espirales.length < numInicial && intentos < 1000) {
    let x = random(width);
    let y = random(height);
    if (!sobreposicion(x, y)) {
      espirales.push(new Espiral(x, y));
    }
    intentos++;
  }
}

function draw() {
  background(20);

  for (let i = espirales.length - 1; i >= 0; i--) {
    let e = espirales[i];
    e.update();
    e.display();

    // Si desaparece, eliminar y generar una nueva
    if (e.alpha <= 0 || e.velocidad <= 0.01 || e.tiempo >= e.vidaMax) {
      espirales.splice(i, 1);
      let nueva = crearEspiralNueva();
      if (nueva) espirales.push(nueva);
    }
  }
}

// Evitar sobreposición
function sobreposicion(x, y) {
  for (let e of espirales) {
    if (dist(x, y, e.x, e.y) < distanciaMin) {
      return true;
    }
  }
  return false;
}

// Crear nueva espiral sin sobreposición
function crearEspiralNueva() {
  let intentos = 0;
  while (intentos < 100) {
    let x = random(width);
    let y = random(height);
    if (!sobreposicion(x, y)) {
      return new Espiral(x, y);
    }
    intentos++;
  }
  return null;
}

class Espiral {
  constructor(x, y) {
    this.x = x;
    this.y = y;
    this.angulo = 0;
    this.radioBase = random(1, 3); // espirales más pequeñas
    this.velocidad = random(3, 4); // velocidad de giro
    this.color = color(random(255), random(255), random(255), 255);
    this.alpha = 255;
    this.tiempo = 0;
    this.vidaMax = random(200, 400); // vida limitada

    // Cada espiral crece en un ángulo inicial aleatorio
    this.direccion = random(360);
  }

  aplicarFriccion() {
    // Fórmula: f = -μN v̂
    let friccion = -mu * N * this.velocidad;
    this.velocidad += friccion;
    if (this.velocidad < 0) this.velocidad = 0;

    // Desvanecimiento por fricción
    this.alpha -= mu * 20; 
    this.alpha = max(this.alpha, 0);
    this.color.setAlpha(this.alpha);
  }

  update() {
    this.aplicarFriccion();
    this.angulo += this.velocidad;
    this.tiempo++;
  }

  display() {
    push();
    translate(this.x, this.y);
    noFill();
    stroke(this.color);
    beginShape();
    for (let a = 0; a < this.angulo; a += 5) {
      // Radio crece con el ángulo → espiral real
      let r = this.radioBase * a / 5;
      let px = r * cos(a + this.direccion);
      let py = r * sin(a + this.direccion);
      vertex(px, py);
    }
    endShape();
    pop();
  }
}
```

 - Captura una imagen representativa de tu ejemplo.    
   <img width="774" height="723" alt="image" src="https://github.com/user-attachments/assets/921e43f1-accd-453c-977c-4609cc555883" />

- Resistencia del aire y de fluidos.
    - Explica cómo modelaste la fuerza.
      > Para modelar la fuerza de resistencia que actúa sobre las hojas, utilicé el concepto de drag o resistencia viscosa, que es la fuerza que un fluido (como el aire) ejerce sobre un objeto en movimiento, siempre en dirección opuesta a su velocidad. En el código, esta fuerza se calcula como proporcional al cuadrado de la velocidad de cada hoja y se aplica como una aceleración sobre su movimiento, respetando la relación fundamental de Newton <img width="64" height="28" alt="image" src="https://github.com/user-attachments/assets/02630a23-7cb5-4de1-9292-84d1486900e8" />
 Cada hoja también tiene un valor de masa y un coeficiente de arrastre, lo que permite que la resistencia afecte a unas más que a otras, simulando la variación en su interacción con el aire. De esta manera, las hojas desaceleran de forma realista mientras caen, y eventualmente desaparecen o reaparecen en la parte superior del lienzo, creando un ciclo continuo de movimiento.
    - Conceptualmente cómo se relaciona la fuerza con la obra generativa.
      > Esta fuerza se integra directamente con la obra generativa porque define el comportamiento dinámico y visual de los elementos. Hace que las hojas caigan de manera natural y, además, permite que cada una tenga un movimiento único y orgánico, generando un patrón visual complejo a partir de reglas físicas simples. Así, la relación entre la fuerza y la obra generativa radica en que se utilizan estos principios para mostrar cómo se verían en la naturaleza las hojas cayendo con la resistencia del aire.
    - Copia el enlace a tu ejemplo en p5.js.
      
      https://editor.p5js.org/LCami-Villanueva/sketches/43sjTLMG0
    - Copia el código.
```javascript
      let hojas = [];
let numHojas = 40;
let coefDrag = 0.06;

function setup() {
  createCanvas(600, 400);
  for (let i = 0; i < numHojas; i++) {
    hojas.push(new Hoja(random(width), random(-height, 0)));
  }
}

function draw() {
  background(200, 225, 255);
  
  for (let h of hojas) {
    h.update();
    h.display();
  }
}

class Hoja {
  constructor(x, y) {
    this.pos = createVector(x, y);
    this.vel = createVector(random(-0.5,0.5), random(2,4));
    this.acc = createVector(0,0);
    this.alpha = 255;
    this.color = color(random(100,255), random(50,200), 0, this.alpha);
    this.size = random(10,18);
    this.angle = random(TWO_PI);
    this.angleVel = random(-0.02,0.02);
    this.tiempo = 0;
    this.tiempoParaDesvanecer = random(50,150);
    this.mass = 1; // se puede variar para ver efecto de masa
  }

  aplicarFuerza(fuerza) {
    let f = fuerza.copy().div(this.mass);
    this.acc.add(f);
  }

  aplicarDrag() {
    let speed = this.vel.mag();
    let dragMagnitude = coefDrag * speed * speed;
    let drag = this.vel.copy();
    drag.mult(-1);
    drag.setMag(dragMagnitude);
    this.aplicarFuerza(drag);
  }

  update() {
    // aplicar gravedad simple
    let gravity = createVector(0, 0.1 * this.mass);
    this.aplicarFuerza(gravity);

    // aplicar drag
    this.aplicarDrag();

    // actualizar velocidad y posición
    this.vel.add(this.acc);
    this.pos.add(this.vel);
    this.angle += this.angleVel;
    this.acc.mult(0); // reset aceleración

    this.tiempo++;

    // desvanecimiento gradual después de cierto tiempo
    if (this.tiempo > this.tiempoParaDesvanecer) {
      this.alpha -= 0.2;
      this.alpha = max(this.alpha,0);
      this.color.setAlpha(this.alpha);
    }

    // reaparecer arriba al llegar al fondo o desaparecer
    if (this.pos.y > height || this.alpha <= 0) {
      this.pos.y = random(-50,0);
      this.pos.x = random(width);
      this.alpha = 255;
      this.color.setAlpha(this.alpha);
      this.tiempo = 0;
      this.tiempoParaDesvanecer = random(50,150);
      this.vel = createVector(random(-0.5,0.5), random(2,4));
    }
  }

  display() {
    push();
    translate(this.pos.x, this.pos.y);
    rotate(this.angle);
    fill(this.color);
    noStroke();
    ellipse(0,0,this.size,this.size*0.4);
    pop();
  }
}
```
- Captura una imagen representativa de tu ejemplo.
  <img width="917" height="605" alt="image" src="https://github.com/user-attachments/assets/a286fe30-dfe2-4fbf-acaf-c07ee03e606c" />

- Atracción gravitacional.
    - Explica cómo modelaste la fuerza.
      > Modelé la fuerza tomando como base la segunda ley de Newton, que dice que la fuerza es igual a la masa por la aceleración. Para aplicarlo en el código, cada abeja recibe una fuerza de atracción que depende de la distancia que tiene con la flor. Esa fuerza la calculé usando una fórmula de atracción gravitacional: mientras más cerca esté la abeja, más fuerte es la atracción, y mientras más lejos esté, la fuerza se hace más débil. Además, ajusté la fórmula con una constante para controlar la intensidad y con límites de distancia mínima y máxima para que el movimiento no se volviera exagerado o inestable. Así, cada abeja siente una especie de "jalón" hacia la flor, que cambia en tiempo real según su posición.
    - Conceptualmente cómo se relaciona la fuerza con la obra generativa.
      > Esta fuerza es lo que conecta los elementos principales de la obra generativa. La flor actúa como un centro que irradia atracción, y las abejas reaccionan a esa fuerza acercándose a ella, como en la naturaleza. Gracias a esto, no solo se genera un movimiento fluido y orgánico, sino que también se crea un diálogo visual entre los objetos: la flor, con sus colores claros y delicados, y las abejas que se mueven a su alrededor. La fuerza se convierte entonces en un puente entre la matemática y lo visual, transformando una fórmula en un comportamiento vivo que da sentido y coherencia a la pieza.
    - Copia el enlace a tu ejemplo en p5.js.
      https://editor.p5js.org/LCami-Villanueva/sketches/KOdK4Upti
    - Copia el código.
 ```JavaScript
// The Nature of Code
// Daniel Shiffman (adaptado a "Flor y Abejas")
// https://natureofcode.com/

let flower;
let bees = [];

function setup() {
  createCanvas(600, 600);
  flower = new Flower(width/2, height/2, 10); // Flor más pequeña
  for (let i = 0; i < 10; i++) {
    bees.push(new Bee(random(width), random(height), random(1, 2)));
  }
}

function draw() {
  background(240, 250, 255);

  // Dibujar la flor
  flower.show();

  // Dibujar y actualizar abejas
  for (let bee of bees) {
    let force = flower.attract(bee); // Fuerza gravitacional hacia la flor
    bee.applyForce(force);
    bee.update();
    bee.show();
    bee.edges(); // Reaparece si sale
  }
}


class Flower {
  constructor(x, y, mass) {
    this.mass = mass;
    this.radius = mass * 5;
    this.position = createVector(x, y);
  }

  attract(m) {
    let force = p5.Vector.sub(this.position, m.position);
    let distance = force.mag();
    distance = constrain(distance, 8, 30); // evitar explosión
    force.normalize();
    let strength = (0.5 * this.mass * m.mass) / (distance * distance); 
    force.mult(strength);
    return force;
  }

  show() {
    push();
    translate(this.position.x, this.position.y);

    // Pétalos rosas
    fill(255, 180, 200);
    noStroke();
    for (let i = 0; i < 8; i++) {
      ellipse(this.radius, 0, this.radius * 2, this.radius);
      rotate(TWO_PI / 8);
    }

    // Centro casi blanco azul
    fill(200, 230, 255);
    ellipse(0, 0, this.radius * 1.5);

    pop();
  }
}


class Bee {
  constructor(x, y, mass) {
    this.mass = mass;
    this.radius = mass * 4;
    this.position = createVector(x, y);
    this.velocity = createVector(random(-1, 1), random(-1, 1));
    this.acceleration = createVector(0, 0);
  }

  applyForce(force) {
    let f = p5.Vector.div(force, this.mass);
    this.acceleration.add(f);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.acceleration.mult(0);
  }

  show() {
    stroke(0);
    strokeWeight(1);
    fill(255, 220, 0);
    ellipse(this.position.x, this.position.y, this.radius * 2);
    // rayas negras de abeja
    stroke(0);
    line(this.position.x - this.radius/2, this.position.y,
         this.position.x + this.radius/2, this.position.y);
  }

  edges() {
    if (this.position.x > width) this.position.x = 0;
    if (this.position.x < 0) this.position.x = width;
    if (this.position.y > height) this.position.y = 0;
    if (this.position.y < 0) this.position.y = height;
  }
}

function mouseDragged() {
  flower.position.set(mouseX, mouseY);
}

```
 - Captura una imagen representativa de tu ejemplo.
   <img width="854" height="728" alt="image" src="https://github.com/user-attachments/assets/b7f2c875-d797-4a05-b5d3-60b5047a2477" />



