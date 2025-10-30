# Evidencias de la unidad 8
## Actividad 01 💡
1. Describe tus observaciones sobre la conexión sonido-imagen en al menos dos de las performances vistas.
   > ### Performances 1: LE PARODY & ALBA G. CORRAL
   > La verdad la conexión sonido-imagen es muy evidente a lo largo del video esto hace que las iamgnes se vean como una coreografía, una interpretación. Por un lado, el ritmo marca muchos aspectos y se pude ver como alguna sveces con este se lanzando ráfaga  de partículas sincronizadas con los golpes de la percusión.  Tambien muchas veces se ve que la musica modula el entorno alterando la poca o mucha intesidad en forma simagenes y colores dependiendo de la musica. Pero obviamnete se nota que al ser en tiempo real manejado por el artista esto le da un toque mucho mas personalidado y unico.
   >
   > ### Performances 2: Performance at Festival des Bains Numeriques #9
   > Al igual que en el video anterior, aquí el ritmo también es primordial. Se nota que maneja las explosiones y el tamaño de los círculos, pero creo que en este performance el color brilla mucho más; es más expresivo y deja ver mejor lo que se está interpretando. Sobre todo, la manera en que las formas se juntan, creando figuras que representan los altos y bajos de la música, me parece increíble."
   > 
2. Explica qué elementos te parecieron generativos y por qué crees que cada visualización sería única.
   > Para mí, los elementos generativos son claros: las formas, especialmente todo cómo algunas parecen seguir a otras, los movimientos, la velocidad con que se mueven, y por supuesto, los colores y los cambios de paleta.
   >
   > Siento que lo que hace que cada visualización sea única viene de dos fuentes. Primero, el sistema debe usar aleatoriedad para decidir cómo reacciona a la música; esto le da un toque impredecible sin que deje de interpretar la canción. Pero, principalmente, la clave es el factor humano. El hecho de que una persona pueda manipular los parámetros en tiempo real hace que cada presentación sea irrepetible, ya que depende mucho de lo que la música le haga sentir al artista en ese preciso momento. La forma en que decide mover esos parámetros, como la intensidad o el color, siempre va a variar en cada show.

3. Comparte tu reflexión sobre la sensación de “liveness”.
   > Para mí, la sensación de "liveness" se da principalmente por la intervención humana en tiempo real. Es lo que diferencia esto de un simple visualizador automático y lo convierte en una interpretación en el momento, **reflejando** lo que se **siente** en ese instante en el show. Es la combinación de cómo la música te hace "sentir" algo y la decisión técnica de "mover los parámetros" para reaccionar a eso. Yo creo que es esa mezcla entre la lógica del sistema y el sentir humano lo que hace que cada performance sea totalmente única e irrepetible, y **genera** esa sensación de**l** **"aquí y el ahora"**, **donde** tanto **tú** como **espectador** como el **intérprete** **están** **en** la misma sintonía,por lo que esta sensación te hace sentir que es un momento especial y me parece fundamental en este tipo de shows.

