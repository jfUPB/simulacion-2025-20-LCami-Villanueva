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
<img width="622" height="294" alt="image" src="https://github.com/user-attachments/assets/cd78668f-b3b2-43c2-a0d6-a11cb0b4f6b9" />

### Ejemplo 4.6
> 1. Para este ejmeplo me gustaría aplicar una fuerza tipo pendulo
> 2. Aquí Cada vez que se llama a addParticle(), se agrega una nueva partícula al arreglo, mientras que en cada frame, durante la ejecución de run(), se recorre el arreglo de atrás hacia adelante para actualizar cada partícula y revisar si ha “muerto” mediante isDead(). Cuando la partícula cumple su vida útil, se elimina del arreglo usando splice(), liberando memoria de forma progresiva y evitando que el arreglo crezca indefinidamente. Esto es muy similar a los ejemplos anteriores, donde también se controlaba el ciclo de vida de las partículas para mantener la simulación eficiente y sin saturar la memoria.
> 3. En este ejemplo apliqué el concepto de péndulo para las partículas. Lo implementé usando coordenadas polares, donde cada partícula tiene un ángulo y una longitud desde su origen, y su aceleración angular se calcula con la fórmula de oscilación armónica. Esto hace que la partícula se mueva de un lado a otro, y no en círculos completos, simulando un péndulo real que va y viene. Lo hice así para que el movimiento de las partículas fuera visualmente más interesante, mostrando oscilaciones suaves y controladas en lugar de trayectorias lineales o circulares.
> 4.  [Link Ejemplo 4.6](https://editor.p5js.org/LCami-Villanueva/sketches/qhbJax5mo)
> 5.  Cambios en Clase Particle
``` JS
class Particle {
  constructor(x, y, isPendulum = false) {
    this.position = createVector(x, y);
    this.acceleration = createVector(0, 0.0);
    this.velocity = createVector(random(-1, 1), random(-2, 0));
    this.lifespan = 255.0;
    this.mass = 1;

    // Propiedades para péndulo
    this.isPendulum = isPendulum;
    if (this.isPendulum) {
      this.r = random(50, 150);           // longitud del hilo
      this.angle = random(-PI / 8, PI / 8); // menor amplitud para que no vaya tan lejos
      this.aVelocity = random(0.05, 0.1); // velocidad inicial más rápida
      this.aAcceleration = 0;
      this.origin = createVector(x, y);
    }
  }

  run() {
    this.update();
    this.show();
  }

  applyForce(force) {
    if (!this.isPendulum) {
      let f = force.copy();
      f.div(this.mass);
      this.acceleration.add(f);
    } else {
      // Fuerza de gravedad proyectada como aceleración angular
      let g = force.y; // gravedad vertical
      this.aAcceleration = (-g / this.r) * sin(this.angle);
    }
  }

  update() {
    if (!this.isPendulum) {
      this.velocity.add(this.acceleration);
      this.position.add(this.velocity);
      this.acceleration.mult(0);
    } else {
      // Oscilación tipo péndulo (va y vuelve)
      this.aVelocity += this.aAcceleration;
      this.angle += this.aVelocity;
      this.aVelocity *= 0.99; // amortiguación ligera
      this.aAcceleration = 0;
      this.position.x = this.origin.x + this.r * sin(this.angle);
      this.position.y = this.origin.y + this.r * cos(this.angle);
    }
    this.lifespan -= 2.0;
  }

  show() {
    stroke(0, this.lifespan);
    strokeWeight(2);
    fill(127, this.lifespan);
    circle(this.position.x, this.position.y, 8);
  }

  isDead() {
    return this.lifespan < 0.0;
  }
}
```
Cambios en clase Emmiter
``` JS
class Emitter {
  constructor(x, y) {
    this.origin = createVector(x, y);
    this.particles = [];
  }

  addParticle() {
    // Aleatoriamente decidimos si la partícula será péndulo
    let isPendulum = random(1) < 0.3; // 30% serán péndulo
    this.particles.push(new Particle(this.origin.x, this.origin.y, isPendulum));
  }

  run() {
    for (let i = this.particles.length - 1; i >= 0; i--) {
      let p = this.particles[i];
      p.run();
      if (p.isDead()) {
        this.particles.splice(i, 1);
      }
    }
  }

  applyForce(force) {
    for (let particle of this.particles) {
      particle.applyForce(force);
    }
  }
}
```
<img width="556" height="605" alt="image" src="https://github.com/user-attachments/assets/d6dab517-6bc7-4a32-84d6-e56197ecd157" />

### Ejemplo 4.7
> 1. Para este ejmeplo me gustaría aplicar una fuerza de atracción gravitacional.
> 2. En este código la gestión de partículas sigue la misma lógica de los ejemplos anteriores: el sistema de partículas crea instancias de la clase Particle y las almacena en un arreglo dinámico. En cada iteración del draw(), cada partícula actualiza su posición según las fuerzas aplicadas y se dibuja en pantalla. Además, se reduce progresivamente su atributo lifespan, que funciona como un temporizador de vida. Cuando lifespan llega a un valor bajo (cercano a cero), la partícula se considera “muerta” y se elimina del arreglo mediante el método remove(). Esto asegura que la memoria se use de forma eficiente, ya que solo se mantienen en memoria las partículas activas y se descartan las que han completado su ciclo de vida, evitando fugas o acumulaciones innecesarias.
> 3. En este ejemplo añadí un attractor que coloqué con el mouse para generar una fuerza de atracción sobre las partículas. Para ello reutilicé la misma lógica del repeller, modificando el cálculo de la fuerza para que en lugar de repeler, atrajera a las partículas según una fórmula basada en la gravitación (fuerza inversamente proporcional al cuadrado de la distancia). De esta manera, cada partícula actualiza su movimiento bajo la influencia de la gravedad global y de la atracción del nuevo objeto, lo que me permitió simular un comportamiento más complejo y realista dentro del sistema de partículas, manteniendo la gestión de memoria eficiente mediante la eliminación de partículas muertas.
> 4.  [Link Ejemplo 4.7](https://editor.p5js.org/LCami-Villanueva/sketches/GuxVXP8YB)
> 5.  Cambios en Clase Particle
``` JS
class Repeller {
  // Se agregó parámetro mode para permitir repulsión o atracción
  constructor(x, y, mode = "repel") {
    this.position = createVector(x, y);
    this.power = 150;
    this.mode = mode; // "repel" o "attract"
  }

  show() {
    stroke(0);
    strokeWeight(2);
    // Cambia el color según tipo de fuerza
    if (this.mode === "repel") fill(127); // gris para repulsor
    else fill(100, 200, 255, 150); // azul semitransparente para atractor
    circle(this.position.x, this.position.y, 32);
  }

  repel(particle) {
    let force = p5.Vector.sub(this.position, particle.position);
    let distance = force.mag();
    distance = constrain(distance, 5, 50);
    // Cambiado: fuerza positiva si mode = "attract"
    let strength = (this.mode === "repel" ? -1 : 1) * this.power / (distance * distance);
    force.setMag(strength);
    return force;
  }
}
```
Cambios en el Sketch 
``` JS
let emitter;
let repeller;
let attractor = null; // nueva variable para la masa atractora

function setup() {
  createCanvas(640, 240);
  emitter = new Emitter(width / 2, 60);
  repeller = new Repeller(width / 2, 250, "repel");
}

function draw() {
  background(255);

  emitter.addParticle();

  // gravedad hacia abajo
  let gravity = createVector(0, 0.1);
  emitter.applyForce(gravity);

  // aplicar repulsor
  emitter.applyRepeller(repeller);

  // aplicar atractor si existe (nuevo)
  if (attractor) {
    emitter.applyRepeller(attractor);
    attractor.show();
  }

  emitter.run();
  repeller.show();
}

// Crear masa atractora al hacer clic (nuevo)
function mousePressed() {
  attractor = new Repeller(mouseX, mouseY, "attract"); // mismo Repeller pero modo "attract"
}
```
> <img width="637" height="307" alt="image" src="https://github.com/user-attachments/assets/24bf1fb4-3aeb-471f-8de7-346e20eb2f6e" />

# Apply: Aplicación 🛠
## Actividad 03
Es hora de una nueva creación. Diseña e implementa una obra de arte generativa algorítmica interactiva en tiempo real en p5.js que cumpla con los siguientes requisitos:

Documenta el proceso de creación, incluyendo la idea inicial, bocetos, experimentación con el código y el resultado final.

1. Es unidad incluye una novedad: DISEÑO. Debes intencionar tu obra. Esta vez te pediré que DISEÑES antes de generar código. Define un concepto, haz bocetos, define la interacción, etc. ¿Cuál es el concepto de tu obra? ¿Qué quieres comunicar con ella?
   > **ETAPA DE DISEÑO** 🎨✨
   >
   > Luego de ver los ejmplos del libro y revisar varias cosas, me gustó mucho el ultimo ejemplo que es un sistema de particulas que emula el fuego, me gustaría que mi obra se encaminara hacia allá. 🔥
   >
   > 💡 **Lluvia de ideas** 
   >  * Represemntar Fuego de diferentes colores, como cuando se mezclan con diferentes compuestos quimicos
   >  * Hacer que pueda caer particulas que representen agua estas apagarían el fuego
   >  * Que al apagarse el fuego se convierta en humito
   >  * Que el fuego sea danzante, que se pueda manejar con audio y que se mueva dependiendo del sonido.
   >  * Que los colores tambien cambien dependiendo de la musica,
   >  * Que el fuego pueda avivarse y crecer y expandirse.
            
   > ✏️ **Bocetos**
   
   > 🧩 **Conceptos Preliminares**
   > 
   > Con la obra pretendo simular una llama de fuego cambiante que pasa por diversos estados dependiendo del aire, del agua. Los factores ambientales que la rodean afectan su comportamiento: cómo se mueve con viento. Todo ocurre dentro de un marco de contraste entre lo fuerte y lo frágil, mostrando cómo lo fuerte puede volverse frágil y lo frágil puede transformarse en fuerza de nuevo.
   
   > 🖱️ **Interacción Preliminar**
   > * Musica: Cambia color e intensidad de fuego.
   > * Mouse arrastrado: Genera viento.
   > * Mouse con click : Agregas particulas de agua que apagan el fuego o Chispas que avivan
   > * Tecla W: Echas agua con el mouse (Defecto)
   > * Tecla F: Agregas chispas por el mouse

   > 🧪 **Experimentos**
   > 
   > Aprovechando que Gemini me permite hacer una vista previa del código que se le da o genera, haré los primeros experimentos allí, estas pruebas serán sin audio, en vez de eso se         > usará el sonido ambiente.
   > 
   > * Experimento 1. Lo primero que cree  fue la clase particula, que sería la base del sitema, ya que en ella se encuentra la lógica de todas las particulas que existiran, máS             >adelante, en este caso se creo con las caracteristicas deseadas para hacer el fuego, esta ya contiene el tiempo de vida por lo que despues de un tiempo las particulas mueren para        >liberar memoría.
   >   
   > Imagen Experimento 1.
   > 
   > <img width="765" height="623" alt="image" src="https://github.com/user-attachments/assets/ef1fcbfc-6b13-4ee6-a153-8954dc445484" />
   
   > * Experimento 2.
   > Agregué las particulas de agua y de humo, para que al echara agua se apague le fuergo, además que al apagarse salgan las partculas de humito.

   > Imagen Experimento 2
   > <img width="883" height="679" alt="image" src="https://github.com/user-attachments/assets/0717abbc-ea34-4609-bf40-ec1d4284fd44" />
   
   > * Experimento 3.
   >   Intente que el agua y el fuego se vieran un poco mejor, y aunque logre con blending y transparencia mejoroar la apariencia de fuego, el gaua se complico, no daba los resultados que
   >   queria y al implementar una tecnica diferente de renderizado no supe por que se creo una estela azul por un lado.
   >   
   >Imagen experimento 3
   > 
   >   <img width="610" height="687" alt="image" src="https://github.com/user-attachments/assets/50c754fc-a61c-4453-8fe1-21ab00183af2" />
   >*Experimeto 4
   > Aquí volví a la forma de renderizado anterior, solo que haciendo que el agua tuviera un estela  y arregle le puse un blending al humo para que se viera más como humo.
   > 
   > <img width="492" height="490" alt="image" src="https://github.com/user-attachments/assets/28f26a59-7f41-4390-a8ec-59f7d78d63ea" />
   >
   >*Experimeto 5.
   > Quise agregar viento por lo que al oprimir las flechas en el teclado se genera una fuerzaq que mueve el fuego como si viniera viento con esa dirección.
   > 
   > Imagen Experimento 5
   > 
   > <img width="709" height="436" alt="image" src="https://github.com/user-attachments/assets/da0b2604-1130-4adc-a2ef-44b48c63ccab" />

   > *Experimento 6
   > Aquí agregué audio y probe diferentes niveles de sensibilidad para reaccionar al sonido, logrando que los colores cambiens egun este, además agregue dos modos cuando escucha el         >sonido ambiente y cargando una cancion y reaccioanndo a esta.
   > 
   > Imagen Experimento 6
   >
   > <img width="653" height="645" alt="image" src="https://github.com/user-attachments/assets/bfebedbb-20ca-42a5-86f4-03ecdd52577f" />

   > 💬 **Que comunica**
   > 
   > ✨ Quiero comunicar dualidad, el estar entre lo fuerte que puede lllegar a ser el fuego y al mismo tiempo lo fragil que se puede sentir frente al agua. Al mismo tiempo la obra          >refleja cómo algo intenso puede apagarse, o también       > cómo puede recuperarse y fortalecerse nuevamente. Representa lo cambiante, mostrando que, aunque muchas veces algo parezca    >extinguido, siempre queda un rastro (Humo vapor en este caso) que recuerda lo que ya no está y evidencia       > cómo puede permanecer de una forma no tan física, pero aún existir.✨

   > ✨ **Concepto Final**
   > 🌀La obra representa la dualidad de un mismo elemento, en este caso, el fuego. Por un lado, puede verse fuerte, imponente y casi indestructible; una fuerza que, incluso dentro de su    > fortaleza, es cambiante y capaz de representar estados y emociones.
   >
   >Sin embargo, al mismo tiempo, vive al vilo de la debilidad: tan solo un poco de agua puede llevarlo a desaparecer. Pero no todo está perdido, ya que una pequeña chispa en el lugar       >indicado es suficiente para que el fuego renazca con el mismo vigor.
   > 
   > 💫 **Explicación Obra Final**
   >
   > 🌀Al final esta obra es un fuego digital vivo que danza y reacciona al sonido. Todo lo que ves en pantalla, desde la llama principal hasta el humo que se disipa, está creado por        > de pequeñas partículas que nacen, se mueven y mueren constantemente. La llama no es estática; su forma y color cambian con la música que escucha. Los sonidos graves la hacen crecer     > y pulsar con fuerza, mientras que los agudos pueden transformarla en un fuego de tonos azules y morados, mostrando así sus diferentes "emociones".
3. Debes utilizar los conceptos de herencia y polimorfismo que revisaste en la fase de investigación.
   > Este concepto fue utilizado en el array principal sistemaParticulas para almacenar y gestionar de forma unificada objetos de clases distintas (ParticulaFuego, ParticulaAgua y           > ParticulaHumo), ya que todas heredan de la clase base Particula. El objetivo de esta implementación fue simplificar radicalmente el bucle principal del programa, permitiendo invocar    > métodos genéricos como update() y show() sobre cualquier elemento del array sin necesidad de verificar su tipo específico, lo que dio como resultado un código más limpio, organizado    > y fácilmente escalable.
5. Debes utilizar al menos un concepto de cada una de las unidades anteriores: 4 conceptos.
   > * Unidad 1
   > * Unidad 2
   > * Unidad 3
   > * Unidad 4
   > * Unidad 5
7. Debes definir cómo vas a gestionar el tiempo de vida de las partículas y la memoria.
   > El teimpo de Particula se gestinó ....
9. La obra debe ser interactiva en tiempo real. Puedes usar teclado, mouse, música, el micrófono, video, sensor o cualquier otro dispositivo de entrada.
   > ⌨️**Interacciones finales**💫
11. Incluye un enlace a tu código en el editor de p5.js.
    > [Obra unidad 5]()
13. Incluye el código fuente.
    > ``` JS
    > ```    
14. Captura de pantallas de tu obra con las imágenes que más te gusten











