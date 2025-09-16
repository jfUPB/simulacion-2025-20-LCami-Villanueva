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

>3. Cada partícula recibe un noiseOffset único en el constructor y, en cada frame, se utiliza noise(this.noiseOffset, frameCount * 0.01) para obtener un valor que varía suavemente con el tiempo. Ese valor se transforma en una pequeña fuerza vertical adicional aplicada con applyForce(). Con esto se logra que las partículas no caigan en línea recta, sino que, al estar influenciadas por esa fuerza, desciendan de manera más suave, como si pesaran menos y fueran movidas por una ligera brisa que las hace flotar.
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
<img width="795" height="302" alt="image" src="https://github.com/user-attachments/assets/7b67ae96-e195-42dd-a64f-717ca55a68e3" />

### Ejemplo 4.4
> Aquí funciona de forma parecida al ejemplo anterior, solo que ahora se hace mediante otra clase llamada Emitter(). Esta clase se encarga de controlar tanto la generación como la desaparición de las partículas. Además, cada vez que haces click se crea un nuevo Emitter, el cual se encarga de gestionarse por sí mismo.
### Ejemplo 4.5
> La forma de generar las partículas es parecida al ejemplo anterior, pero con una diferencia: después de crear el Emitter, al momento de generar cada partícula se usa un random para decidir si será un círculo o un cuadrito (que corresponde a la clase Confetti). La eliminación sigue siendo igual, usando splice para quitar las partículas cuando ya no sirven.
### Ejemplo 4.6
> La gestión funciona de la misma manera que en el ejemplo anterior: se crea un Emitter en el setup y, en cada frame, este va generando una nueva partícula. Luego, gracias a la revisión con isDead(), cada partícula se elimina en el momento adecuado, lo que evita que se acumulen infinitas partículas y asegura que la memoria se libere progresivamente.
### Ejemplo 4.7
> La gestión vuelve a ser la misma: se crea un Emitter y en cada frame este genera una nueva partícula. Después, con la función isDead(), se eliminan las que ya cumplieron su ciclo.


