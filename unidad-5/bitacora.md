# Evidencias de la unidad 5
## Actividad 2  
🧐🧪✍ Para cada una de las simulaciones: ¿Cómo se está gestionando la creación y la desaparción de las partículas y cómo se gestiona la memoria en cada una de las simulaciones?
### Ejemplo 4.2
> **Las partículas se crean con particles.push(new Particle(width / 2, 20));. Dentro de la clase Particle hay un método llamado isDead(), que revisa un atributo llamado lifespan. Ese valor va disminuyendo cada vez que se ejecuta update(), y cuando llega a ser menor que 0, la partícula se elimina con splice. Así, las partículas que ya no sirven desaparecen y la memoria se va liberando de manera progresiva.**
### Ejemplo 4.4
> Aquí funciona de forma parecida al ejemplo anterior, solo que ahora se hace mediante otra clase llamada Emitter(). Esta clase se encarga de controlar tanto la generación como la desaparición de las partículas. Además, cada vez que haces click se crea un nuevo Emitter, el cual se encarga de gestionarse por sí mismo.
### Ejemplo 4.5
> La forma de generar las partículas es parecida al ejemplo anterior, pero con una diferencia: después de crear el Emitter, al momento de generar cada partícula se usa un random para decidir si será un círculo o un cuadrito (que corresponde a la clase Confetti). La eliminación sigue siendo igual, usando splice para quitar las partículas cuando ya no sirven.
### Ejemplo 4.6
> La gestión funciona de la misma manera que en el ejemplo anterior: se crea un Emitter en el setup y, en cada frame, este va generando una nueva partícula. Luego, gracias a la revisión con isDead(), cada partícula se elimina en el momento adecuado, lo que evita que se acumulen infinitas partículas y asegura que la memoria se libere progresivamente.
### Ejemplo 4.7
> La gestión vuelve a ser la misma: se crea un Emitter y en cada frame este genera una nueva partícula. Después, con la función isDead(), se eliminan las que ya cumplieron su ciclo.

🧐🧪✍️ **Experimentos**
1. Vas a modificar cada una de las simulaciones anteriores incluyen en cada una, al menos un concepto de las unidades anteriores, pero no repitas concepto, la idea es que repases al menos uno de cada unidad.
2. Vas a gestionar la creación y la desaparición de las partículas y la memoria. Explica cómo lo hiciste (aunque es posible que la simulación ya lo haga, trata de identificarlo de nuevo y explicarlo con tus palabras).
3. Explica qué concepto aplicaste, cómo lo aplicaste y por qué.
4. Incluye un enlace a tu código en el editor de p5.js.
5. Incluye el código fuente de cada una de las simulaciones.
6. Captura de pantallas de cada una de las simulaciones con las imágenes que más te gusten como resultado de la ejecución de cada una de las simulaciones.

### Ejemplo 4.2
>1. Para este ejemplo agregué un Perlin Noise en el eje Y para el movimiento de las partículas. 

>2. En la simulación, la gestión de la creación y eliminación de partículas se hace de manera progresiva. En cada draw() se crea una nueva partícula y se almacena en un arreglo (particles). Luego, en cada frame, todas las partículas se actualizan y se dibujan con run(). Para evitar que se acumulen infinitamente, cada partícula tiene un atributo lifespan que va disminuyendo hasta llegar a cero. Cuando esto ocurre, el método isDead() devuelve true y, en ese momento, la partícula se elimina del arreglo con splice(). De esta forma, la memoria se mantiene controlada y no se satura, ya que las partículas “muertas” no siguen ocupando espacio.

