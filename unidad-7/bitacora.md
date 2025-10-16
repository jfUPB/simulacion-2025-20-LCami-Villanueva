# Evidencias de la unidad 7
## Set: 💡
### Actividad 01 🧐

1. Tu análisis de 3-4 ejemplos de Ji Lee, explicando cómo logran la conexión palabra-imagen.
>
>### **Zipper**
>
><img width="478" height="478" alt="image" src="https://github.com/user-attachments/assets/f188af32-748f-4e52-b324-90f7dbc167c0" />
>
> En este ejemplo refuerzó la idea de la palabra Zipper usando una línea con formas que simulan los dientes de una cremallera. Esta línea divide la palabra y se ubica entre las letras “P” y “R”, simula los dientes y el cierre característico de una cremallera, a la vez que se ve como la "E",  haciendo que el diseño refleje directamente el significado del término y el termino al mismo tiempo.
>
> ### **Tunnel**
>
> <img width="478" height="483" alt="image" src="https://github.com/user-attachments/assets/ba8cbbc7-2f4b-4711-9bad-fe7a5bb72c37" />
>
> En este ejemplo se representa la forma de un túnel uniendo y separando las letras “n”. La franja negra entre ellas crea la sensación de profundidad, haciendo que una “n” parezca la entrada y la otra la salida. De esta forma, el diseño refuerza visualmente el significado de la palabra.
>
> ### Garfield 
>
> <img width="470" height="457" alt="image" src="https://github.com/user-attachments/assets/9dffa871-b9f4-4293-aaf7-9a15bf86c13b" />
>
>En este ejemplo se repite la letra “G” para simular los ojos característicos del gato Garfield. Aunque no se muestra directamente al personaje, el diseño representa una de sus rasgos más reconocibles de forma simple y visual. Tipográficamente, se usa una fuente gruesa y redondeada que refuerza el estilo divertido y caricaturesco del personaje.
>
> ### **Memory**
>
> <img width="461" height="479" alt="image" src="https://github.com/user-attachments/assets/0f075f53-d0a0-47fa-9431-27bddbd523d2" />
>
> En este ejemplo se representa cómo, con el paso del tiempo, la memoria se va desvaneciendo. Las primeras letras aparecen más claras y difusas, mientras que las últimas son más oscuras y definidas. Este cambio visual refuerza la idea del olvido y de cómo los recuerdos se vuelven menos nítidos con el tiempo.

2. Tus propias ideas (descripción o boceto simple) para representar visualmente 2-3 palabras distintas de forma estática.
   >
   >  ### Semilla:
   >
   > <img width="927" height="506" alt="image" src="https://github.com/user-attachments/assets/118ea529-1a55-411c-ad4a-6a386d53b119" />
   >
   >Para la palabra 'Semilla' imagino una historia de crecimiento. La 'S' contiene la tierra y las raíces desde donde nace todo. Aunque el diseño es estático, lo imagino animado: empezando con un montículo de tierra, cae una semilla, las raíces y la 'S' brotan, y el resto de las letras surgen del suelo, culminando con la hoja de la 'i' y los tallos de las 'l'
   >
   > ### Ola
   >
   > <img width="818" height="578" alt="image" src="https://github.com/user-attachments/assets/5d3f2cf4-45de-4268-9504-4eb8aa718c1d" />
   >
   >Para 'Ola', mi idea fue transformar la palabra en un solo gesto fluido. La 'O' es la protagonista, convirtiéndose en una ola grande y estilizada que domina la composición. Las letras 'l' y 'a' no la siguen, sino que son parte de su estela, arrastradas por la misma fuerza del agua. Así, la palabra entera se siente como un único movimiento dinámico que captura la esencia del mar.
   >
   > ### Caída
   >
   ><img width="385" height="375" alt="image" src="https://github.com/user-attachments/assets/b134a84d-75e7-4f97-871c-ac52e7fa7415" />
   >
   >Para 'Caída', la palabra sigue una trayectoria descendente donde cada letra está más rotada que la anterior, mostrando la aceleración. Detalles clave, como el la 'a' final deformada en el suelo, marca el impacto.
   
