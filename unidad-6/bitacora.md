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
   > **Craig Reynolds** es el padre del concepto de fuerzas de dirección.La relación es directa y fundamental; él acuñó el término y desarrolló el modelo que seguimos utilizando hoy.
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
   > Su trabajo no solo sentó las bases para la simulación de vida artificial, sino que se convirtió en una técnica estándar en la industria de los **videojuegos,

   ### Actividad 03 ✏️