>3. Como dije anteriormente para este ejemplo quise agregar perlon noise así lo que hice fue que en cada partícula recibe un noiseOffset único en el constructor y, en cada frame, se utiliza noise(this.noiseOffset, frameCount * 0.01) para obtener un valor que varía suavemente con el tiempo. Ese valor se transforma en una pequeña fuerza vertical adicional aplicada con applyForce(). Con esto se logra que las partículas no caigan en línea recta, sino que, al estar influenciadas por esa fuerza, desciendan de manera más suave, como si pesaran menos y fueran movidas por una ligera brisa que las hace flotar.
>4. [Link Ejemplo 4.2](https://editor.p5js.org/LCami-Villanueva/sketches/vyOgMlDp9 "Perlin Noise para ejmplo 4.2")
>5. Código Fuente 4.2, como solo hice cambios en l clase Particle, solo cópiare ese código Fuente.
``` JS
// Simple Particle System con Perlin Noise
class Particle {
  constructor(x, y) {
    this.position = createVector(x, y);
    this.acceleration = createVector(0, 0);
    this.velocity = createVector(random(-1, 1), random(-1, 0));
    this.lifespan = 255.0;

    // Cada partícula tiene su propio "offset" en el ruido
    this.noiseOffset = random(1000);
  }

  run() {
    let gravity = createVector(0, 0.05);
    this.applyForce(gravity);

    // Viento individual con Perlin Noise
    let n = noise(this.noiseOffset, frameCount * 0.01);
    let windX = map(n, 0, 1, -0.2, 0.2); // viento suave
    let wind = createVector(windX, 0);
    this.applyForce(wind);

    this.update();
    this.show();
  }

  applyForce(force) {
    this.acceleration.add(force);
  }

  // Method to update position
  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.lifespan -= 2;
    this.acceleration.mult(0);
  }

  // Method to display
  show() {
    stroke(0, this.lifespan);
    strokeWeight(2);
    fill(127, this.lifespan);
    circle(this.position.x, this.position.y, 8);
  }

  // Is the particle still useful?
  isDead() {
    return (this.lifespan < 0.0);
  }
}
```
> . <img width="795" height="302" alt="image" src="https://github.com/user-attachments/assets/7b67ae96-e195-42dd-a64f-717ca55a68e3" />

### Ejemplo 4.4
> 1. Para este ejemplo quiero aplicar algún concepto de fuerza.
> 2. Funciona de forma similar al 4.2 pero esta vez mediante otra clase llamada Emitter() .Cada partícula empieza en la posición del emisor y se le asignan propiedades iniciales como velocidad y vida útil. La desaparición ocurre porque cada partícula tiene una variable de “tiempo de vida” (lifespan) que va disminuyendo en cada frame. Cuando ese valor llega a cero, la partícula se considera muerta y el sistema la elimina de la lista de partículas.
> 3.En este ejemplo lo que apliqué es el concepto de la Aplicación de fuerzas. Lo que hice fue generar una fuerza de repulsión que proviene del mouse y actúa sobre las partículas. Esta fuerza externa se calcula en función de la distancia entre cada partícula y el cursor, y al aplicarse modifica directamente la aceleración, que luego afecta la velocidad y la posición según el Motion 101. De esta manera, logré que las partículas reaccionen dinámicamente al movimiento del mouse, mostrando cómo una interacción externa puede alterar el comportamiento del sistema y dándole un carácter más interactivo.
>4. [Link Ejemplo 4.4](https://editor.p5js.org/LCami-Villanueva/sketches/C2F96WWTq)
>5. Modificaciones en la clase Emitter
 ``` JS
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

class Emitter {
  constructor(x, y) {
    this.origin = createVector(x, y);
    this.particles = [];
  }

  addParticle() {
    this.particles.push(new Particle(this.origin.x, this.origin.y));
  }

  run() {
    // Looping through backwards to delete
    for (let i = this.particles.length - 1; i >= 0; i--) {
      this.particles[i].run();
      if (this.particles[i].isDead()) {
        // Remove the particle
        this.particles.splice(i, 1);
      }
    }
  }

  // Nuevo método: fuerza de repulsión desde el mouse
  applyRepel(mouse) {
    for (let p of this.particles) {
      let dir = p.position.copy().sub(mouse); // vector desde el mouse a la partícula
      let d = dir.mag(); // distancia al mouse
      dir.normalize();

      // fuerza inversa al cuadrado (más cerca = más fuerte)
      let strength = constrain(100 / (d * d), 0, 5);
      dir.mult(strength);

      p.applyForce(dir);
    }
  }
}
````
Modificaciones en el Sketch Principal 
``` JS
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

// Particles are generated each cycle through draw(),
// fall with gravity and fade out over time
// A ParticleSystem object manages a variable size
// list of particles.

// an array of ParticleSystems
let emitters = [];

function setup() {
  createCanvas(640, 240);
  let text = createP("click to add particle systems");
}

function draw() {
  background(255);
  for (let emitter of emitters) {
    emitter.run();
    emitter.addParticle();
    emitter.applyRepel(createVector(mouseX, mouseY)); // fuerza de repulsión
  }
}

function mousePressed() {
  emitters.push(new Emitter(mouseX, mouseY));
}
```
<img width="789" height="293" alt="image" src="https://github.com/user-attachments/assets/498792c2-0d95-4ef7-83fa-9dea3e7b7e3b" />

### Ejemplo 4.5
> 1. Para este ejemplo quiero usar un random con distribucion gauseana para los colores paara que de la ilusión que el confetti es mas colorido 
> 2. Este funciona de forma muy similar a los anteriores, aquí lo que se hace es que a través de la clase Emitter. Cada frame se genera una nueva partícula con addParticle(), que puede ser un círculo (Particle) o un cuadrado (Confetti). Luego, en el método run(), se recorre el arreglo de partículas y se llama a isDead() para verificar si su lifespan llegó a cero. Cuando esto ocurre, la partícula se elimina con splice(), lo que libera memoria y evita que el arreglo crezca indefinidamente. De esta manera, aunque la simulación genere partículas continuamente, se mantiene controlada la cantidad en memoria, asegurando que solo existan las necesarias en cada momento.
> 3.En este caso, quise aplicar el concepto de random gaussiano para darle variabilidad natural al tamaño y al color de las partículas. Lo implementé usando randomGaussian() dentro de los constructores o del método show() de Particle y Confetti, generando así valores alrededor de una media con cierta desviación estándar. La idea fue que los círculos tengan colores fríos y tamaños variados y los cuadrados colores cálidos, lo que logra que la simulación se vea más orgánica y menos uniforme, imitando cómo en la vida real los objetos de un mismo tipo no son idénticos y crean un efecto visual más interesante y dinámico.
>4. [Link Ejemplo 4.5](https://editor.p5js.org/LCami-Villanueva/sketches/8Xr7Q8xrs)
>5. Modificaciones en la clase Confetti
``` JS
class Confetti extends Particle {
  show() {
    let warmHue = constrain(randomGaussian(30, 20), 0, 60); // color cálido

    colorMode(HSB, 360, 100, 100, 255);
    fill(warmHue, 90, 100, this.lifespan);
    stroke(warmHue, 80, 60, this.lifespan);
    strokeWeight(2);

    rectMode(CENTER);
    push();
    translate(this.position.x, this.position.y);
    let angle = map(this.position.x, 0, width, 0, TWO_PI * 2);
    rotate(angle);
    square(0, 0, 12);
    pop();
  }
}
```
Modificaciones en la clase Particle
``` JS
class Particle {
  constructor(x, y) {
    this.position = createVector(x, y);
    this.acceleration = createVector(0, 0);
    this.velocity = createVector(random(-1, 1), random(-1, 0));
    this.lifespan = 255.0;

    // Tamaño y color con distribución gaussiana (círculos fríos)
    this.size = abs(randomGaussian(8, 3));
    let coldHue = constrain(randomGaussian(220, 30), 180, 260);
    this.col = color(coldHue, 80, 100, this.lifespan);
  }

  run() {
    let gravity = createVector(0, 0.05);
    this.applyForce(gravity);
    this.update();
    this.show();
  }

  applyForce(force) {
    this.acceleration.add(force);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.lifespan -= 2;
    this.acceleration.mult(0);
  }

  show() {
    colorMode(HSB, 360, 100, 100, 255);
    noStroke();
    fill(this.col);
    circle(this.position.x, this.position.y, this.size);
  }

  isDead() {
    return this.lifespan < 0.0;
  }
}
```
### Ejemplo 4.6
> La gestión funciona de la misma manera que en el ejemplo anterior: se crea un Emitter en el setup y, en cada frame, este va generando una nueva partícula. Luego, gracias a la revisión con isDead(), cada partícula se elimina en el momento adecuado, lo que evita que se acumulen infinitas partículas y asegura que la memoria se libere progresivamente.
### Ejemplo 4.7
> La gestión vuelve a ser la misma: se crea un Emitter y en cada frame este genera una nueva partícula. Después, con la función isDead(), se eliminan las que ya cumplieron su ciclo.





