# Unidad 3


## 🤔 Fase: Reflect

### Actividad 11
**Parte 1: recuperación de conocimiento (Retrieval Practice)**

- Escribe la ecuación vectorial de la segunda ley de Newton y explica cada uno de sus componentes.
  > 
- ¿Por qué es necesario multiplicar la aceleración por cero en cada frame del método update()?.
  > Se multiplican para reiniciarlas en cada frame, ya que si no se reinician las aceleraciones se suman y se acelerarría infinitamnete, y la idea es que la aceleración sea solo la sumatoria de las fuerzas en cada frame.
- Explica la diferencia entre paso por valor y paso por referencia cuando aplicamos fuerzas a un objeto.
  > La diferencia es que el paso por valor crea una copia del numero original y no afecta la variable global, mientras que por referencia se pasa ese valor y se cambia, en el caso de fuerzas el paso se hace por valor creando una copia, para que nos e afecte el valor original y el valor sea ese solo en ese momento y el valor global siga siendo el mismo.
- ¿Cuál es la diferencia conceptual entre modelar fuerzas (como fricción, gravedad) y simplemente definir algoritmos de aceleración?
  > Que el algoritmo de aceleración simplemete es un vetos que se agrega a la velocidad, mientras que cuando se modela una fuerza estas se definen por formulas, que van de la mano con como funciona el munod real teniendo en cuenta factores como la gravedad y ahí usas las formulas correspondiuente a cada fuerza.
**Parte 2: reflexión sobre tu proceso (Metacognición)**
- ¿Qué fue lo más desafiante en la Actividad 10 (problema de los n-cuerpos)? ¿El concepto creativo, la implementación de las fuerzas o la integración de la interactividad?wr
  > Que cuando tuve una idea clara de que hacer realmente no sabía como empezar, no por los algoritmos ya realizados en la unidad, si no porque quría hacer la obra de calder y no podía imaginar como programar esa forma, en eso tuve que pedirle ayuda a chat, y apartir de ahí y con los algoritmos que ya conocia poder realizar el restode la obra.
- ¿Las fuerzas que modelaste produjeron el comportamiento que esperabas? Describe un momento “sorpresa” (esperado o inesperado) durante el desarrollo.
  > Creo que en general sí, solo que tuve que probar con varios valores para poder obtener el resultado que deseaba, ya que al principio era muy debil, y luego al subirlo ya era mucho entonces tuve que hacer varias pruebas.
- ¿Cómo ha cambiado tu forma de pensar sobre la “física” en el arte generativo después de esta unidad?
  > La verdad no había pensado en palicar fuerzas del mundo real al arte generativo, pensaba que pues con randoms y vectores de velocidad y movimeinto era suficiente, pero pues en realidad, creo que es muy interesante darle ese aire del mundo real porque eso hace que sxes mucho mas femiliar con lo que conocemos y por lo tanto lo sintamos mas cercano.
- Si tuvieras una semana más, ¿Qué otras fuerzas te gustaría modelar o cómo mejorarías tu simulación del problema de los n-cuerpos?.
- Creo que mejoraría el movimiento del viento porque a pesar de ser un perlin noise en algunos momentos lo siento muy brusco hacía la derecha, me gustraíá que fuera mas suave y que moviera los objetos en varias direcciones. 


