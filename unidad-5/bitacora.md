# Evidencias de la unidad 5
## Actividad 2  
🧐🧪✍ Para cada una de las simulaciones: ¿Cómo se está gestionando la creación y la desaparción de las partículas y cómo se gestiona la memoria en cada una de las simulaciones?
### Ejemplo 4.2
> **Las partículas se crean con particles.push(new Particle(width / 2, 20));. Dentro de la clase Particle hay un método llamado isDead(), que revisa un atributo llamado lifespan. Ese valor va disminuyendo cada vez que se ejecuta update(), y cuando llega a ser menor que 0, la partícula se elimina con splice. Así, las partículas que ya no sirven desaparecen y la memoria se va liberando de manera progresiva. Si no se eliminan las partículas muertas, el arreglo crece sin control y el bucle de actualización run() debe recorrer cada vez más elementos, lo que degrada el rendimiento del sistema.**
### Ejemplo 4.4
> Aquí funciona de forma parecida al ejemplo anterior, solo que ahora se hace mediante otra clase llamada Emitter(). Esta clase se encarga de controlar tanto la generación como la desaparición de las partículas. Además, cada vez que haces click se crea un nuevo Emitter, el cual se encarga de gestionarse por sí mismo. 
### Ejemplo 4.5
> La forma de generar las partículas es parecida al ejemplo anterior, pero con una diferencia: después de crear el Emitter, al momento de generar cada partícula se usa un random para decidir si será un círculo o un cuadrito (que corresponde a la clase Confetti). La eliminación sigue siendo igual, usando splice para quitar las partículas cuando ya no sirven Aunque la variabilidad de color y tamaño no altera el ciclo de vida en memoria, partículas más grandes o en mayor cantidad demandan más cálculos gráficos, lo que puede impactar el rendimiento si el array crece demasiado..
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