## Seek: Investigación 🔎
### Actividad 02 ✍️ 
1. Muestra el código de los dos (o más) experimentos básicos que replicaste integrando Matter.js y p5.js.
   > Experimento 1: 🧪   **Crear un mundo con gravedad y añadir algunos cuerpos simples (círculos, cajas) que caigan y colisionen.**
   >   > ✨ Para este ejercicio, mi objetivo fue crear un mundo básico con gravedad usando Matter.js, basándome en el primer ejemplo del video que integra la librería con p5.js. De ahí tomé la estructura fundamental: crear el Engine y el World en el setup(), y lo más importante, actualizar la simulación con Engine.update(engine) dentro del draw(). A partir de esa base, construí mi propia escena añadiendo un suelo estático y varios Bodies dinámicos como cajas y círculos. Finalmente, creé una función para dibujarlos que simplemente toma la posición y el ángulo que Matter.js calcula y los representa en el lienzo de p5.js.✨
   >   >
``` JS
  // Módulos que vamos a usar de Matter.js
const { Engine, World, Bodies, Composite } = Matter;

// Variables para el motor de física y los objetos
let engine;
let world;
let ground;
let shapes = []; // Un arreglo para guardar todas nuestras figuras

function setup() {
  // 1. Creamos el lienzo (canvas) de p5.js
  createCanvas(600, 400);

  // 2. Creamos el motor de física y el mundo
  engine = Engine.create();
  world = engine.world;

  // 3. Creamos nuestros cuerpos (bodies)

  // El suelo: es un cuerpo estático para que no se caiga
  ground = Bodies.rectangle(width / 2, height - 10, width, 20, {
    isStatic: true
  });
  // Le añadimos sus dimensiones para poder dibujarlo con la misma función
  ground.w = width;
  ground.h = 20;


  // Cuerpos simples: círculos y cajas (dinámicos)
  let box1 = Bodies.rectangle(200, 50, 80, 80, { restitution: 0.8, friction: 0.1 });
  // Guardamos sus dimensiones originales
  box1.w = 80;
  box1.h = 80;

  let circle1 = Bodies.circle(300, 20, 40, { restitution: 0.5 });
  // Guardamos su radio original
  circle1.r = 40;

  let box2 = Bodies.rectangle(250, 150, 50, 50, { angle: PI / 4 });
  // Guardamos sus dimensiones originales
  box2.w = 50;
  box2.h = 50;


  // 4. Añadimos todos los cuerpos al mundo
  Composite.add(world, [ground, box1, circle1, box2]);

  // Guardamos las figuras dinámicas en nuestro arreglo para dibujarlas
  shapes.push(box1);
  shapes.push(circle1);
  shapes.push(box2);
}

function draw() {
  background(51); // Fondo oscuro

  // 5. Actualizamos el motor de física en cada fotograma
  Engine.update(engine);

  // 6. Dibujamos todos los cuerpos en el lienzo de p5.js

  // Dibujar el suelo
  fill(170);
  noStroke();
  drawBody(ground);

  // Dibujar las figuras dinámicas
  fill(255, 100, 200); // Color rosado para las figuras
  stroke(255);
  for (let shape of shapes) {
    drawBody(shape);
  }
}

// Función auxiliar para dibujar cualquier tipo de cuerpo (body)
function drawBody(body) {
  // Si el cuerpo es un rectángulo
  if (body.label === 'Rectangle Body') {
    let pos = body.position;
    let angle = body.angle;

    push();
    translate(pos.x, pos.y);
    rotate(angle);
    rectMode(CENTER);
    // Usamos las dimensiones guardadas
    rect(0, 0, body.w, body.h);
    pop();
  }

  // Si el cuerpo es un círculo
  if (body.label === 'Circle Body') {
    let pos = body.position;

    push();
    translate(pos.x, pos.y);
    ellipseMode(CENTER);
    // Usamos el radio guardado
    ellipse(0, 0, body.r * 2);
    pop();
  }
}
```
   > Experimento 2: 🧪  **Crear cuerpos estáticos (como el suelo)**.
   >   > ✨ Para este segundo experimento, el foco era entender y crear cuerpos estáticos. Ya había usado uno para el suelo, pero quería explorar cómo crear un entorno más complejo. Descubrí que la clave es muy simple: al crear cualquier Body (sea un rectángulo o cualquier otra forma), solo hay que añadir la opción { isStatic: true }. Esto le dice a Matter.js que ese objeto es inamovible: no le afecta la gravedad ni las colisiones, simplemente se queda fijo en su lugar. En mi sketch, además del suelo, añadí una rampa (que es solo un rectángulo estático con un ángulo) y una pared lateral, creando así un escenario fijo donde los cuerpos dinámicos pueden rebotar y deslizarse.✨
   >   >