## Actividad 02
1.  La pieza musical elegida (con enlace/archivo si es posible).
    > La canción elegida es [The Milk Cartoon de Madilyn Mei](https://www.youtube.com/watch?v=vzlgrmieUAs)
    >
#### 2. La descripción de tu concepto visual.

> Mi concepto visual es una metáfora de la disonancia de la canción. La protagonista, una única luz (la Estrellita), está huyendo de un espacio oscuro e infinito que representa la "cacería".
>
> La Estrellita corre por un "pasillo infinito", que es una ilusión de formas que fluyen constantemente hacia ella. El conflicto central es la **"oscuridad"**.
>
> Mi rol es manipular esta realidad. Puedo evocar un **Pulso de Brillo (K)**, forzar un **Blackout Fugaz (L)** para simular el agotamiento, o manipular las formas y colores del entorno (Rotación y Paletas temporales), transformando el pasaje de un sueño delicado a una pesadilla inquietante para reflejar esa lucha interna.

---

#### 3. Los inputs seleccionados y la justificación de por qué los elegiste.

##### 3.1. Inputs Reactivos (Automáticos)

* **Ritmo de la Canción (Rasgueo Urgente):** La Energía HighMid de FFT controla la velocidad del pasillo. Vincula directamente la sensación de "huida" con la urgencia rítmica de la canción.
* **Tensión Armónica (La Oscuridad):** La intensidad de la música manipula la paleta de colores general de las Puertas, reflejando el cambio emocional del "cuento de hadas" a la "pesadilla".
* **Movimiento de la Estrellita:** El movimiento lateral caótico (bandazos erráticos) de la Estrella se intensifica con la música, simulando la desesperación.

##### 3.2. Inputs de Performance (Manuales)

**Nota:** Todos los efectos manuales (excepto Acelerar/Frenar) tienen una duración de **1 segundo** o menos, enfatizando el control fugaz y dramático.

* **Acelerador / Freno Manual (Flechas UP/DOWN):** Permite crear **"sprints"** o momentos de **"agotamiento"** (Override de Velocidad).
* **Pulso de Brillo (Tecla K):** Es el **"Grito de Poder"** de la estrella. Aumenta temporalmente el tamaño y la luminiscencia para desafiar a la oscuridad.
* **Blackout Fugaz (Tecla L):** Simula la vulnerabilidad extrema. Apaga y enciende la luz en solo **0.2 segundos** (12 frames), creando un parpadeo rápido.
* **Rotación de la Realidad (Teclas Q/W):** Fuerza la rotación del entorno, interpretando el **retorcimiento del espacio** (inspiración en Alexander Calder) por 1 segundo.
* **Paletas Temporales (Teclas 1, 2, 3):** Permite cambiar el entorno visual (Warm, BW estricto, Random) temporalmente.
* **Control de Distorsión (Flechas LEFT/RIGHT):** Permite realizar **"Gestos"** o movimientos laterales elásticos que interpretan la evasión y la lucha por el equilibrio.
* **Ancho del Pasillo (Repulsor):** Este control se implementó como una **fuerza repulsora fija** de la Estrellita, estableciendo su "presencia" inherente.

---

#### 4. ¿Qué algoritmos o técnicas planeas usar y por qué?

* **Sistemas de Partículas:** Técnica central para el "Pasillo Infinito" y la Estela de Luz.
* **Física de Muelle/Amortiguación:** Utilizado en la Estrellita para dar un movimiento elástico y orgánico que simula la lucha por el equilibrio.
* **Fuerzas:** La Estrellita aplica una **fuerza repulsora fija** al entorno, la mecánica clave de su interacción.
* **Ruido Perlin (`noise()`):** Usado para la **"Distorsión"** (movimiento lateral errático) de la Estrellita, añadiendo pánico y vida al protagonista.
* **Control de Frame-Rate y Temporización:** Uso de contadores de *frame* para gestionar los efectos manuales con **precisión temporal** y el inicio suave de la simulación.
5. Tus bocetos y una explicación de cómo los inputs influirán en los visuales.
   > ### Bocetos:
   >
   > > Mi concepto visual final sigue siendo una metáfora de la disonancia de la canción, manteniendo el contraste entre el dulce *cuento de hadas* y el *terror de la cacería*. La protagonista (la Estrellita) es la única luz, constantemente huyendo a través de un pasillo infinito de formas que representan la oscuridad.

### La Lucha por la Luz: Conexión de Inputs y Visuales

#### 1.  Inputs Reactivos (La Música como Antagonista)

* **Ritmo (Rasgueo Urgente):** El pulso rítmico controla la velocidad del pasillo y de las puertas cósmicas. A mayor urgencia en la canción, más rápido fluye el túnel hacia la Estrellita, aumentando la sensación de pánico y huida.
* **Tensión Armónica (Tonalidad):** La intensidad de la música mapea la paleta de colores del pasillo. Esto refleja el cambio de estado emocional, pasando de tonos suaves de "cuento de hadas" a tonos inquietantes de "pesadilla".
* **Movimiento de la Estrellita:** La Estrellita tiene un movimiento lateral caótico que se intensifica con la velocidad de la música, simulando los "bandazos erráticos" de desesperación.

#### 2.Inputs de Performance 

Estos comandos manuales crean picos de intensidad expresiva de **1 segundo** de duración.

* **Acelerador/Freno (Flechas UP/DOWN):** Permite hacer un *override* momentáneo de la velocidad. Se usa para crear un "sprint" dramático o momentos de "agotamiento".
* **Pulso de Brillo (Tecla K):** Es mi "Grito de Poder". La Estrellita y su estela duplican su tamaño y luminiscencia , desafiando a la oscuridad con un pulso de luz intensa.
* **Blackout Fugaz (Tecla L):** Simula la vulnerabilidad extrema. La luz desaparece y reaparece en solo **0.2 segundos**, creando un parpadeo rápido como si la luz estuviera al borde de la extinción.
* **Rotación de la Realidad (Teclas Q/W):** Fuerza a las Puertas Cósmicas a rotar. Esto interpreta el retorcimiento del espacio  ante la presión, llevando el túnel a una pesadilla espiralada por 1 segundo.
* **Paletas Temporales (Teclas 1, 2, 3):** Permite cambiar el entorno visual (Warm, BW estricto, Random) para acentuar un sentimiento, volviendo a la paleta reactiva al finalizar el segundo.
* **Control de Distorsión (Flechas LEFT/RIGHT):** Permite realizar "Gestos" o movimientos laterales elásticos, interpretando la evasión y la lucha por el equilibrio.

  ### Proceso
   >###1
   > El primer paso fue establecer el escenario y la protagonista. Necesitaba una "única luz" simple y un entorno que generara la ilusión de huida. Utilicé partículas muy básicas para construir el pasillo infinito, configurándolas para que fluyeran desde el centro hacia afuera, lo que establece la perspectiva y el movimiento inicial. La Estrellita aquí es solo un punto simple en un espacio oscuro y estático, listo para recibir vida.
   > 
   > <img width="1136" height="846" alt="image" src="https://github.com/user-attachments/assets/97ad7d0d-6ed2-495d-ae39-98a96eec58a4" />
   >
   > ### 2
   >A continuación, a la estrellita le implementé la física para darle un movimiento elástico y estable. Lo más importante fue añadir la estela y el brillo, que definen a la Estrellita como una entidad de luz. La estela se creó como un rastro de partículas que se desvanece, reforzando la sensación de velocidad y movimiento constante a través del pasillo.
   >    
   > ![Recording 2025-10-29 190608](https://github.com/user-attachments/assets/7b4eb9ef-74cd-4c2d-859a-efe0a622d859)
   >
   >### 3
   >introduje las formas, el elemento de arte generativo. Estas formas complejas, compuestas de capas y pétalos que reaccionan al audio, se vuelven el corazón dinámico del túnel. Su aparición y color (Azul/Morado) ahora completan el entorno, creando el pasaje en que la Estrellita debe navegar, pasando de un punto estático a un mundo vivo y cambiante.
   >
   > ![20251030-0600-25 4093284](https://github.com/user-attachments/assets/da912e3e-3198-40dc-baa4-c028ba0d1ce7

   > ### 4
   > Fianlmente añadí la interactividad, transformando la simulación en una performance controlada. Utilizando la lógica de temporizadores y el input del teclado. Ahora puedo expresar la narrativa de supervivencia con comandos: provoco el Pulso de Brillo (K), fuerzo el Blackout (L) o manipulo el entorno con los efectos de Rotación (Q/W) y Paletas Temporales. Estos inputs me permiten acentuar la disonancia emocional de la música, creando la lucha por la luz en tiempo real .
   >
   > 