>3. Como dije anteriormente para este ejemplo quise agregar perlin noise así lo que hice fue que en cada partícula recibe un noiseOffset único en el constructor. El valor generado por noise() se traduce en un vector wind. Este vector, al pasarse a applyForce(), se suma al vector acceleration de la partícula. En el siguiente update(), esta acceleration modifica la velocity, y la velocity finalmente altera la position. Es esta interacción en cadena entre los conceptos de ruido, fuerza y vectores de movimiento la que transforma un número aleatorio en un desplazamiento suave y orgánico en pantalla.
.
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
> 2. Aquí se utiliza la clase Emitter para crear y administrar partículas. En cada frame se agregan nuevas partículas y se recorren todas en run(). Cada partícula tiene un lifespan decreciente, y al llegar a cero se elimina con splice(). Esto garantiza que la memoria no se sature con partículas muertas y que el arreglo se mantenga en un tamaño controlado. De no ser así, cada clic generaría más partículas acumuladas, y el loop tendría que procesar un número creciente de elementos, lo que degradaría la velocidad de la simulación.
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
> 2. Este funciona de forma muy similar a los anteriores, aquí la clase Emitter genera en cada frame nuevas partículas que pueden ser círculos (Particle) o cuadrados (Confetti). Cada objeto tiene un ciclo de vida definido por lifespan. Cuando este llega a cero, isDead() devuelve true y se elimina con splice(). Gracias a este control, el arreglo se mantiene con un número estable de partículas. Si no existiera este mecanismo, el run() debería recorrer un arreglo cada vez más grande, provocando ralentizaciones notorias y un consumo innecesario de memoria.
> 3.En este caso, quise aplicar el concepto de random gaussiano para darle variabilidad natural al tamaño y al color de las partículas. Lo implementé usando randomGaussian() dentro de los constructores o del método show() de Particle y Confetti, generando así valores alrededor de una media con cierta desviación estándar. La idea fue que los círculos tengan colores fríos y tamaños variados y los cuadrados colores cálidos. Aquí, el random gaussiano, interactúa directamente con las propiedades visuales de cada objeto Particle. Al asignar el resultado de randomGaussian() a los atributos de color (this.col) y tamaño (this.size) dentro del constructor, cada partícula nace con una identidad visual única pero coherente con el grupo. Esta interacción es la que produce la apariencia de un conjunto variado pero natural..
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
> 2. En este ejemplo también se emplea un Emitter. Cada frame genera partículas que pueden ser normales o de tipo péndulo. Todas reducen su lifespan hasta que isDead() las descarta con splice(). Esto mantiene estable el tamaño del arreglo y evita fugas de memoria. Si las partículas no se eliminaran, el bucle run() debería recorrer un arreglo cada vez más grande, lo que afectaría directamente la eficiencia de la simulación.
> 3. En este ejemplo apliqué el concepto de péndulo para las partículas. Lo implementé usando coordenadas polares, la gravedad se proyecta como aceleración angular: aAcceleration = (-g / r) * sin(angle),donde cada partícula tiene un ángulo y una longitud desde su origen, y su aceleración angular se calcula con la fórmula de oscilación armónica con con sin() y cos(). Esto hace que la partícula se mueva de un lado a otro, y no en círculos completos, simulando un péndulo real que va y viene. Lo hice así para que el movimiento de las partículas fuera visualmente más interesante, mostrando oscilaciones suaves y controladas en lugar de trayectorias lineales o circulares.
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
> 2. En este código La lógica de gestión es la misma: cada partícula nace en el emisor, se actualiza en cada frame y reduce su lifespan. Cuando este llega a cero, se elimina con splice(). Así, la memoria se mantiene controlada y el rendimiento se conserva. De lo contrario, el arreglo crecería indefinidamente, ralentizando el run() con el tiempo y afectando la experiencia interactiva.
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
   > Aprovechando que Gemini me permite hacer una vista previa del código que se le da o genera, haré los primeros experimentos allí, estas pruebas serán sin audio, en vez de eso se         > usará el sonido ambiente para ver los cambios.
   > 
   > * Experimento 1.
   > * Lo primero que cree  fue la clase particula, que sería la base del sistema, ya que en ella se encuentra la lógica de todas las particulas que existiran, máS             >adelante,    > en este caso se creo con las caracteristicas deseadas para hacer el fuego, esta ya contiene el tiempo de vida por lo que despues de un tiempo las particulas mueren para                 > liberar memoría.
   >   
   > Imagen Experimento 1.
   > 
   > <img width="765" height="623" alt="image" src="https://github.com/user-attachments/assets/ef1fcbfc-6b13-4ee6-a153-8954dc445484" />
   
   > * Experimento 2.
   > Agregué las clases de particulas de agua y de humo, para que al echara agua se apague le fuergo, además que al apagarse salgan las partculas de humito.

   > Imagen Experimento 2
   > 
   > <img width="883" height="679" alt="image" src="https://github.com/user-attachments/assets/0717abbc-ea34-4609-bf40-ec1d4284fd44" />
   
   > * Experimento 3.
   >   Intente que el agua y el fuego se vieran un poco mejor, y aunque logre con blending y transparencia mejoroar la apariencia de fuego, el gaua se complico, no daba los resultados que
   >   queria y al implementar una tecnica diferente de renderizado no supe por que se creo una estela azul por un lado.
   >   
   >Imagen experimento 3
   > 
   >   <img width="610" height="687" alt="image" src="https://github.com/user-attachments/assets/50c754fc-a61c-4453-8fe1-21ab00183af2" />
   >
   > * Experimeto 4
   > Aquí volví a la forma de renderizado anterior, solo que haciendo que el agua tuviera un estela  y arregle le puse un blending al humo para que se viera más como humo.
   >
   > Imagen Experimento 4
   > 
   > <img width="492" height="490" alt="image" src="https://github.com/user-attachments/assets/28f26a59-7f41-4390-a8ec-59f7d78d63ea" />
   >
   > * Experimeto 5.
   > Quise agregar viento por lo que al oprimir las flechas en el teclado se genera una fuerzaq que mueve el fuego como si viniera viento con esa dirección.
   > 
   > Imagen Experimento 5
   > 
   > <img width="709" height="436" alt="image" src="https://github.com/user-attachments/assets/da0b2604-1130-4adc-a2ef-44b48c63ccab" />

   > * Experimento 6
   > Aquí agregué ya pasé a P5  audio y probe diferentes niveles de sensibilidad para reaccionar al sonido, logrando que los colores cambiens segun este, además agregue dos modos cuando     > escucha el sonido ambiente y cargando una cancion y reaccionando a esta.
   > 
   > Imagen Experimento 6
   > 
   > <img width="653" height="645" alt="image" src="https://github.com/user-attachments/assets/bfebedbb-20ca-42a5-86f4-03ecdd52577f" />

   > 💬 **Que comunica**
   > 
   > ✨ Quiero comunicar dualidad, el estar entre lo fuerte que puede lllegar a ser el fuego y al mismo tiempo lo fragil que se puede sentir frente al agua. Al mismo tiempo la obra          > refleja cómo algo intenso puede apagarse, o también cómo puede recuperarse y fortalecerse nuevamente. Representa lo cambiante, mostrando que, aunque muchas veces algo parezca           > extinguido, siempre queda un rastro (Humo vapor en este caso) que recuerda lo que ya no está y evidencia cómo puede permanecer de una forma no tan física, pero aún existir.✨

   > ✨ **Concepto Final**
   > 
   > 🌀La obra representa la dualidad de un mismo elemento, en este caso, el fuego. Por un lado, puede verse fuerte, imponente y casi indestructible; una fuerza que, incluso dentro de su    > fortaleza, es cambiante y capaz de representar estados y emociones.
   >
   >Sin embargo, al mismo tiempo, vive al vilo de la debilidad: tan solo un poco de agua puede llevarlo a desaparecer. Pero no todo está perdido, ya que una pequeña chispa en el lugar       >indicado es suficiente para que el fuego renazca con el mismo vigor.
   > 
   > 💫 **Explicación Obra Final**
   >
   > 🌀Al final esta obra es un fuego digital vivo que danza y reacciona al sonido. Todo lo que se ve en pantalla, desde la llama principal hasta el humo que se disipa, está creado por        > pequeñas partículas que nacen, se mueven y mueren constantemente. La llama no es estática; su forma y color cambian con la música que escucha. Los sonidos graves la hacen crecer        > y pulsar con fuerza, mientras que los agudos pueden transformarla en un fuego de tonos azules y morados, mostrando así sus diferentes "emociones".