``` JS
// Módulos de Matter.js
const { Engine, World, Bodies, Composite } = Matter;

let engine;
let world;

// Arreglos para guardar los cuerpos
let dynamicShapes = [];
let staticShapes = [];

function setup() {
  createCanvas(600, 400);

  engine = Engine.create();
  world = engine.world;

  // --- CUERPOS ESTÁTICOS (el escenario) ---

  // 1. El suelo
  let ground = Bodies.rectangle(width / 2, height - 10, width, 20, {
    isStatic: true // La propiedad clave para que no se mueva
  });
  ground.w = width;
  ground.h = 20;

  // 2. Una rampa
  let ramp = Bodies.rectangle(300, 300, 400, 20, {
    isStatic: true,
    angle: -PI / 12 // Le damos una inclinación
  });
  ramp.w = 400;
  ramp.h = 20;

  // Añadimos los cuerpos estáticos a su arreglo
  staticShapes.push(ground, ramp);


  // --- CUERPOS DINÁMICOS (los que caen) ---

  let box = Bodies.rectangle(100, 50, 40, 40, { restitution: 0.8 });
  box.w = 40;
  box.h = 40;

  let circle = Bodies.circle(450, 20, 25, { restitution: 0.6 });
  circle.r = 25;

  // Añadimos los cuerpos dinámicos a su arreglo
  dynamicShapes.push(box, circle);


  // Finalmente, añadimos TODOS los cuerpos al mundo
  Composite.add(world, staticShapes);
  Composite.add(world, dynamicShapes);
}

function draw() {
  background(51);
  Engine.update(engine);

  // Dibujar los cuerpos estáticos (grises)
  fill(170);
  noStroke();
  for (let body of staticShapes) {
    drawBody(body);
  }

  // Dibujar los cuerpos dinámicos (rosados)
  fill(255, 100, 200);
  stroke(255);
  for (let body of dynamicShapes) {
    drawBody(body);
  }
}

// Función para añadir más figuras con el mouse
function mousePressed() {
  let newShape;
  if (random(1) > 0.5) {
    newShape = Bodies.rectangle(mouseX, mouseY, 30, 30, { restitution: 0.8 });
    newShape.w = 30;
    newShape.h = 30;
  } else {
    newShape = Bodies.circle(mouseX, mouseY, 15, { restitution: 0.5 });
    newShape.r = 15;
  }
  dynamicShapes.push(newShape);
  Composite.add(world, newShape);
}


// Función auxiliar para dibujar cualquier tipo de cuerpo
function drawBody(body) {
  if (body.label === 'Rectangle Body') {
    let pos = body.position;
    let angle = body.angle;
    push();
    translate(pos.x, pos.y);
    rotate(angle);
    rectMode(CENTER);
    rect(0, 0, body.w, body.h);
    pop();
  }

  if (body.label === 'Circle Body') {
    let pos = body.position;
    push();
    translate(pos.x, pos.y);
    ellipseMode(CENTER);
    ellipse(0, 0, body.r * 2);
    pop();
  }
}
```

