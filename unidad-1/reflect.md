# Unidad 1

## 🤔 Fase: Reflect

### Actividad 9:

**Parte 1: recuperación de conocimiento (Retrieval Practice)**

- Describe la diferencia fundamental entre la aleatoriedad generada por random() y la apariencia de aleatoriedad del Ruido Perlin (noise()). ¿En qué tipo de situación usarías cada una?

  
  La principal diferencvia es que le random genera valores en cuaquier punto del espacio, generalmente dispersos, sin orden mientras el perlin nose aunque lo hace aleatoreo, lso valores no son tan arbitarios por los que se siente mas organico y natural, los random teineden a tener un orden y mas sentido.
  
  
- Explica con tus palabras qué es una distribución de probabilidad. ¿Qué diferencia visual produce una caminata aleatoria con una distribución uniforme versus una con una distribución normal?

  
  Una distriución de probablidad es que tanta probabilidad existe de que suceda algo. Visualmente la diferencia es que la uniforme al hacer que todos los valores tengan la misma probabilidad lo que hace que el espacio se rellene de manera uniforme, es decir en todos los puntos, mientras que en una distribución no uniforme los puntos tienden a un valor por lo que se reelna mas rápido hacia valores cercanos a ese valor, si lo hacemos con opacidad esto se traduciría en que los espacios cercanos al valor s 3even más oscuros. 



- ¿Cuál es el papel de la aleatoriedad en el arte generativo? Menciona al menos dos funciones distintas que cumple

  
  La aleatoriedad permite que el arte generativo no sea repetitivo, ya que con esto se logra que sea impredecible y único.


  
- Piensa en tu obra final (Actividad 08). Describe uno de los conceptos de aleatoriedad que usaste y explica por qué fue una elección adecuada para lograr el efecto que buscabas.
  
  En mi obra final use el randon Gausiano para hacer que los colores al dar click cambiaran entre colores primaverakes (Cercanos al verde) y colores otoñales (Cercanos al naranja), siento que fue la elección adecuada porque me permitio poder hacer que las hojas represntando cada estcaión no fueran todas exactamente del mismo color, pero que al tiempo el estar sesgadas por la media y la desviación los colores fueran cercanos y repr4esentaran la estación que deseaba.
  
- ¿Qué es un “paseo” o “caminata” (walk) en el contexto de la simulación? ¿Qué característica particular tiene una caminata de tipo “Lévy flight”?

  En este contexto una caminata es un patrón que se genera con numeros aletaoreos que detenterninan la dirección del movimiento. Una caminata de Lévy flight es aquella que teine una probabilidad de dar pasos mas grandes, es decir la acaminata por lo general se concentra en un espacio, con valores cercanos, el caso de Lévy flight en momentos determinados puede hacer un salto, que es un paso grande que permite estar en un lugar alejado de donde empezó la caminata.
  
**Parte 2: reflexión sobre tu proceso (Metacognición)**
- ¿Cuál fue el concepto más abstracto o difícil de “visualizar” para ti en esta unidad? ¿Qué hiciste para finalmente comprenderlo?

  
   El concepto mas dificil de visualizar para mí fue el de perlin noise, ya que realmenete no lograba ver como se generaba esa distribución, al principio pense que iba más por el lado de generar uan estela en un movimiento, pero aunque si puede generar este efecto no se reduce a eso, para comprenderlo le pedí a chat mas ejemplos de en donde se aplica, como y por que entendiendo al fin que es mas el hecho de suavizar los valores paraq ue se sineta mas organico y natural.

  
- Describe un momento durante el desarrollo de tu obra final (Actividad 08) en el que un “error” o un resultado inesperado te llevó a una idea creativa interesante.
  
  Durante mi desarrollo tuve un error que era que de la nada se generaban una cantidad mayor de hojas, esto me llevó a poner la función de que al oprimir la g se crearan alaeatoremanete mas hojas, lo que me hizo pensar en que esta función era como abonar la tierra del arbol haciendo que fuera mas grande.
  
- Al combinar diferentes técnicas de aleatoriedad, ¿Cuál fue el mayor desafío? ¿La interacción entre los sistemas, el control de los parámetros, el rendimiento?
  
  Para mí el mayor desafío fue el integrar todo en un solo, a veces el hecho de quere inetgrar una nueva tecnica de aleatoriedad me dañaba como había concebido la anterior y la logica del código.
  
