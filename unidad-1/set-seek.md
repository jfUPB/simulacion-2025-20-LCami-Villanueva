# Unidad 1

## 🔎 Fase: Set + Seek

### Actividad 1: 🌀

Permite crear resultados únicos en cada obra, que tienden a ser más orgánicos y naturales, generando una expresividad visual que evita lo repetitivo.

### Actividad 2 – Análisis del trabajo de Sofía ✨

En el caso de Sofía, ella usa la aleatoriedad en colores velocidad para generar las lienas, lo que permite que la obra no sea predecible ni siempre igual, dándole un efecto más orgánico y haciendo que quien la observa e interactúa con ella la perciba como única en cada ocasión.

Al mismo tiempo, esta aleatoriedad controlada asegura que, sin salirse de ciertos parámetros, se pueda definir el tipo de sensación que genera la obra en cada momento. Entonces, aunque cada ejecución sea distinta y única, produce una experiencia similar, sincronizada con la música.  

### Aplicación profesional – Artista 3D 🎨

En mi perfil profesional como artista 3D este concepto se puede aplicar en muchos aspectos: desde la generación de texturas, combinando diferentes nodos (algunos con valores aleatorios como los de ruido), hasta en la generación de estos mismos materiales y texturas de manera procedural.

Por otro lado, este concepto también se puede aplicar en la generación de modelos como árboles y en general objetos orgánicos, permitiendo así que se vean más naturales y realistas. O también en la generación de sistemas de partículas, ya que en la mayoría se usa la aleatoriedad para buscar un flujo más dinámico y realista.

### Actividad 3
- Modificar el código:

  Modifiqué el 4 del ramdom por un 3 
  
<img width="451" height="289" alt="image" src="https://github.com/user-attachments/assets/f1c68d6e-460f-4ebb-a76b-fc056589e7d8" />

- Antes de ejecutar el código, escribe en tu bitácora qué esperas que suceda.
  Al cambiar el 4 por un 3, hará que solo haya 3 posibilidades, es decir 0 (Derecha), 1 (Izquierda) o 2 (arriba) es decir, **Nunca habrá pasos hacia abajo**.

- Ejecuta el código y escribe en tu bitácora qué sucedió realmente.
  El paso nunca se dio hacia arrriba, solo hacia derecha izquierda y abajo, esto se debe a que en las cordenadas de graficos de computadores se  inicia en la esquina superior izuierda, por lo que aumenta hacía la derecha y aumenta hacia abajo, entonces al no darse y negativo nunca va hacia arriba.
  
  <img width="290" height="268" alt="image" src="https://github.com/user-attachments/assets/889e8a43-7fcc-4744-b6a0-f58259ec35a8" />
  
- Ocurrió lo que esperabas? ¿Por qué crees que sí o por qué crees que no?
  No exactamente como esperba ya que sucedio lo contario, ya que no tuve en cuenta como funcionaba este sistema de coordenadas y lo tome como un sistema de coordenadas normal no uno de gráficos de computador.

 ### Actividad 4
- En tus propias palabras cuál es la diferencia entre una distribución uniforme y una no uniforme de números aleatorios.

Un sistema de distribución uniforme es un sistema en que todos los números tiene la misma probabilidad de salir, es decir si son 4 números cada uno tiene un 25% de probabilidad de salir.

Un sistema de distribución no uniforme tiende hacia un número definido, es decir, es más probable que salgan valores cercanos a ese número. En este caso, se puede definir una desviación, que representa qué tanto pueden alejarse los valores de esa media.
  
- Modifica el código de la caminata aleatoria para que utilice una distribución no uniforme, favoreciendo el movimiento hacia la derecha.
<img width="811" height="240" alt="image" src="https://github.com/user-attachments/assets/0b6b21db-e92f-47d0-bcac-3ccc821ba44c" />


  Así se favorece el moviemiento hacia la derecha ya que al sumar 1  esto dezplaza la media hacia la derecha.

  
 ### Actividad 5
**Distribución Normal**      
- Crea un nuevo sketch en p5.js que represente una distribución normal.
- Copia el código en tu bitácora.

```let total = 1000; // Total de muestras que queremos generar
let bins = new Array(50).fill(0); // 50 "cajones" para agrupar los valores
let media = 250;
let desviacion = 40;

function setup() {
  createCanvas(600, 400);
  background(255);

  // Generar mil valores distribuidos normalmente
  for (let i = 0; i < total; i++) {
    let num = randomGaussian() * desviacion + media;

    // Mapear valor a un índice del histograma
    let index = floor(map(num, 150, 350, 0, bins.length));
    if (index >= 0 && index < bins.length) {
      bins[index]++;
    }
  }
}

function draw() {
  background(255);
  stroke(0);
  fill(100, 150, 255);

  let w = width / bins.length;

  // Dibujar cada barra del histograma
  for (let i = 0; i < bins.length; i++) {
    let h = bins[i] * 4; // escalar altura para que se vea mejor
    rect(i * w, height - h, w, h);
  }

  noLoop(); // Solo dibujar una vez
}
```
- Coloca en enlace a tu sketch en p5.js en tu bitácora.
https://editor.p5js.org/LCami-Villanueva/sketches/fN5sRFIDK
  
