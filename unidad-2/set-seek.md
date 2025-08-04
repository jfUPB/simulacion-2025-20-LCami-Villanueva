# Unidad 2

## 🔎 Fase: Set + Seek

### Actividad 01
- ¿Cómo funciona la suma dos vectores en p5.js?
  
  > La suma de vetores en p5.js funciona igual que en la geometría euclidiana y bajo ese mismo concepto, sumar los componentes correspondientes de cada vector. Esto se hace atraves de la **función .add**, esta permite que los vectore sse sumen correctamente, es decor los componente en x de un vector con los en x del otro, los componentes en y de uno con los del otro, y así depenediendo de la dimension en que se encuentre el vector. Para obtener el vector que rfepresenta la suma de los vectores originales.
  
- ¿Por qué esta línea position = position + velocity; no funcio
   > No funciona porque en JavaScript el operador + está diseñado para trabajar con valores primitivos, como numeros entero, flotantes o cadenas, pero no sabe cómo sumar objetos como los Vectores. Cuando escribimos position = position + velocity, estamos intentando sumar dos objetos, lo cual no está definido en JavaScript. Por eso, en p5.js se utiliza el método .add(), que está programado para realizar la suma componente a componente entre vectores.

### Actividad 02

Realiza este ejercicio del libro Ejercicio 1.1

- ¿Qué tuviste que hacer para hacer la conversión propuesta?
  
  > - Cambié dos variables (x, y) por un solo Vector.
  > - Sustituí operaciones escalares que usan (+ o -) por métodos del vector (.add()).
  > - Adapté las funciones como point() donde dibujo el punto para usar los componentes del vector.
  
- Muestra el código que utilizaste para resolver el ejercicio.
```javascript  
let walker;

function setup() {
  createCanvas(640, 240);
  walker = new Walker();
  background(255);
}

function draw() {
  walker.step();
  walker.show();
}

class Walker {
  constructor() {
    // Usé un vector para representar la posición
    this.position = createVector(width / 2, height / 2);
  }

  show() {
    stroke(0);
   // Adapté las función para usar los componentes del vector.
    point(this.position.x, this.position.y);
  }

  step() {
    const choice = floor(random(4));
    let step = createVector(0, 0);

    if (choice == 0) {
      step.x = 1;
    } else if (choice == 1) {
      step.x = -1;
    } else if (choice == 2) {
      step.y = 1;
    } else {
      step.y = -1;
    }

    // Sumé el paso a la posición con .add()
    this.position.add(step);
  }
}
```
### Actividad 03
 Experimenta.
- ¿Qué resultado esperas obtener en el programa anterior?
 > Espero que se dibuje un fondo cuadrado casi blanco y que se cree un vector con la posición (6, 9), que se va a mostrar en la consola. Luego, esa posición se va a modificar a (20, 30)      usando la función playingVector, y esa nueva posición también se va a imprimir en consola. Por último, como se usa noLoop(), el mensaje "Only once" se mostrará una sola vez en la   consola.
  
- ¿Qué resultado obtuviste?
> Mi respuesta fue básicamente lo que dije, fondo cuadrado casi blanco y que se cree un vector con la posición (6, 9), que se va a mostrar en la consola. Luego, esa posición se va a modificar a (20, 30) usando la función playingVector, y esa nueva posición también se va a imprimir en consola. Solo que en consola se mostraron las coordenadas en tres dimensiones, o sea, apareció como (6, 9, 0) y luego como (20, 30, 0).
  
- Recuerda los conceptos de paso por valor y paso por referencia en programación. Muestra ejemplos de este concepto en javascript.
#### **Paso por valor**
  
> Cuando pasas tipos primitivos como number, string, boolean, null, undefined, symbol, bigint, se pasa una copia del valor. Cambiar esa copia no afecta al valor original.

Ejemplo:
   ```javascript
function cambiarValor(x) {
  x = x + 1;
  console.log("Dentro de la función:", x); // 6
}

let numero = 5;
cambiarValor(numero);
console.log("Fuera de la función:", numero); // 5
  ```
 *Aunque se modifica x dentro de la función, el valor original (numero) no cambia.*
 
 #### Paso por referencia
> Cuando pasas objetos o arrays (incluidos los vectores de p5.js), se pasa una referencia a la ubicación en memoria, no una copia del contenido. Cambiar algo dentro del objeto afecta al original.

