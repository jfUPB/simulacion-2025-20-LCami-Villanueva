# Evidencias de la unidad 6
## 💡 Set: 
### Actibidad 1: ✏️
  **1.** Captura en tu bitácora dos imágenes de Tyler Hobbs que te llamen la atención y explica por qué.
> <img width="885" height="586" alt="image" src="https://github.com/user-attachments/assets/392df303-8895-4815-ba2a-df82b329fab7" />
>
> Lo que más me llama la atención de esta obra es cómo las formas circulares, dispuestas en un flujo continuo, evocan la sensación de un tejido artesanal. Las bolitas parecen esferas que, al entrelazarse, recuerdan un bordado o un tapiz natural. Esa cualidad orgánica transmite calma y armonía, como si la obra capturara un proceso lento, paciente y hecho a mano, acercando lo digital a lo humano y lo artesanal.




> <img width="907" height="683" alt="image" src="https://github.com/user-attachments/assets/84e5c3cd-4e53-4cb4-a450-a2f0953389e6" />
>
> Esta obra me atrae la intensidad del movimiento que generan las líneas, como si cada trazo escondiera una historia secreta. El caos aparente me hace pensar en relatos oscuros, en atmósferas densas similares a las que describe Edgar Allan Poe. Las curvas, superpuestas y tensas, transmiten una sensación de misterio e inquietud.


 2.¿Qué te inspira de su trabajo?
 > Lo que más me inspira del trabajo de Tyler Hobbs es su capacidad para convertir un recurso técnico como los flow fields en un lenguaje artístico lleno de posibilidades expresivas. Me motiva cómo explora las variaciones, los límites y las distorsiones de estas estructuras matemáticas hasta transformarlas en obras que parecen orgánicas, casi vivas. En su proceso veo una invitación a no conformarse con la primera solución que da el algoritmo, sino a experimentar, pulir y buscar nuevas formas de narrar visualmente con el código. Eso me impulsa a pensar la programación no solo como una herramienta funcional, sino como un medio creativo con el que se pueden tejer historias, atmósferas y sensaciones.

## 🔎 Seek:
### Actividad 02 🧐
1. ¿Qué es una fuerza de dirección (steering force)?
> Una fuerza de dirección (steering force) no es una fuerza en el sentido físico tradicional (como la gravedad o la fricción), sino una construcción algorítmica que calcula un vector para "guiar" a un agente autónomo hacia un objetivo o comportamiento deseado. Es, en   esencia, la intención de movimiento del agente convertida en un vector.
>
> El principio fundamental se basa en una fórmula simple pero poderosa:
> 
>  **Fuerza de Dirección = Velocidad Deseada - Velocidad Actual**
> 
> Desglosando esto:
> - Velocidad Deseada: Es un vector que representa la forma ideal en que el agente querría moverse para cumplir su objetivo. Por ejemplo, si el objetivo es "ir hacia el mouse", la velocidad deseada sería un vector apuntando desde el agente hacia el mouse, con una magnitud    > igual a la máxima velocidad posible del agente.
> - **Velocidad Actual:** Es el vector de velocidad que el agente ya posee en un momento dado.
> - **Fuerza de Dirección:** El resultado de la resta es un vector de "corrección". Este vector, cuando se aplica como una fuerza al sistema de movimiento del agente (el Motion 101), ajusta su aceleración para que su velocidad actual se alinee gradualmente con la velocidad   > deseada. No es un cambio instantáneo, sino una guía suave, lo que produce un movimiento mucho más orgánico y realista.
>   
> En resumen, una steering force es el motor de la toma de decisiones de un agente. No describe cómo el mundo físico empuja al agente, sino cómo el agente decide empujarse a sí mismo para lograr un propósito.

3. ¿Qué diferencia tiene este tipo de fuerza con las que ya hemos estudiado en el contexto de la simulación de agentes?
   >
   > Esta es la distinción más importante. La diferencia radica en la naturaleza de la fuerza: reactiva vs. proactiva.
   > |Característica | Fuerzas Físicas | Fuerzas de Dirección |
   > |-----------|-----------|-----------|
   > | Naturaleza | Reactiva. Describen cómo el entorno (gravedad, viento, fricción) actúa sobre el agente. El agente es un objeto pasivo que sufre estas fuerzas.   | Proactiva. Describen cómo el agente decide actuar para lograr un objetivo. El agente es una entidad activa que genera sus propias fuerzas para navegar.   |
   > | Origen   | Externo al agente (ej. la masa de un planeta, la viscosidad de un fluido).  | Interno al agente. Nace de un algoritmo de decisión basado en sus metas (ej. "quiero llegar a ese punto").   |
   > | Objetivo   | Simular las leyes de la física de manera realista.   | Simular comportamiento y autonomía. El objetivo no es la precisión física, sino la credibilidad del movimiento y la intención.   |
   > | Ejemplo Práctico   |Un asteroide siendo atraído por la gravedad de un planeta. El asteroide no "quiere" ir hacia el planeta; simplemente es arrastrado por una fuerza externa.   | Un pez en un cardumen que "quiere" mantenerse cerca de sus compañeros. El pez calcula activamente una fuerza de cohesión para no quedarse atrás.   |
   >
   >En conclusión, las fuerzas de la Unidad 3 son las leyes del mundo que afectan a todo por igual. Las fuerzas de dirección son las decisiones y deseos de los individuos que viven en ese mundo. Al combinar ambas, se pueden crear simulaciones increíblemente ricas y realistas.