3. Debes utilizar los conceptos de herencia y polimorfismo que revisaste en la fase de investigación.
   > Este concepto fue utilizado en el array principal sistemaParticulas para almacenar y gestionar de forma unificada objetos de clases distintas (ParticulaFuego, ParticulaAgua y           > ParticulaHumo), ya que todas heredan de la clase base Particula. El objetivo de esta implementación fue simplificar radicalmente el bucle principal del programa, permitiendo invocar    > métodos genéricos como update() y show() sobre cualquier elemento del array sin necesidad de verificar su tipo específico, lo que dio como resultado un código más limpio, organizado    > y fácilmente escalable.
5. Debes utilizar al menos un concepto de cada una de las unidades anteriores: 4 conceptos.
   > * Unidad 1:
   >   >   * Ruido Perlin (noise()): Controla el movimiento de la ParticulaHumo, dándole un aspecto de deriva suave y caótico en lugar de un movimiento predecible.
   >   >   * Distribución Gaussiana (randomGaussian()): Se usa para generar las partículas de fuego en la base, concentrándolas en el centro pero con una dispersión natural hacia los        >   >     lados, lo que le da a la llama su forma de campana.
   > * Unidad 2: (Motion 101): Es el motor fundamental de toda la simulación.
   >   >  * La clase Particula base está construida sobre este principio, con los vectores position, velocity y acceleration.
   >   >  * El método update() de cada partícula implementa la lógica central (velocidad += aceleración, posición += velocidad) que permite que todos los elementos se muevan.
   > * Unidad 3 (Fuerzas): Se aplicaron múltiples fuerzas para influir en el comportamiento de las partículas.
   >   >  * Fuerza de Viento: El vientoGlobal, controlado por las flechas del teclado, es un vector de fuerza que se aplica a las partículas de fuego y humo con applyForce().
   >   >  * Fuerza de Gravedad: La ParticulaAgua es afectada por una fuerza constante hacia abajo (applyForce(createVector(0, 0.25))) que simula la gravedad.
   >   >  * Fuerza de Atracción: La llama obtiene su forma cónica gracias a una fuerza de atracción central que empuja a las ParticulaFuego hacia el eje vertical a medida que suben, una     >   >    aplicación artística del principio de fuerzas centrales.
   > * Unidad 4 (Movimiento Angular / Oscilación): Se usó para darle vida y dinamismo a la llama.
   >   >  * Oscilación con sin(): La "danza" del fuego se logra aplicando una fuerza horizontal               >   >    oscilatoria a cada ParticulaFuego. La amplitud de esta oscilación está directamente ligada a      >   >    las frecuencias medias de la música, haciendo que la llama baile al compás.
   