Ejemplo:
```javascript
function modificarVector(v) {
  v.x = 10;
  v.y = 20;
}

let posicion = createVector(5, 5);
modificarVector(posicion);
console.log(posicion.toString()); // Vector with components (10, 20, 0)
```
*Como posicion es un objeto, la función puede cambiar directamente sus propiedades.*
- ¿Qué tipo de paso se está realizando en el código?
  > En ese código se está realizando un paso por referencia.
  > Porque la posición es un objeto y cuando se pasa un objeto a una función, no se copia el objeto, sino que se pasa una referencia a su ubicación en memoria. Es decir, ambas variables (position y v) apuntan al mismo vector.

- ¿Qué aprendiste?
  > Aprendí que cuando paso un objeto  a una función, en realidad no se copia, sino que se pasa la referencia, o sea, que si cambio el objeto dentro de la función, también se cambia por fuera. Eso se llama paso por referencia. En cambio, si fuera un número o un string, ahí sí se copia el valor y no se modifica el original (paso por valor). Esto me ayudó a entender por qué el vector position sí cambió después de usar la función playingVector() en el código de ejemplo.


### Actividad 04

- ¿Para qué sirve el método mag()? Nota que hay otro método llamado magSq(). ¿Cuál es la diferencia entre ambos? ¿Cuál es más eficiente?
  > - El método mag() sirve para obtener la magnitud (o longitud) de un vector. Es equivalente a calcular la distancia desde el origen (0, 0) hasta el punto definido por el vector usando el Teorema de Pitágoras, Con la formula Raiz(x^2 + y^2 + z^2).
  > -  El método magSq() devuelve la magnitud al cuadrado del vector, es decir, evita calcular la raíz cuadrada:
  > - Desde este punto de vista el magSq() es más eficiente que mag() porque no calcula la raíz cuadrada, lo que ahorra recursos en operaciones repetitivas o cuando solo necesitas comparar vectores.
  
- ¿Para qué sirve el método normalize()?
  > Sirve para conviertir la magnitud de un vector en uno con la misma dirección, es decir, lo transforma en un vector unitario.
     Esto para mantener la dirección del vector original, pero sin importar su magnitud. Es útil, cuando por ejemplo solo te interesa hacia dónde apunta un objeto, pero quieres controlar tú la velocidad o magnitud            aparte.
- Te encuentras con un periodista en la calle y te pregunta ¿Para qué sirve el método dot()? ¿Qué le responderías en un frase?
  > El método dot() calcula el producto punto entre dos vectores. Es como medir cuánta 'sombra' de un vector cae sobre el otro. Es muy útil para saber cómo se relacionan dos direcciones en el espacio.
  
- El método dot() tiene una versión estática y una de instancia. ¿Cuál es la diferencia entre ambas?
  > La diferencia es que la versión de instancia v1.dot(v2) se llama desde un vector y usa otro como argumento, mientras que la versión estática p5.Vector.dot(v1, v2) se llama desde la clase y recibe ambos vectores   como parámetros.
  > Por lo tanto  la versión normal se usa cuando ya tienes un vector y quieres compararlo con otro.
y la versión estática (p5.Vector.dot(v1, v2)) se usa cuando quieres comparar dos vectores desde fuera, sin que uno “llame” al otro.

- Ahora el mismo periodista curioso de antes te pregunta si le puedes dar una intuición geométrica acerca del producto cruz. Entonces te pregunta ¿Cuál es la interpretación geométrica del producto cruz de dos vectores? Tu respuesta debe incluir qué pasa con la orientación y la magnitud del vector resultante.
  > El producto cruz entre dos vectores se puede imaginar como un nuevo vector que es perpendicular a los dos vectores originales. Si los dos vectores están en el plano, el producto cruz “apunta” hacia afuera del plano, como si saliera hacia ti o se alejara de ti, dependiendo del orden de los vectores. En cuanto a la magnitud, el producto cruz mide el área del paralelogramo formado por los dos vectores. Es decir, cuánto "espacio" en el plano abarcan juntos. Entonces, geométricamente, la dirección del vector cruzado indica una orientación perpendicular (hacia arriba o hacia abajo del plano). Y la magnitud te dice cuán separados o inclinados están los vectores entre sí. 
- ¿Para que te puede servir el método dist()?
  > El método dist() sirve para calcular la distancia entre dos puntos representados por sus coordenadas o vectores. Es decir, te dice qué tan lejos está un punto del otro.
  
- ¿Para qué sirven los métodos normalize() y limit()?
  > - normalize(): Sirve para conviertir un vector en un vector unitario, es decir, con la misma dirección pero con magnitud 1.
Es muy util cuando te interesa solo la dirección del vector, no su tamaño.

  > - limit(): limita la magnitud del vector a un valor máximo.
Es útil para evitar que algo se mueva demasiado rápido o con una fuerza excesiva en simulaciones o animaciones.