3. Incluye una **captura de pantalla o ENLACE a un GIF (no olvides, enlace) de cada experimento funcionando.**
   > Experimento 1: 🧪 **Crear un mundo con gravedad y añadir algunos cuerpos simples (círculos, cajas) que caigan y colisionen.**
   > - [Ejemplo Mundo Con Gravedad](https://editor.p5js.org/LCami-Villanueva/sketches/dGYzPqN5L)
   > 
   > - GIF
   > 
   >   ![20251014-1853-40 9723303](https://github.com/user-attachments/assets/a3ab2d1a-1728-4761-8e17-691b24c6e347)
   > 
   > Experimento 2: 🧪
   > - [Ejemplo objeto Estatico ](https://editor.p5js.org/LCami-Villanueva/sketches/lfqodjwjb)
   >
   > - GIF
   >
   >  <img width="732" height="495" alt="image" src="https://github.com/user-attachments/assets/ee94b649-32ad-4d67-8540-af0b97b9a7d7" />
   >
4. Proporciona tu explicación clara y concisa de los conceptos clave (Engine, World, Bodies, Constraint, MouseConstraint).
   > - **Engine (Motor):** Para mí, el Engine es el cerebro de toda la simulación. Es el que se encarga de que el tiempo avance y calcula toda la física, como la gravedad y las colisiones. Aunque no lo vemos directamente, es el motor que lo mueve todo.
   > - **World (Mundo):** El World es como el escenario donde ocurre la simulación. Es el contenedor que guarda todos mis objetos (Bodies). Entendí que para que a un objeto le afecte la gravedad o pueda chocar, es obligatorio añadirlo a este mundo.
   > - **Body (Cuerpo):** Los Bodies son los actores de mi proyecto: las cajas, las pelotas, el suelo, etc. Son los objetos físicos que vemos y que tienen propiedades como masa o posición. Lo más importante es que pueden ser dinámicos (que se mueven y reaccionan) o estáticos (que son fijos, como las paredes).
   > - **Constraint (Vínculo):** Un Constraint lo veo como un vínculo invisible, como una cuerda o una varilla que une dos Bodies entre sí, o un Body a un punto fijo. Es perfecto para crear cosas como cadenas, péndulos o puentes colgantes.
   > - **MouseConstraint (Vínculo con el Mouse):** Este es simplemente la herramienta que me permite "jugar" con la simulación. Es un Constraint especial que conecta mi mouse con los Bodies, dejándome agarrarlos, arrastrarlos y lanzarlos. Es la forma más directa de hacer el proyecto interactivo.
   
5. Menciona brevemente cualquier dificultad encontrada al configurar o usar Matter.js inicialmente.
   > Realmete no tuve ninguna dificultad muy complicada, tal vez al principio que me dio error porque había referenciado mal la librería, pero no fue nada grave. 

# Apply 🛠
## Actividad 03 
### ETAPA DE DISEÑO 🎨✨
>
> ### IDEA FALLIDA 🚫❌ 
>  >Para esta etapa inicial decidí comenzar con la palabra “Ola”, trabajándola como en la imagen que realicé en la parte de ideas. Sin embargo, durante el proceso no encontré una forma adecuada de representar la ola en la letra O, y los resultados que obtuve no me convencieron. Finalmente, me rendí, ya que la idea tampoco me inspiraba lo suficiente.
>
> <img width="697" height="393" alt="image" src="https://github.com/user-attachments/assets/4996eb36-8e6e-4a1a-9846-c3b213ae4204" />
>
>- [Código Idea Fallida ❌ ](https://editor.p5js.org/LCami-Villanueva/sketches/J5eKax_XR)
>  
> 🚫 ❌
>
> ### IDEA DOS 💡✅
> > 💫 Para esta segunda idea pensé en la palabra sol, y en hacer que la O sea como el sol y tenga un resplandor. Inicialmente, las letras flotan en un espacio sin gravedad, y la "O" ya emite sutiles ondas de luz.
> > 
1. Indica claramente la palabra elegida.
   > ### Sol 
2. Explica tu idea conceptual: ¿Cómo la animación física representa el significado de la palabra?
   > La palabra "SOL". La "O" se presenta como un núcleo de energía contenida, y la interacción del usuario actúa como el catalizador que desata su verdadero significado. Al ser activada, esta se expande de forma explosiva, ejerciendo una fuerza que desplaza a las otras letras y emitiendo partículas como una erupción solar, convirtiendo así el texto en una simulación dinámica de su propio concepto.
3. Describe brevemente los aspectos técnicos clave de tu implementación: ¿Cómo formaste las letras con Matter.js? ¿Qué propiedades físicas fueron importantes? ¿Usaste restricciones?
   >
   > En esta implementación, cada letra de la palabra "SOL" está representada por un cuerpo circular invisible (Bodies.circle) en el motor de física. El carácter visual de la letra simplemente se dibuja en la
   > posición de este cuerpo físico en cada fotograma, lo que permite que el texto se comporte de acuerdo con las leyes de la simulación.
   > 
   > Las propiedades físicas más importantes fueron:
   >
   > - Gravedad Cero: world.gravity.y = 0 es fundamental para que las letras floten en el espacio en lugar de caer.
   > - Restitución y Fricción: Se ajustaron valores bajos de restitution (0.6) y friction (0.1) para dar a las letras un rebote suave y una interacción fluida, evitando que se detuvieran por completo o rebotaran de manera caótica.
   > - Densidad: La density (0.04) fue clave para que los cuerpos tuvieran suficiente masa para reaccionar de forma natural al empujarse entre sí al inicio.
   >
   > No utilicé restricciones (Constraints) de Matter.js. En su lugar, el efecto de separación durante la animación se logró de forma visual y programática. Manipulé directamente el desplazamiento (offsetX) de las letras "S" y "L" usando la función lerp(). Esta decisión fue deliberada para tener un control artístico total sobre el movimiento, asegurando una separación suave y coreografiada en lugar de una reacción física que podría ser menos predecible.
   > 
4. Incluye el código completo de tu sketch final.
``` JS
const Engine = Matter.Engine;
const World = Matter.World;
const Bodies = Matter.Bodies;
const Body = Matter.Body;

let engine;
let world;
let letters = [];
let animating = false;
let animationProgress = 0;
let particles = [];
let clickedO = false;
let concentric = [];

function setup() {
  createCanvas(800, 800);
  textAlign(CENTER, CENTER);
  textFont('Georgia');
  
  // Create Matter.js engine
  engine = Engine.create();
  world = engine.world;
  world.gravity.y = 0;
  
  // Create letter objects with manual positioning
  let word = 'SOL';
  let startX = width / 2 - 50;
  let spacing = 55;
  
  for (let i = 0; i < word.length; i++) {
    let x = startX + i * spacing;
    let y = height / 2;
    let letterSize = 150;
    
    // Create physics body for each letter
    let body = Bodies.circle(x, y, letterSize / 2, {
      restitution: 0.6,
      friction: 0.1,
      density: 0.04
    });
    
    World.add(world, body);
    
    letters.push({
      letter: word[i],
      body: body,
      letterSize: letterSize,
      offsetX: 0
    });
  }
}

function draw() {
  background(20, 30, 50);
  
  // Get sun center coordinates
  let centerX = letters[1].body.position.x + letters[1].offsetX;
  let centerY = letters[1].body.position.y;
  
  // Generate new concentric circle every few frames
  if (frameCount % 40 === 0) {
    concentric.push({
      radius: 0,
      alpha: 255
    });
  }
  
  // Draw and update concentric circles
  drawConcentricCircles(centerX, centerY);
  
  // Update physics
  if (!clickedO) {
    Engine.update(engine);
  }
  
  // Handle animation
  if (animating) {
    animationProgress += 0.02;
    
    let oLetter = letters.find(l => l.letter === 'O');
    if (oLetter && animationProgress <= 1) {
      let maxOSize = 300;
      let currentOSize = lerp(oLetter.letterSize, maxOSize, animationProgress);
      oLetter.letterSize = currentOSize;
      
      // Calculate safe separation distance
      let separation = min((width - maxOSize)/2 - 60, 110);
      
      // Apply separation to S and L
      for (let letter of letters) {
        if (letter.letter === 'S') {
          let targetOffsetX = -separation;
          letter.offsetX = lerp(letter.offsetX, targetOffsetX, 0.1);
        } else if (letter.letter === 'L') {
          let targetOffsetX = separation;
          letter.offsetX = lerp(letter.offsetX, targetOffsetX, 0.1);
        }
      }
      
      // Generate particles
      if (frameCount % 3 === 0) {
        let angle = random(TWO_PI);
        let speed = random(1, 3);
        let distance = random(currentOSize * 0.5, currentOSize * 0.8);
        particles.push({
          x: oLetter.body.position.x + 400 + cos(angle) * distance,
          y: oLetter.body.position.y + 400 + sin(angle) * distance,
          vx: cos(angle) * speed * 1.5,
          vy: sin(angle) * speed * 1.5,
          life: 1,
          particleSize: random(30, 70)
        });
      }
    }
    
    if (animationProgress > 1) {
      animating = false;
      animationProgress = 1;
    }
  }
  
  // Draw particles
  drawParticles();
  
  // Draw letters
  for (let letter of letters) {
    let pos = letter.body.position;
    
    // Custom rendering based on letter
    if (letter.letter === 'O') {
      fill(255, 200, 50);
      noStroke();
      circle(pos.x + letter.offsetX, pos.y, letter.letterSize);
      
      // Draw inner circle for sun effect
      fill(255, 220, 100, 150);
      circle(pos.x + letter.offsetX, pos.y, letter.letterSize * 0.7);
    } else {
      fill(255);
      textSize(letter.letterSize);
      text(letter.letter, pos.x + letter.offsetX, pos.y);
    }
  }
  

  
  // Apply separation if not in animation
  if (!animating && !clickedO) {
    separateLetters();
  }
  
  // Update existing particles
  for (let i = particles.length - 1; i >= 0; i--) {
    let p = particles[i];
    p.x += p.vx;
    p.y += p.vy;
    p.life -= 0.02;
    
    if (p.life <= 0) {
      particles.splice(i, 1);
    }
  }
}

function drawParticles() {
  for (let p of particles) {
    let alpha = p.life * 255;
    fill(255, 200, 50, alpha);
    noStroke();
    circle(p.x - (letters.find(l => l.letter === 'O')?.body.position.x || 0) - (letters.find(l => l.letter === 'O')?.offsetX || 0), 
           p.y - (letters.find(l => l.letter === 'O')?.body.position.y || 0), 
           p.particleSize * p.life);
  }
}

function separateLetters() {
  let oIndex = letters.findIndex(l => l.letter === 'O');
  if (oIndex !== -1) {
    // Apply separation forces
    for (let i = 0; i < letters.length; i++) {
      if (i < oIndex) {
        // Letters before O move left
        Body.applyForce(letters[i].body, letters[i].body.position, {x: -0.0, y: 0});
      } else if (i > oIndex) {
        // Letters after O move right
        Body.applyForce(letters[i].body, letters[i].body.position, {x: 0.0, y: 0});
      }
    }
  }
}

function drawConcentricCircles(centerX, centerY) {
  // Update and draw each concentric circle
  for (let i = concentric.length - 1; i >= 0; i--) {
    let c = concentric[i];
    
    // Increase radius and decrease alpha
    c.radius += 2;
    c.alpha -= 3;
    
    // Draw the circle
    noFill();
    stroke(255, 200, 50, c.alpha);
    strokeWeight(2);
    circle(centerX, centerY, c.radius * 3);
    
    // Remove if faded out
    if (c.alpha <= 0) {
      concentric.splice(i, 1);
    }
  }
}

function mousePressed() {
  // Check if click is on 'O' letter
  for (let letter of letters) {
    if (letter.letter === 'O') {
      let pos = letter.body.position;
      let d = dist(mouseX, mouseY, pos.x + letter.offsetX, pos.y);
      if (d < letter.letterSize / 2) {
        animating = true;
        animationProgress = 0;
        clickedO = true;
        particles = [];
      }
    }
  }
}
```
5. Inserta una captura de pantalla estática Y un enlace a un GIF animado (¡Esencial!) que muestre tu tipografía semántica animada en acción.
   > - [ENlace Código](https://editor.p5js.org/LCami-Villanueva/sketches/4lNsKCmqA)
   >   
   > - GIF
   >   ![20251016-0631-57 1638613](https://github.com/user-attachments/assets/8f60a52f-1c47-4dc9-b988-ca74c088da75)


    













