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
 ### Actividad 04 ✏
  1. Explica con tus palabras el objetivo y la lógica general de cálculo de cada una de las tres reglas de Flocking (Separación, Alineación, Cohesión).
     > - Separación: El objetivo de esta regla es evitar colisiones. El método ```separate()``` itera sobre todos los demás boids y, para aquellos que están dentro de un radio de ```desiredSeparation```, calcula un vector de repulsión. Este vector apunta en dirección opuesta al vecino y su magnitud es inversamente proporcional a la distancia, generando un empuje más fuerte cuanto más
     >   cerca esté. Finalmente, se promedian todos estos vectores de repulsión para obtener una única fuerza de dirección ```(steer)``` que aleja al agente del amontonamiento.
     > -  Alineación: Esta regla busca que el grupo se mueva de forma unificada. El método ```align()``` identifica a todos los boids dentro de un ```neighborDistance``` y calcula el vector de velocidad promedio de ese grupo local. Este vector promedio se convierte en la velocidad deseada del agente, y se utiliza la fórmula de Reynolds (Steer = Desired - Velocity) para calcular la
     >    fuerza dirección que ajusta suavemente la trayectoria del agente hasta que se alinee con la de sus compañeros.
     > - Cohesión: El propósito de esta regla es mantener la bandada unida, evitando que los agentes se dispersen. De forma similar a la alineación, el método ```cohere()``` encuentra el centro geométrico de sus vecinos cercanos promediando sus vectores de posición. Este punto central se convierte en el target para un comportamiento de ```seek()```, el cual calcula la fuerza de
     >    dirección necesaria para guiar al agente hacia el centro del grupo local.
  2. Lista los parámetros clave identificados (radio de percepción, pesos de las reglas, maxspeed, maxforce).
     > - maxspeed (Velocidad Máxima): Limita la velocidad máxima a la que un agente puede moverse. Un valor alto crea una bandada más rápida y energética; uno
     >   bajo, una más lenta y pausada.
     > - maxforce (Fuerza Máxima): Controla la agilidad o capacidad de giro de un agente. Un valor bajo genera movimientos suaves y curvas amplias, mientras que
     >   un valor alto permite giros bruscos y reacciones rápidas.
     > - Radios de Percepción (desiredSeparation y neighborDistance): Definen el "espacio personal" y la "conciencia social" de cada agente.
     > - desiredSeparation (en separate): Es un radio muy corto que activa la fuerza de repulsión para evitar colisiones.
     > - neighborDistance (en align y cohere): Es un radio más grande que define qué agentes son considerados "vecinos" para calcular el movimiento y la cohesión
     >   del grupo.
     > - Pesos de las Reglas (los multiplicadores en flock()): Estos valores (1.5 para separación, 1.0 para alineación y cohesión) son cruciales, ya que
     >   establecen la jerarquía de prioridades de un agente. Al darle un peso mayor a la separación, nos aseguramos de que evitar una colisión sea siempre más
     >   importante que intentar alinearse con el grupo.
  3. Describe la modificación que realizaste al código y explica detalladamente el efecto que tuvo en el comportamiento colectivo del enjambre (¿Se dispersan? ¿Forman grupos compactos? ¿se mueven caóticamente?). Incluye una captura de pantalla o GIF si ilustra bien el cambio. Muestra el fragmento de código modificado.
     >  > #### Experimento #3: Cambiar el Peso de las Reglas
      > - Descripción de la Modificación
      >   
      >    Para este experimento, la modificación consistió en anular por completo la influencia de la regla de Alineación. Esto se logró dentro del método flock() de la clase Boid, estableciendo el multiplicador del vector de fuerza de alineación (ali) a 0.0. Al hacer esto, se elimina por completo el deseo de los agentes de moverse en la misma dirección que sus vecinos, aislando únicamente las fuerzas de Separación (evitar choques) y Cohesión (mantenerse cerca del grupo) para observar su interacción directa.
      >    
      > - Efecto en el Comportamiento Colectivo del ejambre
      >   
      >   El efecto de anular la alineación es inmediato y drástico. La bandada no se dispersa, ya que la fuerza de Cohesión sigue atrayendo a los agentes hacia el centro del grupo, manteniéndolos en un grupo compacto. Sin embargo, sin la regla de Alineación que les proporcione una dirección común, el movimiento se vuelve completamente caótico. Cada agente intenta acercarse al grupo (Cohesión) mientras evita a sus vecinos inmediatos (Separación), pero sin un rumbo compartido, sus trayectorias individuales se vuelven erráticas y conflictivas. El resultado es un "hervidero", una masa agitada que permanece agrupada pero que hierve y se retuerce sobre sí misma sin desplazarse de manera coherente, muy similar a un enjambre de abejas.
      >
      > - Gif
      >    
      > ![Recording-2025-09-29-010511](https://github.com/user-attachments/assets/23e7de5e-b6cc-43d1-a7f4-71b35cd6ecff)
      >
      >- Código Modificado
      >   
      >  ``` JS
      >   flock(boids) {
      > let sep = this.separate(boids); // Separation
      > let ali = this.align(boids); // Alignment
      > let coh = this.cohere(boids); // Cohesion
      > sep.mult(1.5);
      >  ali.mult(0.0); // Cambie este valor a 0 
      >  coh.mult(1.0);
      > this.applyForce(sep);
      > this.applyForce(ali);
      > this.applyForce(coh);
      >  }
      >```
### Actividad 05
   1. Documenta todo el proceso de diseño y creación en tu bitácora, incluyendo bocetos y decisiones de diseño.
   > **ETAPA DE DISEÑO** 🎨✨
   >
   > Luego de ver los ejemplos del libro y una de las obras de Tyler Hobbs, en específico Mirror Removal #5, 2019, me llamó mucho la atención que estos campos de flujo pueden verse como huellas dactilares. Este pensamiento se reafirmó cuando fui al MAMM, donde vi una exposición en la que había una pared con muchas huellas dactilares y, dentro de ellas, imágenes de personas. Aunque esta exposición hablaba de una realidad triste, ya que representaba a víctimas de la violencia, decidí que quería un concepto parecido, pero usando las huellas como una muestra de identidad propia, pues cada persona es única como su huella. No quería representar un tema triste, por lo que busqué una canción alegre que mostrara cómo eso que nos hace únicos convierte una experiencia divertida en algo distinto para cada uno, pero en un recuerdo inolvidable para todos.🔥
   >
   > 💡 **Lluvia de ideas** 
   >  * Huellas dactilares representando que cada experinecia es unica y diferente pero igualmente divertida
   >  * Canción escogida Samba do Brasil, (Es muy alegre y podríá represnetar un carnaval)
   >  * Carnaval en calles
   >  * Bailarines bailando al ritmo de la musica
   >  * Los bailarines forman la huella
   >  * Puedes modificar la huella para que cada una sea unica
   >  * Poder ver las diferentes huellas en una "Galería"     
            
   
   > 🧩 **Conceptos Preliminares**
   > 
   >Con la obra pretendo capturar la esencia efímera de un carnaval, donde cada agente es un 'danzante' impulsado por la energía vibrante de la música. A medida que se mueven, no solo bailan, sino que 'pintan' el lienzo con el rastro de su recorrido, dejando una estela de color que es su prueba efímera de haber estado ahí. La verdadera magia ocurre a nivel colectivo: la suma de todos estos bailes individuales y caóticos va revelando gradualmente una estructura mayor, una huella dactilar. De esta forma, la obra no representa una huella genérica, sino que forma la huella única de ese carnaval en específico, un registro visual e irrepetible forjado por la energía de sus participantes.  
   
   >🖱️ **Interactividad Preliminar**
   >   * Mouse (Movimiento): Actúa como atractor, llamando a los danzantes para guiar la coreografía y concentrar el color en áreas específicas de la huella.
   >      * Mouse (Clic): Genera una ráfaga de danzantes nuevos y de vida corta.
   >      * Teclas 'S', 'A', 'C' : Modulan en tiempo real el comportamiento de la bandada.
   >           * 'S' (Separación): Aumenta el deseo de espacio personal, haciendo el baile más caótico y disperso.
   >           * 'A' (Alineación): Incrementa el orden, haciendo que los danzantes formen ríos de movimiento fluidos.
   >           * 'C' (Cohesión): Fomenta la unión, haciendo que la bandada se agrupe en una masa compacta y densa
   >           * Barra Espaciadora (Modo Lienzo): Oculta a los danzantes activos para permitirte contemplar únicamente la huella pintada con sus estelas.
   >           * Tecla 'G' (Guardar): Guarda la huella actual en la galería y limpia el lienzo para empezar a pintar una nueva.
   >           * Tecla 'V' (Ver Galería): Entra y sale del modo galería, donde puedes ver todas las huellas que has creado una al lado de la otra.
   >             
   > 🧪 **Experimentos**
   >   * Experimento 1.
   >
   >    Lo primero que hice diseñar el flowfield por lo que en cada fotograma el método update() recalcula todos los vectores de la huella basándose en la música. A partir de ahí, la energía de los graves (bassEnergy) controla el “zoom” del ruido Perlin, de modo que con bajos suaves las curvas resultan amplias y fluidas, mientras que con golpes fuertes se contraen, volviéndose más apretadas y complejas. Por otro lado, la energía de los agudos (trebleEnergy) introduce una dimensión temporal al campo: con agudos suaves permanece estable, pero cuando los sonidos son más intensos, como platillos o voces altas, el campo vibra y cambia rápidamente, generando turbulencias que los danzantes deben atravesar. Finalmente, estos danzantes se limitan a seguir el campo de flujo vivo, lo que transforma su recorrido en una coreografía compleja y profundamente conectada con la canción.
>
><p align="center">
  <img src="https://github.com/user-attachments/assets/61756120-e7a9-4a71-91ba-610c46739578" width="45%">
  <img src="https://github.com/user-attachments/assets/283aa74c-3b2a-4ac5-b92f-5c66d41e99a6" width="45%">
</p>

> * Experimento 2.
> 
>El siguiente paso fue agregar a los danzantes para representar el baile. Ellos siguen el campo de flujo y dejan una estela que marca el lugar por donde han pasado. De esta manera, al moverse conforme al flujo, también siguen el ritmo de la música.
>
><img width="734" height="656" alt="Screenshot 2025-10-01 143821" src="https://github.com/user-attachments/assets/783244fd-ed02-42e2-b14a-2556d8d86afc" />

>
> * Experimento 3.
>
> Para que los danzantes se sintieran como un grupo y no como individuos aislados, implementé el algoritmo de Flocking. A partir de este punto, cada agente aplica las tres reglas clásicas: Separación (para no chocar), Alineación (para moverse en la misma dirección) y Cohesión (para mantenerse unidos). Esto se combinó con una conexión más profunda con la música: la forma de su "falda" ahora pulsa con los bajos, mientras que sus colores reaccionan a los agudos, creando una coreografía colectiva mucho más rica y orgánica.
>
> <img width="726" height="641" alt="Screenshot 2025-10-01 145447" src="https://github.com/user-attachments/assets/b1769c11-8acc-4ac3-a925-6642a8c3b108" />
>
> * Experimento 4.
>
>Aquí me enfrenté al desafío más grande: el equilibrio. Por un lado, la estela que dejaban los danzantes o se acumulaba demasiado, saturando la pantalla con líneas, o se desvanecía tan rápido que no se llegaba a formar la huella. Por otro lado, la regla de Separación era un problema: o era muy débil y los danzantes se amontonaban visualmente (ya que sus 'faldas' eran más grandes que su radio de colisión), o era tan fuerte que la bandada se desintegraba.
>
> La solución final fue doble. Para la estela, implementé un 'pulso de limpieza' rítmico: el rastro se acumula suavemente, pero con cada golpe fuerte de la percusión (bassBeat), la pantalla se limpia con un desvanecimiento rápido, manteniendo la imagen siempre fresca. Para la separación, la clave fue recalibrar los pesos de las fuerzas, dándole mucha más prioridad a la separación y aumentando el 'espacio personal' de cada danzante. Esto, junto con hacerlos un poco más pequeños, finalmente logró que el baile se viera fluido y sin amontonamientos.
>
><p align="center">
  <img src="https://github.com/user-attachments/assets/fc8e968f-eca5-4b4e-ab43-16d853ba2c84" width="48%">
  <img src="https://github.com/user-attachments/assets/37081f70-0683-4aba-8ab6-0dc7532b603d" width="48%">
</p>

>
> * Expermineto 5.
>   
> Finalmente, para consolidar la obra como un verdadero instrumento visual, se reintrodujeron y refinaron las interacciones clave. Se implementó una "mesa de mezclas de emociones" con las teclas 'S', 'A' y 'C', permitiendo al usuario modular en tiempo real la emoción de la bandada. Además, se añadieron los "solos" de los danzantes al hacer clic y las explosiones de confeti con los golpes de la música, completando así la atmósfera de carnaval.
>
> <img width="734" height="659" alt="image" src="https://github.com/user-attachments/assets/5fbeccec-65aa-4e13-baaf-0f896fad13bb" />
>
> **Cabe resaltar que la idea original de la huella se desechó en el proceso. Una vez que el campo de flujo comenzó a moverse con la música, se volvió muy difícil que una huella estática se pudiera mantener. Sin embargo, como el reto principal era que la obra se sintiera como un instrumento, decidí centrar todo el enfoque en la expresividad de los danzantes y su coreografía.**
>
> ⚙️ **Descripción Tecnica**
>
>El núcleo de la simulación es un Campo de Flujo (FlowField) dinámico, cuyo campo vectorial se genera en tiempo real mediante Ruido Perlin tridimensional, con parámetros modulados por el análisis de audio FFT de la canción. Una población de agentes autónomos, o "danzantes", navega este entorno combinando el seguimiento del campo con un sistema de Flocking completo (separación, alineación y cohesión), cuyas ponderaciones son manipulables por el usuario como un instrumento visual. Para optimizar la complejidad computacional de la detección de vecinos, se implementa una subdivisión espacial (binning). Finalmente, tanto la apariencia de los danzantes como las estelas que pintan sobre un lienzo de memoria (trailBuffer) son controladas dinámicamente por las diferentes frecuencias del espectro de audio, creando una experiencia sinestésica donde el movimiento y el color son una interpretación directa de la música.
>
> 💬 **Que comunica**
> 
>Lo que quise hacer con esta obra es capturar un poco la esencia de un carnaval. Esa sensación de fiesta vibrante, llena de energía, donde cada persona baila con su propio estilo, con su propio color y su propia alegría. En la simulación, esos “danzantes” representan justamente eso: la individualidad de cada quien. Pero lo interesante no está solo en verlos a cada uno por separado, sino en lo que pasa cuando empiezan a conectarse con la música y entre ellos mismos. Ahí es cuando dejan de ser figuras aisladas y se convierten en una comparsa, como pasa en un carnaval real. Juntos van formando trazos, patrones y figuras que no existirían si bailaran solos.
>
> La idea es que no sea solo un baile individual, sino una suma de alegrías que, al sincronizarse, generan algo mucho más grande y complejo: una huella visual que cambia constantemente y que nunca se repite igual. Como en un carnaval de verdad, cada momento es único, cada trazo cuenta, y la magia surge de la unión de todas esas pequeñas energías en movimiento.
>
> ✨ **Concepto Final**
>
>la simulación transforma el lienzo en una pista de baile donde agentes autónomos, o "danzantes", se mueven al compás de la música. Cada danzante, único en su movimiento, deja una estela de color efímera, una prueba de su existencia en la fiesta. El verdadero corazón de la obra reside en la memoria colectiva: la suma de todos estos rastros individuales va pintando gradualmente una huella dactilar, un símbolo de que cada carnaval, aunque compuesto por innumerables alegrías personales, deja una marca única e irrepetible. El usuario no es un mero espectador, sino el intérprete y director de esta orquesta visual, utilizando la interacción como un instrumento para modular la emoción del baile y, en última instancia, esculpir la forma,
>
> 🖱️ **Interactividad FInal**
>  * Teclas 'S', 'A', 'C' ( Mezclas): Permiten modular la "emoción" de la bandada. La 'S' se encarga de separar a los danzantes para un efecto caótico; la 'A' los alinea en ríos de movimiento fluidos; y la 'C' aumenta la cohesión, agrupándolos en una masa compacta.
>  
>  * Mouse: Actúa como un atractor constante. Todos los danzantes sienten una fuerza que los guía suavemente hacia la posición del cursor, permitiéndote dirigir el foco de la acción.
>  
>  * Clic del Mouse (El Foco del Solista): Al hacer clic cerca de un danzante, este es elegido como "solista" y realiza una pirueta sobre su eje, destacándose del resto del grupo.

2. El código fuente completo de tu sketch en p5.js.
```JS
        // ===================================
// VARIABLES GLOBALES
// ===================================
let danzantes = [];
let confeti = []; // Array para las partículas de confeti
let flowfield;
let trailBuffer;
let cancion, fft;
let audioStarted = false;
let showAgents = true;
const MAX_DANZANTES = 200;

// Variables para la optimización de la cuadrícula
let grid = [];
let gridResolution = 50;
let gridCols, gridRows;

// Variables para la detección de beats y el color rítmico
let globalHue = 220; // Tono inicial (azul estático)
let previousBass = 0;
let previousMid = 0;
let previousTreble = 0;

// Variables del "Instrumento"
let sepWeight = 1.8, aliWeight = 1.0, cohWeight = 1.0;
let targetSep = 1.8, targetAli = 1.0, targetCoh = 1.0;

// Paletas de Colores
let paletaCalida = [];
let paletaFria = [];
let paletaPastel = [];


// ===================================
// FUNCIONES PRINCIPALES DE P5.JS
// ===================================

function preload() {
  // ¡IMPORTANTE! Sube tu canción con el nombre 'DAN.mp3' al editor de p5.js
  cancion = loadSound('DAN.mp3');
}

function setup() {
  createCanvas(windowWidth, windowHeight);
  colorMode(HSB, 360, 100, 100, 100);

  trailBuffer = createGraphics(width, height);
  trailBuffer.colorMode(HSB, 360, 100, 100, 100);
  trailBuffer.background(0);

  fft = new p5.FFT(0.8, 128);
  fft.setInput(cancion);

  paletaCalida = [
    color(0, 80, 100),   // Rojo
    color(20, 90, 100),  // Naranja
    color(40, 100, 100), // Amarillo-Naranja
    color(60, 100, 100), // Amarillo
    color(340, 80, 100), // Rojo-Violeta
  ];

  paletaFria = [
    color(240, 100, 90), // Azul
    color(270, 90, 100), // Morado
    color(300, 80, 100), // Magenta
    color(280, 80, 95),  // Púrpura oscuro
  ];
  
  paletaPastel = [
    color(350, 40, 100), // Rojo pastel
    color(330, 30, 100), // Rosado pastel
    color(0, 0, 100)     // Blanco
  ];

  flowfield = new FlowField(20);
  
  // Inicializa la cuadrícula de optimización
  initGrid();
}

function draw() {
  if (!audioStarted) {
    background(0);
    fill(255);
    textAlign(CENTER, CENTER);
    textSize(20);
    text("Haz clic para comenzar", width / 2, height / 2);
    return;
  }
  
  background(0);

  fft.analyze();
  let bassEnergy = fft.getEnergy('bass');
  let midEnergy = fft.getEnergy('mid');
  let trebleEnergy = fft.getEnergy('treble');

  // --- LÓGICA DE COLOR RÍTMICO Y PULSO DE LIMPIEZA ---
  let targetHue = 220;
  let lerpSpeed = 0.05;
  
  const bassThreshold = 1.1; 
  const midThreshold = 1.15;
  const trebleThreshold = 1.2;

  let bassBeat = bassEnergy > previousBass * bassThreshold && bassEnergy > 120;
  let midBeat = midEnergy > previousMid * midThreshold && midEnergy > 90;
  let trebleBeat = trebleEnergy > previousTreble * trebleThreshold && trebleEnergy > 60;

  if (bassBeat) {
    targetHue = 0;
    lerpSpeed = 0.6;
    trailBuffer.background(0, 0, 0, 40); 
  } else {
    trailBuffer.background(0, 0, 0, 0.5);
  }
  
  if (midBeat) {
    targetHue = 60;
    lerpSpeed = 0.6;
  } else if (trebleBeat) {
    targetHue = 300;
    lerpSpeed = 0.6;
  }
  
  globalHue = lerp(globalHue, targetHue, lerpSpeed);

  previousBass = bassEnergy;
  previousMid = midEnergy;
  previousTreble = trebleEnergy;


  image(trailBuffer, 0, 0);

  flowfield.update(bassEnergy, trebleEnergy);
  
  updateInstrument(); // Actualiza los pesos del instrumento
  updateAndDrawSystems(bassEnergy, midEnergy, trebleEnergy, bassBeat);
  // drawUI(); // UI desactivada
}

function updateAndDrawSystems(bassEnergy, midEnergy, trebleEnergy, bassBeat) {
  if (danzantes.length < MAX_DANZANTES && frameCount % 5 === 0) {
    let cantidad = map(bassEnergy, 0, 255, 0, 3);
    for(let i=0; i<cantidad; i++){
       danzantes.push(new Danzante(random(width), random(height)));
    }
  }

  // --- EXPLOSIONES DE CONFETI ---
  if (bassBeat && danzantes.length > 0) {
    for (let i = 0; i < 3; i++) {
      let d = random(danzantes);
      for (let j = 0; j < 15; j++) {
        confeti.push(new ParticulaConfeti(d.position.x, d.position.y, paletaCalida));
      }
    }
  }
  
  // Actualiza el confeti
  for (let i = confeti.length - 1; i >= 0; i--) {
    let p = confeti[i];
    p.update();
    if (p.isDead()) {
      confeti.splice(i, 1);
    }
  }
  
  for (let i = 0; i < gridCols; i++) {
    for (let j = 0; j < gridRows; j++) {
      grid[i][j] = [];
    }
  }
  for (let d of danzantes) {
    let col = floor(d.position.x / gridResolution);
    let row = floor(d.position.y / gridResolution);
    col = constrain(col, 0, gridCols - 1);
    row = constrain(row, 0, gridRows - 1);
    grid[col][row].push(d);
  }


  for (let i = danzantes.length - 1; i >= 0; i--) {
    let d = danzantes[i];
    
    let neighbors = [];
    let col = floor(d.position.x / gridResolution);
    let row = floor(d.position.y / gridResolution);
    for (let x = -1; x <= 1; x++) {
      for (let y = -1; y <= 1; y++) {
        let checkCol = col + x;
        let checkRow = row + y;
        if (checkCol >= 0 && checkCol < gridCols && checkRow >= 0 && checkRow < gridRows) {
          neighbors = neighbors.concat(grid[checkCol][checkRow]);
        }
      }
    }
    
    d.run(neighbors, flowfield, { bass: bassEnergy, mid: midEnergy, treble: trebleEnergy });
    d.drawTrail(trailBuffer, { bass: bassEnergy, mid: midEnergy, treble: trebleEnergy });
    if (d.isDead()) {
      danzantes.splice(i, 1);
    }
  }

  drawEscena(bassEnergy, midEnergy, trebleEnergy);
}

function drawEscena(bassEnergy, midEnergy, trebleEnergy){
    if (showAgents) {
      for (let d of danzantes) {
        d.show({ bass: bassEnergy, mid: midEnergy, treble: trebleEnergy });
      }
    }
    // Dibuja el confeti encima de todo
    for (let p of confeti) {
        p.show();
    }
}


// ===================================
// CLASES Y FUNCIONES DE INTERACCIÓN
// ===================================

function keyPressed() {
  if (key === ' ') showAgents = !showAgents;
}

function mousePressed() {
  if (!audioStarted) {
    cancion.loop();
    audioStarted = true;
    return;
  }
  
  let closestDist = Infinity;
  let closestDanzante = null;
  
  for (let d of danzantes) {
    let dist = p5.Vector.dist(d.position, createVector(mouseX, mouseY));
    if (dist < closestDist) {
      closestDist = dist;
      closestDanzante = d;
    }
  }
  
  if (closestDanzante && closestDist < 50) {
    closestDanzante.startSolo();
  }
}

function drawUI(){
    // La UI ha sido desactivada para una experiencia visual limpia
}

function updateInstrument() {
  targetSep = 1.8;
  targetAli = 1.0;
  targetCoh = 1.0;
  let sepLerpSpeed = 0.1;

  if (keyIsDown(83)) { 
    targetSep = 4.0;
    sepLerpSpeed = 0.8;
  }
  if (keyIsDown(65)) { 
    targetAli = 2.0; 
  } 
  if (keyIsDown(67)) {
    targetCoh = 2.5;
  }
  
  sepWeight = lerp(sepWeight, targetSep, sepLerpSpeed);
  aliWeight = lerp(aliWeight, targetAli, 0.1);
  cohWeight = lerp(cohWeight, targetCoh, 0.1);
}

function initGrid() {
  gridCols = floor(width / gridResolution);
  gridRows = floor(height / gridResolution);
  grid = new Array(gridCols);
  for (let i = 0; i < gridCols; i++) {
    grid[i] = new Array(gridRows);
  }
}

function windowResized() {
  resizeCanvas(windowWidth, windowHeight);
  trailBuffer = createGraphics(width, height);
  trailBuffer.colorMode(HSB, 360, 100, 100, 100);
  trailBuffer.background(0);
  initGrid();
}

// ===================================
// CLASE DANZANTE (AGENTE)
// ===================================

class Danzante {
  constructor(x, y, lifespan = random(300, 500)) {
    this.position = createVector(x, y);
    this.velocity = p5.Vector.random2D();
    this.acceleration = createVector(0, 0);
    this.baseMaxSpeed = random(1.5, 3);
    this.maxspeed = this.baseMaxSpeed;
    this.maxforce = random(0.5, 1.0);
    this.r = random(2, 5);
    this.history = [];
    this.lifespan = lifespan;
    this.initialLifespan = lifespan;
    this.oscOffset = random(1000);
    this.spin = 0;
    this.spinVelocity = 0;
    this.soloTimer = 0;
  }

  isDead() { return this.lifespan < 0; }

  run(neighbors, flowfield, audioData) {
    this.flock(neighbors, flowfield, audioData);
    this.update(audioData);
    this.borders();
  }

  flock(neighbors, flowfield, audioData) {
    let flow = flowfield.lookup(this.position);
    let sep = this.separate(neighbors);
    let ali = this.align(neighbors);
    let coh = this.cohere(neighbors);
    let mouse = this.seek(createVector(mouseX, mouseY));
    
    flow.mult(1.2);
    sep.mult(sepWeight); 
    ali.mult(aliWeight);
    coh.mult(cohWeight);
    mouse.mult(0.3);
    
    this.applyForce(flow);
    this.applyForce(sep);
    this.applyForce(ali);
    this.applyForce(coh);
    this.applyForce(mouse);
  }

  applyForce(force) { this.acceleration.add(force); }

  startSolo() {
    this.spinVelocity += random(PI, TWO_PI);
    this.soloTimer = 60;
  }

  update(audioData) {
    this.maxspeed = this.baseMaxSpeed + map(audioData.mid, 0, 255, 0, 2.0);
    
    let swayForce = this.velocity.copy();
    swayForce.rotate(PI / 2);
    let swayMagnitude = sin(frameCount * 0.2 + this.oscOffset) * map(audioData.mid, 0, 255, 0, this.maxforce * 0.5);
    swayForce.setMag(swayMagnitude);
    this.applyForce(swayForce);

    this.spin += this.spinVelocity;
    this.spinVelocity *= 0.9;

    if (this.soloTimer > 0) {
      this.soloTimer--;
    }

    this.velocity.add(this.acceleration);
    this.velocity.limit(this.maxspeed);
    this.history.push(this.position.copy());
    this.position.add(this.velocity);
    this.acceleration.mult(0);
    this.lifespan -= 1;
    if (this.history.length > 20) {
      this.history.splice(0, 1);
    }
  }

  show(audioData) {
    let lifeRatio = this.lifespan / this.initialLifespan;
    let { h, s, b } = this.getColor(audioData);
    
    let soloEffect = this.soloTimer / 60.0;
    let baseRadius = this.r * map(audioData.bass, 0, 255, 0.7, 2.0);
    baseRadius *= (1 + soloEffect * 1.5);
    let finalBrightness = b + (soloEffect * 20);

    push();
    translate(this.position.x, this.position.y);
    rotate(this.velocity.heading() + PI / 2 + this.spin);

    stroke(h, s, finalBrightness, 60 * lifeRatio * (1 + soloEffect));
    strokeWeight(1.5 + soloEffect * 2);
    fill(h, s, finalBrightness, 20 * lifeRatio * (1 + soloEffect));

    let numPeaks = 8;
    let angleStep = 360 / (numPeaks * 2);
    beginShape();
    for (let i = 0; i < 360; i += angleStep) {
      let radius = (floor(i / angleStep) % 2 === 0) ? baseRadius * 1.1 : baseRadius * 0.8;
      let x = cos(radians(i)) * radius;
      let y = sin(radians(i)) * radius;
      vertex(x, y);
    }
    endShape(CLOSE);
    
    noStroke();
    fill(h, s, 100, 80 * lifeRatio * (1 + soloEffect * 2));
    ellipse(0, 0, this.r * 0.6 * (1 + soloEffect));

    pop();
  }
  
  drawTrail(buffer, audioData){
    if (this.history.length < 2) return;
    
    let lifeRatio = this.lifespan / this.initialLifespan;
    let { h, s, b } = this.getColor(audioData);
    
    let pos = this.position;
    let prevPos = this.history[this.history.length - 2];
    
    if (p5.Vector.dist(pos, prevPos) < this.maxspeed * 10) {
      let alpha = 5 * lifeRatio;
      let trailBrightness = map(audioData.bass, 0, 255, 80, 100);
      buffer.stroke(h, s, trailBrightness, alpha);
      buffer.strokeWeight(map(audioData.bass, 0, 255, 1, 3));
      buffer.line(pos.x, pos.y, prevPos.x, prevPos.y);
    }
  }

  getColor(audioData) {
    let h = globalHue;
    let s = map(audioData.mid, 0, 255, 70, 100);
    let b = map(audioData.bass, 0, 255, 80, 100);
    return { h, s, b };
  }

  seek(target) {
    let desired = p5.Vector.sub(target, this.position);
    desired.setMag(this.maxspeed);
    let steer = p5.Vector.sub(desired, this.velocity);
    steer.limit(this.maxforce);
    return steer;
  }
  
  borders() {
    if (this.position.x < -this.r) this.position.x = width + this.r;
    if (this.position.y < -this.r) this.position.y = height + this.r;
    if (this.position.x > width + this.r) this.position.x = -this.r;
    if (this.position.y > height + this.r) this.position.y = -this.r;
  }
}

// ===================================
// CLASE FLOWFIELD (LA HUELLA)
// ===================================
class FlowField {
    constructor(r) {
    this.resolution = r;
    this.cols = floor(width / this.resolution);
    this.rows = floor(height / this.resolution);
    this.field = new Array(this.cols);
    for (let i = 0; i < this.cols; i++) {
      this.field[i] = new Array(this.rows);
    }
    this.zoff = 0;
  }

  init() {
    // No necesita init() si se recalcula en update()
  }

  update(bass, treble) {
    let noiseIncrement = map(bass, 0, 255, 0.02, 0.3);
    let zSpeed = map(treble, 0, 255, 0.005, 0.05);
    let xoff = 0;
    for (let i = 0; i < this.cols; i++) {
      let yoff = 0;
      for (let j = 0; j < this.rows; j++) {
        let angle = noise(xoff, yoff, this.zoff) * TWO_PI * 2;
        this.field[i][j] = p5.Vector.fromAngle(angle);
        yoff += noiseIncrement;
      }
      xoff += noiseIncrement;
    }
    this.zoff += zSpeed;
  }

  lookup(position) {
    let column = constrain(floor(position.x / this.resolution), 0, this.cols - 1);
    let row = constrain(floor(position.y / this.resolution), 0, this.rows - 1);
    return this.field[column][row].copy();
  }
}

// ===================================
// CLASE PARTÍCULA BASE Y CONFETI
// ===================================
class Particula {
  constructor(x, y, lifespan = 100) {
    this.position = createVector(x, y);
    this.velocity = createVector(0, 0);
    this.acceleration = createVector(0, 0);
    this.lifespan = lifespan;
  }
  update() {
    this.velocity.add(this.acceleration);
    this.position.add(this.velocity);
    this.acceleration.mult(0);
    this.lifespan -= 1;
  }
  isDead() { return this.lifespan < 0; }
  show() {}
}

class ParticulaConfeti extends Particula {
  constructor(x, y, palette) {
    super(x, y, 100);
    this.velocity = p5.Vector.random2D().mult(random(2, 5));
    this.r = random(1.5, 3); // Más pequeño
    this.angle = random(TWO_PI);
    this.angleVelocity = random(-0.1, 0.1);
    this.color = random(palette);
  }

  update() {
    this.velocity.y += 0.05; // Gravedad
    this.velocity.mult(0.99); // Fricción
    this.position.add(this.velocity);
    this.angle += this.angleVelocity;
    this.lifespan -= 2;
  }

  show() {
    let lifeRatio = this.lifespan / 100;
    push();
    translate(this.position.x, this.position.y);
    rotate(this.angle);
    noStroke();
    fill(hue(this.color), saturation(this.color), brightness(this.color), 80 * lifeRatio); 
    rectMode(CENTER);
    square(0, 0, this.r * 2);
    pop();
  }
}


// Métodos de Flocking
Danzante.prototype.separate = function(neighbors) {
  let desiredseparation = this.r * 20;
  let steer = createVector(0, 0);
  let count = 0;
  for (let other of neighbors) {
    let d = p5.Vector.dist(this.position, other.position);
    if ((d > 0) && (d < desiredseparation)) {
      let diff = p5.Vector.sub(this.position, other.position);
      diff.normalize();
      diff.div(d);
      steer.add(diff);
      count++;
    }
  }
  if (count > 0) {
    steer.div(count);
  }
  if (steer.mag() > 0) {
    steer.setMag(this.maxspeed);
    steer.sub(this.velocity);
    steer.limit(this.maxforce);
  }
  return steer;
}

Danzante.prototype.align = function(neighbors) {
  let neighbordist = 50;
  let sum = createVector(0, 0);
  let count = 0;
  for (let other of neighbors) {
    let d = p5.Vector.dist(this.position, other.position);
    if ((d > 0) && (d < neighbordist)) {
      sum.add(other.velocity);
      count++;
    }
  }
  if (count > 0) {
    sum.div(count);
    sum.setMag(this.maxspeed);
    let steer = p5.Vector.sub(sum, this.velocity);
    steer.limit(this.maxforce);
    return steer;
  } else {
    return createVector(0, 0);
  }
}

Danzante.prototype.cohere = function(neighbors) {
  let neighbordist = 50;
  let sum = createVector(0, 0);
  let count = 0;
  for (let other of neighbors) {
    let d = p5.Vector.dist(this.position, other.position);
    if ((d > 0) && (d < neighbordist)) {
      sum.add(other.position);
      count++;
    }
  }
  if (count > 0) {
    sum.div(count);
    return this.seek(sum);
  } else {
    return createVector(0, 0);
  }
}
```

3. Un enlace a tu sketch en el editor de p5.js.
   > [apply unidad 6](https://editor.p5js.org/LCami-Villanueva/sketches/he0CXgyon)

4. Capturas de pantalla mostrando tu pieza en acción.
   >
   > <img width="789" height="675" alt="image" src="https://github.com/user-attachments/assets/b09a8ba8-5178-4d51-9b0c-6cac1c565050" />

   
     
      


  












