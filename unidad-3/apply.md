# Unidad 3


## 🛠 Fase: Apply
### Actividas 10
1. Diseña e implementa tu obra generativa interactiva en tiempo real.
- Debe ser interactiva.
- Debes usar al menos dos algoritmos diferentes de la unidad 1, además de random.
>**Concepto de la obra**
>Mi obra la pensé como una especie de móvil suspendido en el aire, donde varias placas de diferentes formas y tamaños están conectadas entre sí por alambres  (como las obras de Caler). Cada una de estas placas se comporta como un cuerpo con masa, que no está quieto, sino que responde a las fuerzas de los demás. Eso significa que todas se atraen entre sí como si tuvieran su propia gravedad, y gracias a esto la escultura se mueve de manera orgánica y nunca repite exactamente el mismo estado. Es como observar una pequeña constelación de piezas que se buscan y se equilibran constantemente, recordando la dinámica de los planetas pero con la fragilidad y la ligereza de una escultura cinética.
>Para que fuera interactiva, agregué que las placas reaccionan como si una fuerza las empujara, al dar click o oprmi teclas. También incluí un viento que se activa al oprimir una tecla, para que la obra se sienta aún más viva, como si el aire jugara con ella.

>**Teclas y reacción**
  >- Espacio → Pausa o reanuda la simulación.
  >- W → Crea una ráfaga de viento global.
  >- G → Genera un nuevo nodo conectado al ancla.
  >- Clic sobre un nodo → Permite arrastrarlo.
  >- Clic en espacio vacío → Provoca una explosión de fuerza hacia afuera.
  >- Soltar el mouse → Libera el nodo arrastrado.
 
