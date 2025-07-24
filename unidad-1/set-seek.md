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
  - Crea un nuevo sketch en p5.js que represente una distribución normal.
 
    
     Decidí hacer mi sketch sobre la edad de las personas universitarias. Si bien puedes encontrar muchas edades, el rango casi siempre va de los 17 a los 25 años aproximadamente. Por eso, la media sería 21 con una           desviación de 2, para que la mayoría esté entre los 19 y los 23 años, que sería lo más común. Igual, un 2 es razonable porque no queremos que se disperse tanto, y así la mayoría queda entre los 17 y 25.
    
  - Copia el código en tu bitácora.
```
let edades = []; // Guardamos las edades generadas
let media = 21;
let desviacion = 2;

function setup() {
  createCanvas(640, 240);
  background(255);
  textSize(12);
  fill(0);
  text('Distribución de Edades universitarios de Pregrado ', 180, 20);
  frameRate(60); // Controlar la velocidad de generación
}

function draw() {
  // Simulamos una edad según distribución normal
  let edad = randomGaussian(media, desviacion);
  edades.push(edad);

  // Convertimos edad a posición x en pantalla
  let x = map(edad, 14, 28, 50, width - 50, true); // 16 a 26 años como rango visible
  let y = random(height / 2, height);

  noStroke();
  fill(100, 150, 255, 30); // azul claro, con transparencia
  circle(x, y, 10);

  // Dibujamos escala de edad abajo
  for (let i = 14; i <= 28; i++) {
    let xi = map(i, 14, 28, 50, width - 50);
    fill(0);
    text(i, xi - 5, height - 10);
  }

  // Detener cuando hay muchas
  if (edades.length > 2000) noLoop();
}
```
  - Coloca en enlace a tu sketch en p5.js en tu bitácora.
    https://editor.p5js.org/LCami-Villanueva/sketches/E-B4HfObl
    
  - Selecciona una captura de pantalla de tu sketch y colócala en tu bitácora.
    

<img width="869" height="326" alt="image" src="https://github.com/user-attachments/assets/03c7e96b-4eeb-4433-bf44-328c0492c37d" />

 ### Actividad 6   
 
- Crea un nuevo sketch en p5.js donde modifiques uno de los ejemplos anteriores y adiciones de Lévy flight.
  Decidí escoger el ejemplo de la distribución de edades de los estudiantes universitarios de pregrado, simulando una población donde la mayoría de personas se concentran entre los 17 y 25 años. Con una distribución normal con una media de 21 y una desviación estandar de 2, y agregar el Lévy flight.
  
- Explica por qué usaste esta técnica y qué resultados esberabas obtener.

  Use esta técnica para mostrar casos poco frecuentes con edades muy distintas al promedio, como por ejemplo niños prodigio (entre 10 y 14 años) o adultos mayores que regresan a estudiar (entre 30 y 80 años). La elegí  porque, aunque son raros, estos casos existen en la realidad y pueden tener un impacto significativo en la diversidad y en la dinámica de una comunidad académica.

Esperaba que, al incluir Lévy flights, el gráfico no solo muestre la forma típica de una distribución normal, sino que también haga visibles esas excepciones que no suelen considerarse. Visualmente, buscaba que se destacaran estos puntos fuera de lo común, teniendo en cuenat que esto puede acercarse más a la realidad. 

- Copia el código en tu bitácora.

```
let edades = [];
let media = 21;
let desviacion = 2;

function setup() {
  createCanvas(800, 300);
  background(240);
  textSize(12);
  fill(0);
  textAlign(CENTER);
  text('Distribución de Edades Universitarias + Lévy Flight', width / 2, 20);
  frameRate(60);
}

function draw() {
  let edad;
  
  // Con 97% de probabilidad generamos edad normal
  if (random(1) < 0.97) {
    edad = randomGaussian(media, desviacion);
  } else {
    // 3% de probabilidad de un Lévy flight (niños o adultos mayores)
    if (random(1) < 0.5) {
      edad = random(10, 14); // niños prodigio
    } else {
      edad = random(30, 80); // adultos mayores
    }
  }

  edades.push(edad);

  // Expandimos el mapeo en X para ver edades de 10 a 80
  let x = map(edad, 10, 80, 50, width - 50, true);
  let y = random(height / 2, height - 20);

  noStroke();
  if (edad < 17 || edad > 25) {
    fill(255, 100, 100, 60); // rojo para destacar Lévy flight
  } else {
    fill(100, 150, 255, 30); // azul normal
  }
  circle(x, y, 10);

  // Escala de edades en la parte inferior
  for (let i = 10; i <= 80; i += 5) {
    let xi = map(i, 10, 80, 50, width - 50);
    fill(0);
    text(i, xi, height - 5);
  }

  if (edades.length > 2000) {
    noLoop();
  }
}
```

- Coloca en enlace a tu sketch en p5.js en tu bitácora.  https://editor.p5js.org/LCami-Villanueva/sketches/jOEaQhc8g

- Selecciona una captura de pantalla de tu sketch y colócala en tu bitácora.

  <img width="823" height="409" alt="image" src="https://github.com/user-attachments/assets/8cd62c56-6585-4e77-914a-ee2529004785" />

  