- Si tuvieras que empezar la Actividad 08 de nuevo, ¿Qué harías de manera diferente basándote en lo que sabes ahora?
  
  Creo que hubiera organizado todas mis ideas mejor desde el principio, para poder integrar todo desde el momento uno, ya que teniendo una concepción general de todo lo que quería no hubiera tenido el problema de dañar pasos anteriores por integrar otros.

### Actividad 10

- Encuentra un compañero de trabajo.

  Juan Sebastian Mieles

- Intercambien las URLs de sus bitácoras de aprendizaje.

  
  https://github.com/jfUPB/simulacion-2025-20-Juan1022/blob/unidad1/apply/unidad-1/apply.md
  

  
- Dirígete a la entrada de la Actividad 08: creación de obra generativa de tu compañero. Lee su concepto, interactúa con su sketch y analiza su código.
- [x] Listo

- Basándote en la rúbrica para la actividad 08 evalúa el trabajo del compañero y escribe un comentario de retroalimentación constructiva. Esto lo harás en tu bitácora de aprendizaje.
    - [x] El sketch es una obra generativa, interactiva en tiempo real
    - [x] Combina de manera funcional y coherente al menos tres conceptos de la unidad.
    - [x] Explicación clara del concepto de la obra. (En la bitacora no era tan claro el concepto, pero su explicación fe prcisa y convicente.
    - [x] El código completo
    - [x] Enlace funcional al sketch
    - [x] Captura de pantalla.
       
  **Feedback**: Su obra me pareció muy interesante, me gustó con exploró el concepto de el oceano, el hecho de que las algas y burbujas se muevan de manera organica gracias al perlin noise y que sean tan inesperado la cantidad de peces por atrapar le da un aura de  misterio que puede hacer que se sineta divertido atraparlo. En genral me parecio que aplico todos los conceptos de manera coherente y acertiva.

- Conversa con tu compañero sobre su obra y tu feedback. Escucha sus reflexiones y comparte tus propias ideas.
- [x] Listooo

 ### Actividad 10

- Continuar: ¿Qué actividad, ejemplo o explicación de esta unidad te resultó más reveladora o útil para tu aprendizaje? ¿Qué deberíamos mantener sí o sí?

  Me realemente me gustan los que den ejemplos cotidianos para enseñar, de estos vi varios en la pagina guía y me parecieron, muy interesantes y me ayudaron mucho a entender los conceptos, de igual forma me pareció interesante los ejemplos de obra generativa que el profesor dio al principio ya que me motivaron y ayudaron adarme ideas para mi obra.
- Dejar de hacer: ¿Hubo alguna actividad o concepto que te pareció redundante, confuso o menos útil? ¿Hay algo que eliminarías o cambiarías por completo?

  La verdad no, para mí todo dentro de la unidad todo fue claro y teníamos buenos recursos para comprender, aunque si afine algunos conceptos con la ayuda de chat en general los recuros eran muy bueneo.

  
- Empezar a hacer: ¿Qué te faltó en esta unidad? ¿Quizás más ejemplos de artistas, más desafíos técnicos, más teoría? ¿Qué idea tienes para hacerla mejor?

  Me hubiera gustado mas ejemplos de artistas que explicaran su obra, o tal vez ejemplos de aplicaciones mas concizas en mi área, aunque entiendo que esto es complicado ya que en el curso hay varias lineas pero se podría plantear una actividad extra de desafío tecnico dee aplicación en el area de estudio de cada uno.

  
- Balance Teoría-Práctica: ¿Cómo sentiste el equilibrio entre analizar los ejemplos del texto guía y ponerte a programar tus propios sketches? Explica tu respuesta.

  
  En lo personal me pareció muy adecuado, ya que me pemitió entender el concepto, practicarlo y comprenderlo a profundidad en la practica y luego aplicar todos los conceptos juntos, por lo que creo que esto aseguró un parendizaje más integral.

  
- Comentario Adicional: ¿Hay algo más que quieras compartir sobre tu experiencia en esta unidad?

  En general siento que aprendí bastante en la unidad, y me gustó la metología