7. Debes definir cómo vas a gestionar el tiempo de vida de las partículas y la memoria.
   > En mi código se gestinará el tiempo de vida de las partículas con la variable lifespan, que se reduciran en cada actualización hasta que la partícula muere. Este valor también          controla la transparencia y el tamaño, lo que genera un desvanecimiento natural en fuego, humo y agua. Para la memoria, recorro el arreglo de atrás hacia adelante y elimino con         > splice() las partículas muertas, además de limitar el sistema a 700 partículas para evitar sobrecarga.
9. La obra debe ser interactiva en tiempo real. Puedes usar teclado, mouse, música, el micrófono, video, sensor o cualquier otro dispositivo de entrada.
   > ⌨️**Interacciones finales**💫
   >   > * Mouse Click → lanza agua 💧 o fuego 🔥.
   >   > * Teclado:
   >   >      * W/F → cambia entre agua/fuego.
   >   >      * M → alterna micrófono/canción.
   >   >      * Flechas ← → → controlan viento
   >   > * Sonido: Canción y ambiente, controlan la inetsidad y colores del fuego.
   >   
11. Incluye un enlace a tu código en el editor de p5.js.
    > [Obra unidad 5](https://editor.p5js.org/LCami-Villanueva/sketches/cJ7kgQkMI)
13. Incluye el código fuente.
``` JS
    // ===================================
// VARIABLES GLOBALES
// ===================================
let sistemaParticulas = []; // El array que contendrá todas nuestras partículas
let intensidadNucleo = 1.0; // Controla la vida del núcleo del fuego (1.0 = vivo, 0.0 = apagado)
let vientoGlobal; // Vector para la fuerza del viento del teclado

// Variables de Audio
let mic;
let cancion;
let fft;
let audioStarted = false;
let perlinColorOffset = 0;
let modoCancion = false; // false = micrófono, true = canción

// Paletas de Colores
let paletaCalida = [];
let paletaFria = [];

// Textura para el fuego
let fuegoTextura;

// Interacción
let modoAgua = false;


// ===================================
// FUNCIONES PRINCIPALES DE P5.JS
// ===================================

function preload() {
  // Sube tu canción al editor de p5.js y pon el nombre aquí
  cancion = loadSound('DAN.mp3');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  colorMode(HSB, 360, 100, 100, 100);
  
  vientoGlobal = createVector(0, 0);

  // Configuración del micrófono
  mic = new p5.AudioIn();
  fft = new p5.FFT(0.8, 128);
  fft.setInput(mic); // Inicia con el micrófono por defecto

  paletaCalida = [
    color(0, 80, 100),   // Rojo
    color(20, 90, 100),  // Naranja
    color(40, 100, 100), // Amarillo-Naranja
    color(60, 100, 100), // Amarillo
    color(340, 80, 100), // Rojo-Violeta
  ];

  // Paleta de colores fríos ajustada para más morados
  paletaFria = [
    color(240, 100, 90), // Azul
    color(270, 90, 100), // Morado
    color(300, 80, 100), // Magenta
    color(280, 80, 95),  // Púrpura oscuro
  ];

  // Crear la textura del fuego programáticamente
  fuegoTextura = createGraphics(100, 100);
  fuegoTextura.noStroke();
  for (let i = 50; i > 0; i--) {
    let alpha = map(i, 50, 0, 0, 255);
    fuegoTextura.fill(255, alpha / 3);
    fuegoTextura.ellipse(50, 50, i * 2, i * 2);
  }
}

function draw() {
  if (!audioStarted) {
    background(0);
    // Espera al primer clic del usuario para empezar
    return;
  }

  fft.analyze();

  let bassEnergy = fft.getEnergy('bass');
  let midEnergy = fft.getEnergy('mid');
  let trebleEnergy = fft.getEnergy('treble');
  
  // Amplificador de sensibilidad para el micrófono
  if (!modoCancion) {
    const sensibilidad = 2.5; // Aumenta este valor para más sensibilidad
    bassEnergy = min(bassEnergy * sensibilidad, 255);
    midEnergy = min(midEnergy * sensibilidad, 255);
    trebleEnergy = min(trebleEnergy * sensibilidad, 255);
  }

  background(0);

  // Genera y actualiza partículas
  updateParticulas(bassEnergy, midEnergy, trebleEnergy);
  
  // Dibuja la escena
  drawEscena(bassEnergy, midEnergy, trebleEnergy);

  // Dibuja la interfaz de usuario
  drawUI();
}

function updateParticulas(bassEnergy, midEnergy, trebleEnergy) {
  // --- LÓGICA DE VIENTO CON TECLADO ---
  if (keyIsDown(LEFT_ARROW)) {
    vientoGlobal.x -= 0.1; // Añade fuerza hacia la izquierda
  } else if (keyIsDown(RIGHT_ARROW)) {
    vientoGlobal.x += 0.1; // Añade fuerza hacia la derecha
  }
  // El viento se disipa lentamente y tiene un límite
  vientoGlobal.mult(0.97);
  vientoGlobal.limit(2);

  // OPTIMIZACIÓN: Límite de partículas para evitar colapsos
  if (sistemaParticulas.length < 700) {
    // Genera nuevas partículas de fuego
    if (intensidadNucleo > 0.1) {
      let cantidadFuego = 1 + map(bassEnergy, 0, 255, 0, 5);
      for (let i = 0; i < cantidadFuego; i++) {
        let posX = randomGaussian(width / 2, 50);
        sistemaParticulas.push(new ParticulaFuego(posX, height - 10));
      }
    }
  }


  perlinColorOffset += 0.005;

  // Bucle principal de actualización y eliminación
  for (let i = sistemaParticulas.length - 1; i >= 0; i--) {
    let p = sistemaParticulas[i];
    
    // OPTIMIZACIÓN: El viento se aplica en el mismo bucle de actualización
    if (p instanceof ParticulaFuego || p instanceof ParticulaHumo) {
      p.applyForce(vientoGlobal);
    }

    // Lógica de interacción
    if (p instanceof ParticulaAgua) {
      for (let j = sistemaParticulas.length - 1; j >= 0; j--) {
        let otra = sistemaParticulas[j];
        if (otra instanceof ParticulaFuego && p.position.dist(otra.position) < 30) { 
          otra.lifespan = 0;
          p.lifespan -= 30; 
        }
      }
      let baseFuego = createVector(width / 2, height);
      if (p.position.dist(baseFuego) < 100) { 
        intensidadNucleo -= 0.1; 
        p.lifespan -= 15;
      }
    }

    p.update({ bass: bassEnergy, mid: midEnergy, treble: trebleEnergy });
    
    // Elimina partículas muertas
    if (p.isDead()) {
      if (p instanceof ParticulaFuego) {
        if (random(1) < 0.3) { // Probabilidad de humo ajustada al 30%
          sistemaParticulas.push(new ParticulaHumo(p.position.x, p.position.y));
        }
      }
      sistemaParticulas.splice(i, 1);
    }
  }
}

function drawEscena(bassEnergy, midEnergy, trebleEnergy) {
  // El núcleo del fuego se recupera lentamente SOLO SI está encendido.
  if (intensidadNucleo > 0.01) {
      intensidadNucleo = lerp(intensidadNucleo, 1.0, 0.01);
  }
  intensidadNucleo = constrain(intensidadNucleo, 0, 1);
  
  // CAPA 1: HUMO (MODO NORMAL)
  blendMode(BLEND);
  for (let p of sistemaParticulas) {
    if (p instanceof ParticulaHumo) {
      p.show({ bass: bassEnergy, mid: midEnergy, treble: trebleEnergy });
    }
  }

  // CAPA 2: FUEGO Y AGUA (MODO LUMINOSO)
  blendMode(ADD);
  
  // Efecto de luz ambiental
  let glowSize = map(bassEnergy, 0, 255, 200, 400) * intensidadNucleo;
  let glowAlpha = map(bassEnergy, 0, 255, 5, 20) * intensidadNucleo;
  tint(30, 90, 100, glowAlpha);
  image(fuegoTextura, width / 2, height, glowSize, glowSize);
  
  // Núcleo incandescente
  let coreSize = map(bassEnergy, 0, 255, 60, 120) * intensidadNucleo;
  let coreAlpha = map(bassEnergy, 0, 255, 60, 90) * intensidadNucleo;
  tint(30, 90, 100, coreAlpha);
  image(fuegoTextura, width / 2, height - 10, coreSize * 1.5, coreSize * 0.8);
  tint(50, 100, 100, coreAlpha * 0.5);
  image(fuegoTextura, width / 2, height - 15, coreSize * 0.8, coreSize * 1.2);
  
  // Dibuja las partículas de fuego y agua
  for (let p of sistemaParticulas) {
      if (p instanceof ParticulaFuego || p instanceof ParticulaAgua) {
        p.show({ bass: bassEnergy, mid: midEnergy, treble: trebleEnergy });
      }
  }
  
  blendMode(BLEND);
}

// ===================================
// FUNCIONES DE INTERACCIÓN Y UI
// ===================================

function drawUI() {
  push();
  // Indicador visual para el cursor del mouse
  if (modoAgua) {
    fill(100, 150, 255, 50); // Azul translúcido
    stroke(200, 220, 255, 150);
  } else {
    fill(255, 150, 50, 50); // Naranja translúcido
    stroke(255, 200, 150, 150);
  }
  strokeWeight(2);
  circle(mouseX, mouseY, 25); // Tamaño del indicador reducido
  pop();
}

function keyPressed() {
  if (key === 'w' || key === 'W') modoAgua = true;
  if (key === 'f' || key === 'F') modoAgua = false;
  if (key === 'm' || key === 'M') {
    modoCancion = !modoCancion;
    if (modoCancion) {
      mic.stop();
      cancion.loop();
      fft.setInput(cancion);
    } else {
      cancion.stop();
      mic.start();
      fft.setInput(mic);
    }
  }
}

function mousePressed() {
  if (!audioStarted) {
    userStartAudio();
    mic.start();
    audioStarted = true;
    return; // Detiene la función aquí en el primer clic
  }

  // A partir del segundo clic, esta lógica se ejecuta
  if (modoAgua) {
    if (sistemaParticulas.length < 700) {
      for (let i = 0; i < 40; i++) { // Chorro un poco más controlado
        let p = new ParticulaAgua(mouseX, mouseY);
        p.velocity.y += random(1, 3);
        p.velocity.x += random(-1, 1);
        sistemaParticulas.push(p);
      }
    }
  } else {
    // Si el fuego está apagado Y hacemos clic en la parte inferior, lo reavivamos.
    if (intensidadNucleo <= 0.01 && mouseY > height * 0.75) {
      intensidadNucleo = 1.0; // ¡Vuelve el fuego!
    }
    // Siempre creamos chispas al hacer clic en este modo.
    for (let i = 0; i < 15; i++) {
      sistemaParticulas.push(new ParticulaFuego(mouseX, mouseY, true));
    }
  }
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
}


// ===================================
// CLASES DE PARTÍCULAS
// ===================================

class Particula {
  constructor(x, y, lifespan = 100) {
    this.position = createVector(x, y);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
    this.mass = 1;
    this.lifespan = lifespan;
    this.initialLifespan = lifespan;
  }
  applyForce(force) {
    let f = force.copy();
    f.div(this.mass);
    this.acceleration.add(f);
  }
  update(audioData) {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.acceleration.mult(0);
    this.lifespan -= 1;
  }
  isDead() { return this.lifespan < 0; }
  show(data) { /* Placeholder */ }
}

class ParticulaFuego extends Particula {
  constructor(x, y, avivada = false) {
    super(x, y, random(80, 120));
    let velY = avivada ? random(-3, -5) : random(-1, -3);
    this.velocity = createVector(random(-1, 1), velY);
    this.initialRadius = random(40, 70);
    this.radius = this.initialRadius;
    this.oscOffset = random(TWO_PI);
  }
  update(audioData) {
    this.applyForce(createVector(0, -0.07));
    // La danza (oscilación) es más sutil para una forma más vertical
    let oscilacionAmp = map(audioData.mid, 0, 255, 0.1, 0.5);
    let oscilacion = sin(frameCount * 0.1 + this.oscOffset) * oscilacionAmp;
    this.applyForce(createVector(oscilacion, 0));
    
    // La forma de la llama se mantiene más unida
    let centroX = width / 2;
    let fuerzaCentrado = createVector(centroX - this.position.x, 0);
    // Ajustado para que los bajos no la expandan tanto y sea más vertical
    let bassFactor = map(audioData.bass, 0, 255, 1.0, 0.6); 
    let factorAltura = map(this.position.y, height, 0, 0, 0.15) * bassFactor; 
    fuerzaCentrado.mult(factorAltura);
    this.applyForce(fuerzaCentrado);
    
    super.update(audioData);
  }
  show(audioData) {
    // --- LÓGICA DE COLOR DANZANTE Y SENSIBLE ---
    let perlinVal = noise(perlinColorOffset + this.position.x * 0.01);
    let warmColorIndex = floor(map(perlinVal, 0, 1, 0, paletaCalida.length));
    let c_warm = paletaCalida[warmColorIndex];
    let coldColorIndex = floor(map(perlinVal, 0, 1, 0, paletaFria.length));
    let c_cold = paletaFria[coldColorIndex];
    
    // RANGO AJUSTADO PARA MAYOR SENSIBILIDAD A LOS AGUDOS
    let coolnessFactor = map(audioData.treble, 70, 130, 0, 1);
    coolnessFactor = constrain(coolnessFactor, 0, 1);
    let finalColor = lerpColor(c_warm, c_cold, coolnessFactor);

    let finalSaturation = lerp(saturation(finalColor), 100, map(audioData.mid, 0, 255, 0, 0.5));
    let c = color(hue(finalColor), finalSaturation, brightness(finalColor));
    
    let lifeRatio = this.lifespan / this.initialLifespan;
    let alpha = lifeRatio * lifeRatio * 100;
    let currentRadius = this.initialRadius * lifeRatio;
    
    imageMode(CENTER);
    let glowBrightness = map(audioData.bass, 0, 255, 70, 90) * lifeRatio;
    tint(hue(c), saturation(c), glowBrightness, alpha * 0.5);
    image(fuegoTextura, this.position.x, this.position.y, currentRadius, currentRadius);
    let coreBrightness = map(audioData.bass, 0, 255, 95, 110) * lifeRatio;
    tint(hue(c), saturation(c), coreBrightness, alpha);
    image(fuegoTextura, this.position.x, this.position.y, currentRadius * 0.5, currentRadius * 0.5);
  }
}

class ParticulaAgua extends Particula {
  constructor(x, y) {
    super(x, y, 150); // Vida más corta para optimizar
    this.velocity = p5.Vector.random2D().mult(random(1, 4));
    this.velocity.y = abs(this.velocity.y) * 0.5;
    this.radius = random(4, 8);
  }
  update(audioData) {
    this.applyForce(createVector(0, 0.25));
    super.update(audioData);
  }
  show(audioData) {
    let lifeRatio = this.lifespan / this.initialLifespan;
    let alpha = lifeRatio * lifeRatio * 100;
    let currentRadius = this.radius * lifeRatio;

    // --- ESTELA ("CHORRITO") OPTIMIZADA ---
    let tail = this.velocity.copy();
    tail.mult(-1);
    tail.setMag(map(this.velocity.mag(), 0, 15, 5, 20));
    
    // El color y el grosor se desvanecen con la vida
    stroke(195, 80, 100, alpha * 0.7);
    strokeWeight(currentRadius);
    line(this.position.x, this.position.y, this.position.x + tail.x, this.position.y + tail.y);
  }
}

class ParticulaHumo extends Particula {
  constructor(x, y) {
    super(x, y, random(50, 100)); // Vida más corta para el humo
    this.velocity = createVector(random(-0.2, 0.2), random(-0.3, -0.8));
    this.initialRadius = random(15, 25);
    this.noiseOffset = createVector(random(1000), random(1000));
    this.angle = random(TWO_PI);
    this.angleVelocity = random(-0.01, 0.01);
  }
  update(audioData) {
    this.angle += this.angleVelocity;
    // Movimiento orgánico con Ruido Perlin
    let noiseForceX = map(noise(this.noiseOffset.x), 0, 1, -0.05, 0.05);
    let noiseForceY = map(noise(this.noiseOffset.y), 0, 1, -0.01, 0);
    this.applyForce(createVector(noiseForceX, noiseForceY));
    this.noiseOffset.add(0.01, 0.01);
    super.update(audioData);
  }
  show(audioData) {
    let lifeRatio = this.lifespan / this.initialLifespan;
    // El humo se expande
    let currentRadius = map(lifeRatio, 1, 0, this.initialRadius, this.initialRadius * 3);
    // Y se desvanece
    let alpha = map(lifeRatio, 1, 0, 25, 0);

    push();
    translate(this.position.x, this.position.y);
    rotate(this.angle);
    tint(0, 0, 80, alpha); // Tinte gris
    imageMode(CENTER);
    image(fuegoTextura, 0, 0, currentRadius, currentRadius);
    pop();
  }
}
 ```    
14. Captura de pantallas de tu obra con las imágenes que más te gusten
    <img width="625" height="635" alt="image" src="https://github.com/user-attachments/assets/15a288a5-3ac6-44ab-b492-3ada5b593d7f" />


## Autoevealuación
**Nota Propuesta:** 5

1.1. Investigación y Experimentación (Evidencia en Actividad 2) 
> * Explica memoria/ciclo de vida en todos los ejemplos.
> * Explica conceptos aplicados y su efecto en todos los ejemplos.
> * Explica la interrelación (array ↔ rendimiento ↔ concepto aplicado.
> * Cada prueba explica el concepto que se agregó y por que.
  
2. Intención y Diseño (Proceso de Actividad 3)
> Evidencia:
> * La bitácora incluye bocetos y explicación conceptual (dualidad fuego/agua, fragilidad/fuerza).
> * Documentas las decisiones estéticas y el proceso (paletas cálidas y frías).
> * Las interacciones (mouse, teclado, audio) aparecen explicadas como parte del diseño, no improvisadas.

3. Aplicación Técnica (Código de Actividad 3)
> Evidencia:
> * Uso de class Particula y subclases ParticulaFuego, ParticulaAgua, ParticulaHumo, cada una teien comportamientos diferentes observables.
> * Uso de polimorfismo (update() y show() sobrescritos).
> * Funciones claras para organización: updateParticulas(), drawEscena(), drawUI().
> * Cada partícula tiene lifespan.
> * Cuando lifespan <= 0, se elimina con splice.
> * Hay un límite máximo (700 partículas) para evitar desbordamiento.

4. Calidad de la Obra Final (Artefacto Entregado)
> * El sistema corre estable después del inicio.
> * Se controla la cantidad de partículas para que no haya sobrecarga.
> * Micrófono: Afecta los colores del fuego.
> * Canción: Permite una versión estable y reproducible que da resultados visuales diferentes.






