5. ¿Qué relación tiene la steering force con Craig Reynolds y su trabajo en simulación de comportamiento animal?
   > **Craig Reynolds** es el padre del concepto de fuerzas de dirección. La relación es directa y fundamental; él acuñó el término y desarrolló el modelo que seguimos utilizando hoy.
   > En 1986, mientras trabajaba en la industria de la animación por computadora, Reynolds se enfrentó al problema de cómo animar de forma realista grupos de animales (como bandadas de pájaros o cardúmenes de peces) sin tener que animar cada individuo a mano. Su investigació     > culminó en un artículo revolucionario llamado "Flocks, Herds, and Schools: A Distributed Behavioral Model".
   >
   > En este trabajo, presentó su famoso y revolucionario modelo "Boids" (abreviatura de "bird-oid objects" u objetos parecidos a pájaros). La genialidad de su propuesta radicó en demostrar que un comportamiento de grupo increíblemente complejo y realista, como una bandada de pájaros en vuelo, podía emerger no de una inteligencia centralizada o un líder, sino de la interacción de agentes individuales siguiendo tres reglas muy simples y locales:
   >
   > - Separación: Cada agente intenta mantener una pequeña distancia con los otros agentes cercanos para evitar colisiones. Es una fuerza repulsiva de corto alcance que previene el amontonamiento.
   > - Alineación: Cada agente intenta moverse en la misma dirección promedio que sus vecinos. Esta regla hace que el grupo se mueva como un todo coherente, copiando la trayectoria general de los que lo rodean.
   > - Cohesión: Cada agente intenta moverse hacia la posición promedio de sus vecinos, es decir, mantenerse cerca del centro del grupo. Es una fuerza de atracción que evita que la bandada se disperse
   >
   > Ningún "boid" conoce el estado global de la bandada; solo percibe a sus vecinos inmediatos. Sin embargo, la suma de estas millones de decisiones locales y descentralizadas da como resultado el fenómeno emergente de un movimiento de bandada fluido y orgánico.
   >
   > Para implementar estas reglas, Reynolds inventó el mecanismo de las fuerzas de dirección. Cada una de estas reglas (y otras que desarrolló después como seek, flee, path following, etc.) era un "comportamiento de dirección" que calculaba un vector de fuerza. Al combinar y ponderar estas fuerzas, cada "boid" podía navegar su entorno y relacionarse con sus compañeros de una manera autónoma y creíble.
   > Su trabajo no solo sentó las bases para la simulación de vida artificial, sino que se convirtió en una técnica estándar en la industria de los **videojuegos**,

   ### Actividad 03 ✏️
   1. Explica brevemente la estructura de datos usada para el campo de flujo y cómo se generan sus vectores.
      > La forma en que se implementa el campo de flujo es usando un array de dos dimensiones ```this.field ```, que básicamente funciona como una cuadrícula que cubre todo el lienzo. El tamaño de esta cuadrícula depende de la resolución, lo que define cuántas columnas
      > ```cols```  y filas ```rows``` se crean. En cada celda se guarda un objeto p5.Vector, que indica la dirección de la fuerza en ese punto. Para generar estos vectores se recorre la cuadrícula con un bucle anidado, y en cada paso se  calcula un valor de Ruido Perlin            > ```noise(xoff, yoff))```, que se convierte en un ángulo. Con ese ángulo se crea un vector unitario ```p5.Vector.fromAngle(angle)``` y se asigna a la celda. De esta manera, se termina  con una estructura llena de direcciones suaves y continuas, que hacen que el campo         > tenga un comportamiento orgánico, parecido a corrientes de viento o agua.
   2. Describe con tus palabras cómo un agente utiliza el campo para calcular su fuerza de dirección.
      > El agente calcula su fuerza de dirección dentro del método ```follow(flow)``` mediante un proceso de tres pasos. Primero, determina el vector de dirección ideal obteniéndolo del campo de flujo con ```flow.lookup(this.position)```. Despues, este vector se escala a la         > velocidad máxima del agente con ```desired.mult(this.maxspeed)``` para establecer una velocidad deseada ```desired```. Finalmente, se aplica la fórmula de Reynolds calculando la diferencia entre la velocidad deseada y la velocidad actual ```let steer = p5.Vector.sub(desired, this.velocity)```. El vector que resulta ```steer```es la fuerza de dirección, la cual se limita a una fuerza máxima ```steer.limit(this.maxforce)``` antes de ser aplicada a la aceleración, guiando así su movimiento de forma gradual y orgánica.
   3. Lista los parámetros clave identificados (resolución, maxspeed, maxforce).
      > - **maxspeed y maxforce (Límites del Agente):** Son los parámetros más cruciales porque definen la personalidad física de cada vehículo. maxspeed controla el ritmo general de la simulación, mientras que maxforce determina la agilidad de los agentes, haciendo que su movimiento se sienta suave y orgánico o, por el contrario, brusco y robótico.
      >
      > - Resolution: Este parámetro define la granularidad del campo de flujo. Un valor bajo crea un mapa de corrientes muy detallado y complejo, mientras que un valor alto genera flujos más amplios y suaves. Cambiar este número altera fundamentalmente el entorno que los agentes deben navegar.
      >
      > - Incremento del Ruido (El "Zoom" del Campo): Los valores 0.1 usados para incrementar xoff y yoff al generar el Ruido Perlin son clave para la estética del movimiento. Controlan la escala de las corrientes; valores pequeños crean flujos suaves como un río, y valores grandes generan turbulencias caóticas.
      >
      > - Númeero de vehiculos (Complejidad del Sistema): Determina la densidad y la riqueza del comportamiento emergente. Una población mayor crea patrones de grupo más complejos y visualmente impactantes, pero también es el factor que más afecta el rendimiento.
      
   6. Describe la modificación que realizaste al código y explica detalladamente el efecto que tuvo en el movimiento y comportamiento colectivo de los agentes. Incluye una captura de pantalla o GIF si ilustra bien el cambio. Muestra el fragmento de código modificado.
      > #### Experimento #1: Alterar maxspeed y maxforce
      > - Descripción de la Modificación
      >   
      >    Para este primer experimento, la modificación se centró en los dos parámetros: maxspeed (su velocidad máxima) y maxforce (su capacidad de giro). El cambio se realizó directamente en la función setup(), dentro del bucle for que inicializa la població de
      >   Vehículos. Se alteraron los rangos de los valores aleatorios asignados a estos dos parámetros al momento de crear cada nuevo objeto Vehicle, haciendo el valor de maxforce muy bajo.
      >   
      > - Efecto en el Movimiento y Comportamiento Colectivo
      >   
      >   Alterar estos parámetros tuvo un efecto inmediato en el comportamiento emergente del grupo. Con un maxforce bajo, los agentes exhibieron una gran inercia; al igual que un barco pesado, viendose mucho mas lento al empezar la simulación, sus giros eran amplios
      >   suaves, forzándolos a ignorar pequeñas turbulencias del campo de flujo. Colectivamente, esto resultó en un movimiento increíblemente fluido y orgánico.
      >
      > - Gif
      >     
      >     ![Video1](https://github.com/user-attachments/assets/463b8390-867b-4a7f-8318-469dc4a13bec)
      >
      > - Código Modificado
      >  ``` JS
      >     function setup() {
      >      let text = createP(
      >       "Hit space bar to toggle debugging lines.<br>Click the mouse to generate a new flow field."
      >       );
      >
      >      createCanvas(640, 240);
      >      flowfield = new FlowField(20);
      >      for (let i = 0; i < 120; i++) {
      >     vehicles.push(
      >     new Vehicle(random(width), random(height), random(1, 2), random(0.001, 0.005)) // Random modificado a valores mucho mas pequeños.
      >     );
      >    }
      >   }        
      >   ```
      >
      >   #### Experimento #2: Modificar la Resolución del Campo de Flujo (Fina)
      > - Descripción de la Modificación
      >   
      >    En este segundo experimento, el cambio se enfocó en el parámetro resolution del objeto FlowField. La modificación se realizó en la función setup(), en la línea donde se instancia el campo de flujo. El valor de la resolución se redujo  ( de 20 a 5), lo que tiene el       >    efecto de crear una cuadrícula mucho más densa y detallada, con un número significativamente mayor de vectores de dirección en el mismo espacio del lienzo.
      >   
      > - Efecto en el Movimiento y Comportamiento Colectivo
      >   
      >   Esta alteración transformó el comportamiento del sistema. Con una resolución tan fina, cada agente se encuentra con una gran variedad de vectores de dirección en distancias muy cortas. En lugar de seguir grandes arcos, sus caminos se llenan de pequeñas desviaciones       > y giros bruscos al intentar seguir cada micro-corriente del campo. Colectivamente, las grandes formaciones fluidas y orgánicas desaparecieron por completo. El grupo ya no se comporta como un solo río, sino como un enjambre caótico y texturizado, donde la                    > individualidad de cada agente es mucho más perceptible. El efecto general es de una mayor energía y complejidad visual, como si los agentes estuvieran navegando por un terreno invisible increíblemente turbulento.
      >
      > - Imagen
      >  <img width="794" height="298" alt="image" src="https://github.com/user-attachments/assets/bcdf5591-784a-4370-8500-bc71d119b99a" />
      >
      > 
      > - Código Modificado
      >   
      >  ``` JS
      >   function setup() {
      > let text = createP(
      > "Hit space bar to toggle debugging lines.<br>Click the mouse to generate a new flow field."
      > );
      > createCanvas(640, 240);
      > flowfield = new FlowField(5); //Modifique la resolución por una mucho mas fina.
      > for (let i = 0; i < 120; i++) {
      > vehicles.push(
      > new Vehicle(random(width), random(height), random(1, 2), random(0.1, 0.5))
      > );
      > }
      > ```

  