2. Explica cómo modelaste el problema de los n-cuerpos en tu obra.
> Modelé mi obra usando la idea de los n-cuerpos, que básicamente significa que cada parte de la escultura (las placas, nodos o el ancla) se comporta como si fuera un “cuerpo” con masa. Cada cuerpo siente la atracción de todos los demás, como si fueran pequeñas fuerzas que lo jalan. Eso hace que el movimiento no sea fijo ni repetitivo, sino que siempre cambie porque todos dependen de todos.
3. Copia el enlace a tu simulación en p5.js.
https://editor.p5js.org/LCami-Villanueva/sketches/UeG_KGBX8
4. Copia el código.
```JavaScript
const CANVAS_W = 800;
const CANVAS_H = 600;
const G = 1.2;
let movers = [];
let links = [];
let running = true;
let dragIndex = -1;
let dragOffset = null;

// ---------- POSICIONES INICIALES CALCADAS ----------
const baseNodes = [
  { x: 600, y: 500, shape: 'anchor' },
  { x: 500, y: 450, shape: 'node' },
  { x: 400, y: 400, shape: 'node' },
  { x: 360, y: 380, shape: 'plate' },
  { x: 450, y: 350, shape: 'node' },
  { x: 420, y: 330, shape: 'plate' },
  { x: 520, y: 400, shape: 'node' },
  { x: 470, y: 300, shape: 'node' },
  { x: 440, y: 280, shape: 'plate' },
  { x: 530, y: 280, shape: 'node' },
  { x: 500, y: 260, shape: 'plate' },
  { x: 560, y: 350, shape: 'node' },
  { x: 600, y: 250, shape: 'node' },
  { x: 620, y: 240, shape: 'plate' },
  { x: 580, y: 300, shape: 'node' },
  { x: 640, y: 220, shape: 'node' },
  { x: 670, y: 210, shape: 'plate' }
];

const hierarchy = [
  [0, 1],[1, 2],[2, 3],
  [1, 4],[4, 5],
  [0, 6],[6, 7],[7, 8],
  [6, 9],[9, 10],
  [0, 11],[11, 12],[12, 13],
  [0, 14],[14, 15],[15, 16]
];

// ---------- SETUP ----------
function setup() {
  createCanvas(CANVAS_W, CANVAS_H);
  for (let i = 0; i < baseNodes.length; i++) {
    const b = baseNodes[i];
    let mass = constrain(3 + randomGaussian(0, 0.8), 0.8, 6);
    let shape = b.shape === 'plate' ? random(['ellipse', 'triangle', 'rect']) : 'dot';
    let hue = constrain(200 + randomGaussian(0, 25), 0, 360);
    let col = color(hue, 80, 30, 220);
    let m = new Mover(b.x, b.y, mass, shape, col, i === 0);
    movers.push(m);
  }
  links = hierarchy.slice();
}

// ---------- DRAW ----------
let windNoiseOffset = 0;
function draw() {
  background(245);

  stroke(40);
  strokeWeight(2);
  for (let pair of links) {
    const a = movers[pair[0]];
    const b = movers[pair[1]];
    line(a.position.x, a.position.y, b.position.x, b.position.y);
  }
  noStroke();

  if (running) {
    windNoiseOffset += 0.005;
    for (let i = 0; i < movers.length; i++) {
      let mi = movers[i];
      if (mi.fixed) continue;

      for (let j = 0; j < movers.length; j++) {
        if (i === j) continue;
        let mj = movers[j];
        let force = p5.Vector.sub(mj.position, mi.position);
        let d = constrain(force.mag(), 8, 250);
        let strength = (G * mi.mass * mj.mass) / (d * d);
        force.setMag(strength);
        mi.applyForce(force);
      }

      let frictionCoef = 0.02;
      let friction = mi.velocity.copy();
      if (friction.mag() > 0.001) {
        friction.mult(-1);
        friction.normalize();
        friction.mult(frictionCoef * mi.mass);
        mi.applyForce(friction);
      }

      let nx = noise(windNoiseOffset + i * 0.1);
      let windX = map(nx, 0, 1, -0.05, 0.05);
      let wind = createVector(windX * (1 / mi.mass) * 2, 0);
      wind.mult(0.2 * mi.mass);
      mi.applyForce(wind);

      let perturb = createVector(random(-0.01, 0.01), random(-0.01, 0.01));
      perturb.mult(0.5);
      mi.applyForce(perturb);
    }
  }

  for (let i = 0; i < movers.length; i++) {
    movers[i].update();
    movers[i].edges();
    movers[i].show();
  }

  if (dragIndex !== -1) {
    let m = movers[dragIndex];
    let mousePos = createVector(mouseX + (dragOffset ? dragOffset.x : 0), mouseY + (dragOffset ? dragOffset.y : 0));
    let force = p5.Vector.sub(mousePos, m.position);
    force.mult(0.5);
    m.applyForce(force);
  }
}

// ---------- MOVER CLASS ----------
class Mover {
  constructor(x, y, m, shape, col, fixed = false) {
    this.position = createVector(x, y);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
    this.mass = m;
    this.shape = shape;
    this.col = col;
    this.fixed = fixed;
    this.size = map(this.mass, 0.8, 6, 12, 36);
  }

  applyForce(force) {
    let f = force.copy();
    f.div(this.mass);
    this.acceleration.add(f);
  }

  update() {
    if (this.fixed) {
      this.velocity.mult(0);
      this.acceleration.mult(0);
      return;
    }
    this.velocity.add(this.acceleration);
    this.velocity.limit(8);
    this.position.add(this.velocity);
    this.acceleration.mult(0);
  }

  edges() {
    if (this.position.x < 0) { this.position.x = 0; this.velocity.x *= -0.3; }
    if (this.position.x > width) { this.position.x = width; this.velocity.x *= -0.3; }
    if (this.position.y < 0) { this.position.y = 0; this.velocity.y *= -0.3; }
    if (this.position.y > height) { this.position.y = height; this.velocity.y *= -0.3; }
  }

  show() {
    push();
    translate(this.position.x, this.position.y);
    fill(red(this.col), green(this.col), blue(this.col), 200);
    noStroke();
    if (this.shape === 'ellipse') {
      ellipse(0, 0, this.size * 1.3, this.size);
    } else if (this.shape === 'triangle') {
      triangle(-this.size * 0.7, this.size * 0.7, 0, -this.size, this.size * 0.7, this.size * 0.7);
    } else if (this.shape === 'rect') {
      rectMode(CENTER);
      rect(0, 0, this.size * 1.4, this.size * 0.9, 8);
    } else if (this.shape === 'dot') {
      fill(80);
      ellipse(0, 0, 6, 6);
    } else if (this.shape === 'anchor') {
      fill(40);
      rectMode(CENTER);
      rect(0, 0, 8, 20);
    } else {
      ellipse(0, 0, this.size, this.size);
    }
    pop();
  }
}

// ---------- INTERACTIVIDAD ----------
function mousePressed() {
  let found = -1;
  for (let i = 0; i < movers.length; i++) {
    let d = dist(mouseX, mouseY, movers[i].position.x, movers[i].position.y);
    if (d < max(16, movers[i].size / 2)) {
      found = i;
      break;
    }
  }
  if (found !== -1) {
    dragIndex = found;
    dragOffset = createVector(movers[found].position.x - mouseX, movers[found].position.y - mouseY);
  } else {
    for (let i = 0; i < movers.length; i++) {
      if (movers[i].fixed) continue;
      let force = p5.Vector.sub(movers[i].position, createVector(mouseX, mouseY));
      let d = constrain(force.mag(), 20, 300);
      force.setMag(120 / (d * d));
      movers[i].applyForce(force);
    }
  }
}

function mouseReleased() {
  dragIndex = -1;
  dragOffset = null;
}

function keyPressed() {
  if (key === ' ') {
    running = !running;
  }
  if (key === 'g' || key === 'G') {
    let nx = baseNodes[0].x + randomGaussian(-40, 30);
    let ny = baseNodes[0].y + randomGaussian(-60, 40);
    let mass = constrain(3 + randomGaussian(0, 0.8), 0.8, 6);
    let shape = random(['ellipse', 'triangle', 'rect']);
    let col = color(constrain(200 + randomGaussian(0, 25), 0, 360), 80, 30, 220);
    let newMover = new Mover(nx, ny, mass, shape, col, false);
    movers.push(newMover);
    links.push([0, movers.length - 1]);
  }
  if (key === 'w' || key === 'W') {
    for (let i = 0; i < movers.length; i++) {
      if (movers[i].fixed) continue;
      let wind = createVector(random(0.5, 1.2), random(-0.2, 0.2));
      wind.mult(movers[i].mass);
      movers[i].applyForce(wind);
    }
  }
}
```

5. Captura una imagen representativa de tu ejemplo.
   <img width="794" height="591" alt="image" src="https://github.com/user-attachments/assets/8012838b-e504-4f29-be1c-f22a949f5050" />