- Selecciona una captura de pantalla de tu sketch y colócala en tu bitácora.

  

  <img width="807" height="689" alt="image" src="https://github.com/user-attachments/assets/500583b9-95d2-4c3e-aa98-003a6c580608" />


  <img width="759" height="543" alt="image" src="https://github.com/user-attachments/assets/4accabf9-fc4f-49ef-89e8-1a9b359d63ed" />

 ### Actividad 6
**Lévy flight**   
- Crea un nuevo sketch en p5.js donde modifiques uno de los ejemplos anteriores y adiciones de Lévy flight.
- Explica por qué usaste esta técnica y qué resultados esberabas obtener.


Usé la técnica de Lévy flight para simular un movimiento más natural e impredecible. Esta técnica mezcla pasos pequeños y frecuentes (generados con distribución normal) con saltos largos y poco frecuentes (Lévy flights), lo que produce trayectorias realistas y complejas.

  
- Copia el código en tu bitácora.

```let walker;

function setup() {
  createCanvas(400, 400);
  walker = new Walker();
  background(240);
}

function draw() {
  walker.step();
  walker.display();
}

class Walker {
  constructor() {
    this.x = width / 2;
    this.y = height / 2;
  }

  step() {
    let stepX, stepY;
    
    // 5% de las veces: paso largo (Lévy flight)
    if (random(1) < 0.05) {
      stepX = random(-100, 100);
      stepY = random(-100, 100);
    } else {
      // 95% de las veces: paso normal (distribución gaussiana)
      stepX = randomGaussian() * 10;
      stepY = randomGaussian() * 10;
    }

    this.x += stepX;
    this.y += stepY;

    // Limitar dentro del canvas
    this.x = constrain(this.x, 0, width);
    this.y = constrain(this.y, 0, height);
  }

  display() {
    stroke(0);
    point(this.x, this.y);
  }
}
```

- Coloca en enlace a tu sketch en p5.js en tu bitácora.
https://editor.p5js.org/LCami-Villanueva/sketches/1MQHB68oS


  
- Selecciona una captura de pantalla de tu sketch y colócala en tu bitácora.


  <img width="639" height="724" alt="image" src="https://github.com/user-attachments/assets/65e6b7d1-7987-4c13-9fdd-46c2590b645d" />

   ### Actividad 7

- Crea un nuevo sketch en p5.js donde los visualices.
- Explica el concepto qué resultados esberabas obtener.

  El Perlin Noise es una función matemática que genera una secuencia de números con transiciones suaves, es decir, no cambia abruptamente como random(). Esto lo hace ideal para representar movimientos o patrones naturales como el viento, las olas, el fuego o el crecimiento orgánico. A diferencia del ruido aleatorio tradicional, el ruido Perlin mantiene cierta continuidad, lo que permite crear animaciones más fluidas y realistas.

  Con este experimento, esperaba lograr un movimiento suave y natural en el lienzo. A diferencia de random(), que hace que los puntos salten de forma impredecible, el ruido Perlin permite que las figuras (como el círculo del sketch) se desplacen suavemente por la pantalla, casi como si fueran impulsadas por el viento. El resultado es una animación más armoniosa y menos caótica, ideal para representar comportamientos orgánicos o naturales.
     
- Copia el código en tu bitácora.

``` let t = 0; // Tiempo para controlar el ruido

function setup() {
  createCanvas(600, 400);
  background(255);
  noFill();
}

function draw() {
  stroke(100, 100, 250, 100);
  strokeWeight(2);
  
  let x = noise(t) * width;
  let y = noise(t + 1000) * height; // +1000 para que X y Y sean diferentes

  ellipse(x, y, 20, 20);
  
  t += 0.01; // Incremento lento para mantener suavidad
}
```
- Coloca en enlace a tu sketch en p5.js en tu bitácora.
  https://editor.p5js.org/LCami-Villanueva/sketches/eIBMRL1kG

  
- Selecciona una captura de pantalla de tu sketch y colócala en tu bitácora.

  <img width="609" height="331" alt="image" src="https://github.com/user-attachments/assets/3b47a575-b674-4ca5-ba66-cd7d63f3dbe6" />


  




 

  

  
  



 
  

  

