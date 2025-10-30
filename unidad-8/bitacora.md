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
   > ![20251030-0600-25 4093284](https://github.com/user-attachments/assets/da912e3e-3198-40dc-baa4-c028ba0d1ce7)

   > ### 4
   > Fianlmente añadí la interactividad, transformando la simulación en una performance controlada. Utilizando la lógica de temporizadores y el input del teclado. Ahora puedo expresar la narrativa de supervivencia con comandos: provoco el Pulso de Brillo (K), fuerzo el Blackout (L) o manipulo el entorno con los efectos de Rotación (Q/W) y Paletas Temporales. Estos inputs me permiten acentuar la disonancia emocional de la música, creando la lucha por la luz en tiempo real .
   >
   > https://github.com/user-attachments/assets/07aca93a-5205-4c65-851f-85ee6cf3ed86
   >
## Actividad 03
 
 1. El código fuente completo de tu sketch en p5.js.
``` JS
    // Simulación p5.js — Estrellita + Puertas + Pasillo
// FINAL CODE: Incluye efectos temporales, inicio suave, corrección BW, pulso de brillo,
// y blackout fugaz de 0.2 segundos, INDEPENDIENTE de otros efectos.

let song, fft;
let estrellita;
let pasillo = [];
let portales = [];
let trailLayer, glowLayer, portalLayer;

// portal / spacing
let portalInnerRadius, portalSpacingFraction, portalSpacing, basePortalVel, maxPortalRadio;

// pasillo color (Gris Pálido Fijo)
let currentR = 230, currentG = 230, currentB = 240, currentAlpha = 80;

// interacción velocidad
let manualSpeed = 1.0;
let manualSpeedStep = 0.5;
let manualOverrideTimer = 0;
let manualOverrideDuration = 120; // 2 segundos

// blackout
let blackoutGlobalTimer = 0;
let blackoutGlobalDuration = 12; // ✨ AJUSTE: 0.2 segundos
// ---

// límites
let wallHalf = 0;

// palette mode (se resetea a 'normal' después del timer)
let paletteMode = 'normal';

// rotación global (se resetea a 0 después del timer)
let portalRotationDir = 0; // -1 ccw, 0 none, +1 cw
let portalRotationSpeed = 0.02; 

// --- TEMPORIZADORES CLAVE ---
let temporaryEffectTimer = 0;
const TEMPORARY_DURATION = 60; // 60 frames = 1 segundo (Efectos Q, W, 1, 2, 3, K)

let initialDelayTimer = 0;
const INITIAL_DELAY_DURATION = 60; // 60 frames = 1 segundo (Inicio suave del Pasillo)
// ----------------------------


function preload() {
  song = loadSound('TheMilkCarton.mp3');
}

function setup() {
  createCanvas(windowWidth, windowHeight);

  portalLayer = createGraphics(width, height);
  trailLayer = createGraphics(width, height);
  trailLayer.noStroke();
  glowLayer = createGraphics(width, height);
  glowLayer.noStroke();

  fft = new p5.FFT();
  song.connect(fft);

  estrellita = new Estrellita();

  for (let i = 0; i < 100; i++) pasillo.push(new FormaPasillo());

  portalInnerRadius = width / 10;
  maxPortalRadio = dist(0, 0, width / 2, height / 2);
  portalSpacingFraction = random(0.25, 0.5);
  portalSpacing = portalSpacingFraction * (maxPortalRadio - portalInnerRadius);
  basePortalVel = 1.0;

  let numPortales = 5;
  for (let i = 0; i < numPortales; i++) {
    let p = new PuertaCosmica();
    p.startInnerRadius = portalInnerRadius;
    p.maxRadio = maxPortalRadio;
    p.velBase = basePortalVel;
    p.radio = portalInnerRadius + i * portalSpacing;
    portales.push(p);
  }

  colorMode(RGB, 255, 255, 255, 100);
  wallHalf = (width / 10) / 2;
  noStroke();

  // INICIALIZAR TEMPORIZADOR DE ANIMACIÓN INICIAL
  initialDelayTimer = INITIAL_DELAY_DURATION;
}

function draw() {
  fft.analyze();
  let energiaRasgueo = fft.getEnergy("highMid");
  let velocidadMundoAudio = map(energiaRasgueo, 40, 200, 0.5, 8.0, true);

  // 1. MANEJO DE TEMPORIZADORES GLOBALES
  if (manualOverrideTimer > 0) manualOverrideTimer--;
  if (blackoutGlobalTimer > 0) blackoutGlobalTimer--;
  if (initialDelayTimer > 0) initialDelayTimer--;

  // Reset de efectos temporales (Paleta, Rotación, Brillo de Estrellita)
  if (temporaryEffectTimer > 0) {
    temporaryEffectTimer--;
  } else {
    paletteMode = 'normal'; 
    portalRotationDir = 0; 
    estrellita.starBrightnessMultiplier = 1.0; // Restaura el brillo al valor normal
  }

  let velocidadMundo = (manualOverrideTimer > 0) ? manualSpeed : velocidadMundoAudio;

  estrellita.update(velocidadMundo);

  for (let p of portales) p.update(velocidadMundo, energiaRasgueo);
  for (let f of pasillo) f.update(velocidadMundo, estrellita);

  portalLayer.clear();
  for (let p of portales) p.show(portalLayer);

  trailLayer.background(0, 15);
  for (let f of pasillo) f.show(trailLayer);

  glowLayer.clear();
  estrellita.drawGlowSource(glowLayer);
  glowLayer.filter(BLUR, 10);

  background(0);
  image(trailLayer, 0, 0);
  image(portalLayer, 0, 0);
  blendMode(ADD);
  image(glowLayer, 0, 0);
  blendMode(BLEND);

  estrellita.drawTrail();
  estrellita.show();

  // HUD MÍNIMO
  push();
  noStroke();
  fill(255);
  textSize(12);
  textAlign(LEFT, TOP);
  const currentRotation = portalRotationDir === 1 ? 'CW (T)' : portalRotationDir === -1 ? 'CCW (T)' : 'OFF';
  const currentPalette = paletteMode === 'normal' ? 'Normal' : `${paletteMode.toUpperCase()} (T)`;
  const currentBrightness = estrellita.starBrightnessMultiplier > 1.0 ? 'PULSE (T)' : 'Normal';
  
  text(`Paleta (1/2/3/0): ${currentPalette}`, 12, height - 58);
  text(`Rotación (Q/W): ${currentRotation}`, 12, height - 40);
  text(`Brillo Estrella (K): ${currentBrightness}`, 12, height - 22);
  pop();
}

// ---------------- Clase PuertaCosmica (Rotación y Color Temporal + BW Estricto) ----------------
class PuertaCosmica {
  constructor() {
    this.vpX = width / 2;
    this.vpY = height / 2;
    this.maxRadio = maxPortalRadio || dist(0, 0, this.vpX, this.vpY);
    this.startInnerRadius = portalInnerRadius || (width / 10);
    this.startRadio = this.startInnerRadius * 1.0;
    this.radio = this.startRadio;
    this.velBase = 1.0;

    this.strokeW = 2;
    this.numPetals = floor(random(8, 15));
    this.currentVel = 0;
    this.currentEnergy = 0;
    this.noiseSeedShape = random(1000);

    this.layer1_shape = floor(random(3));
    this.layer2_shape = floor(random(3));
    this.layer3_shape = floor(random(3));
    this.layer2_isFilled = random() > 0.5;
    this.layer3_isFilled = random() > 0.5;
    this.initialAlphaProgress = 0;

    this.rotationAngle = random(TWO_PI);

    this.currentColor = { r: 120, g: 120, b: 180 };

    // Almacena RGB como números primitivos
    this.randomColor = { r: random(60, 255), g: random(60, 255), b: random(60, 255) };
  }

  reset() {
    this.strokeW = random(1.5, 4);
    this.numPetals = floor(random(8, 15));
    this.noiseSeedShape = random(1000);
    this.layer1_shape = floor(random(3));
    this.layer2_shape = floor(random(3));
    this.layer3_shape = floor(random(3));
    this.layer2_isFilled = random() > 0.5;
    this.layer3_isFilled = random() > 0.5;

    let inner = this.startInnerRadius || (width / 10);
    let spacing = portalSpacing || (random(0.25, 0.5) * (this.maxRadio - inner));

    let minRadio = Infinity;
    for (let q of portales) if (q !== this && typeof q.radio === 'number') minRadio = min(minRadio, q.radio);

    if (!isFinite(minRadio)) this.radio = inner;
    else this.radio = max(inner, minRadio - spacing);

    this.radio = constrain(this.radio, inner, this.maxRadio * 0.9);
    this.initialAlphaProgress = 0;

    // Almacena RGB como números primitivos al resetear
    this.randomColor = { r: random(60, 255), g: random(60, 255), b: random(60, 255) };
  }

  update(velocidad, energia) {
    this.radio += this.velBase * velocidad;
    this.currentEnergy = energia;

    // Rotación: Usa el valor global
    if (portalRotationDir !== 0) {
      this.rotationAngle += portalRotationDir * portalRotationSpeed * velocidad;
    }

    // CALCULAR COLOR OBJETIVO
    let target = this.computeTargetColor(energia);

    // Aplicar fluctuación Perlin
    let per = map(noise(this.noiseSeedShape + frameCount * 0.009), 0, 1, -8, 8);

    // Suavizado interpolando currentColor hacia target+perlin
    this.currentColor.r = lerp(this.currentColor.r, constrain(target.r + per, 0, 255), 0.06);
    this.currentColor.g = lerp(this.currentColor.g, constrain(target.g + per, 0, 255), 0.06);
    this.currentColor.b = lerp(this.currentColor.b, constrain(target.b + per, 0, 255), 0.06);

    // ✨ AJUSTE CLAVE 1: Forzar Escala de Grises Estricta en el modo 'bw'
    // Elimina cualquier tinte residual después del LERP promediando los canales.
    if (paletteMode === 'bw') {
        let avg = (this.currentColor.r + this.currentColor.g + this.currentColor.b) / 3;
        this.currentColor.r = avg;
        this.currentColor.g = avg;
        this.currentColor.b = avg;
    }

    if (this.initialAlphaProgress < 100) {
      this.initialAlphaProgress += 3 * velocidad;
      this.initialAlphaProgress = constrain(this.initialAlphaProgress, 0, 100);
    }

    if (this.radio > this.maxRadio) {
      this.reset();
    }
  }

  // Devuelve un objeto {r,g,b} target según paletteMode y energía
  computeTargetColor(energia) {
    if (paletteMode === 'random') {
      // Devuelve el objeto simple
      return this.randomColor; 
    }

    if (paletteMode === 'bw') {
      let v = map(energia, 40, 200, 40, 220, true);
      return { r: v, g: v, b: v };
    }

    if (paletteMode === 'warm') {
      let r = map(energia, 40, 200, 160, 255, true);
      let g = map(energia, 40, 200, 60, 150, true);
      let b = map(energia, 40, 200, 20, 80, true);
      return { r: r, g: g, b: b };
    }

    // normal (original reactive mapping)
    let r = map(energia, 40, 200, 0, 255, true);
    let g = map(energia, 40, 200, 0, 165, true);
    let b = map(energia, 40, 200, 255, 100, true);
    return { r: r, g: g, b: b };
  }

  show(pg) {
    pg.push();
    pg.translate(this.vpX, this.vpY);
    pg.rotate(this.rotationAngle);
    pg.colorMode(RGB, 255, 255, 255, 100);

    // Usamos los valores ajustados (r, g, b)
    let r = this.currentColor.r;
    let g = this.currentColor.g;
    let b = this.currentColor.b;
    let baseAlpha = map(this.radio, this.startRadio, this.maxRadio, 30, 100, true);

    // Capa 1: Color base
    let color1 = pg.color(r, g, b, baseAlpha * 0.9);
    let color2, color3;
    
    // ✨ AJUSTE CLAVE 2: NEUTRALIZAR VARIACIONES DE COLOR EN MODO BW
    if (paletteMode === 'bw') {
        // En BW, las capas secundarias deben ser el mismo gris que color1
        color2 = color1;
        color3 = color1;
    } else {
        // Modo Normal/Warm/Random: Aplica variación para el efecto cromático
        color2 = pg.color(constrain(r + 20, 0, 255), constrain(g + 10, 0, 255), constrain(b - 20, 0, 255), baseAlpha);
        color3 = pg.color(constrain(r - 20, 0, 255), constrain(g - 10, 0, 255), constrain(b + 20, 0, 255), baseAlpha);
    }

    let angleStep = TWO_PI / this.numPetals;
    let radioInterno = this.radio * 0.25;

    // --- Lógica de Dibujo de las 3 Capas (usando color1, color2, color3) ---
    pg.stroke(color1);
    pg.strokeWeight(this.strokeW * 1.5);
    pg.noFill();
    if (this.layer1_shape == 0 || this.layer1_shape == 2) {
      pg.ellipse(0, 0, this.radio * 2, this.radio * 2);
    } else if (this.layer1_shape == 1) {
      pg.fill(color1);
      for (let i = 0; i < this.numPetals; i++) {
        let x = this.radio * cos(angleStep * i);
        let y = this.radio * sin(angleStep * i);
        pg.ellipse(x, y, this.strokeW * 2, this.strokeW * 2);
      }
    }

    pg.stroke(color2);
    pg.strokeWeight(this.strokeW);
    let r_mid_ext = this.radio * 0.7;
    let r_mid_int = radioInterno * 1.5;
    pg.rotate(angleStep / 2.0);
    if (this.layer2_shape == 2) pg.noFill();
    else if (this.layer2_isFilled) pg.fill(color2);
    else pg.noFill();
    if (this.layer2_shape == 0) {
      for (let i = 0; i < this.numPetals; i++) {
        pg.beginShape();
        pg.curveVertex(r_mid_int, 0); pg.curveVertex(r_mid_int, 0);
        pg.curveVertex(r_mid_ext * 0.8, -this.radio * 0.2);
        pg.curveVertex(r_mid_ext, 0);
        pg.curveVertex(r_mid_ext * 0.8, this.radio * 0.2);
        pg.curveVertex(r_mid_int, 0); pg.curveVertex(r_mid_int, 0);
        pg.endShape();
        pg.rotate(angleStep);
      }
    } else if (this.layer2_shape == 1) {
      for (let i = 0; i < this.numPetals; i++) {
        pg.beginShape();
        pg.curveVertex(r_mid_int, 0); pg.curveVertex(r_mid_int, 0);
        pg.curveVertex(r_mid_ext, -this.radio * 0.3);
        pg.curveVertex(r_mid_ext, this.radio * 0.3);
        pg.curveVertex(r_mid_int, 0); pg.curveVertex(r_mid_int, 0);
        pg.endShape();
        pg.rotate(angleStep);
      }
    } else if (this.layer2_shape == 2) {
      pg.ellipse(0, 0, r_mid_ext * 2, r_mid_ext * 2);
    }
    pg.rotate(-angleStep * this.numPetals);
    pg.rotate(-angleStep / 2.0);

    pg.stroke(color3);
    pg.strokeWeight(this.strokeW);
    if (this.layer3_shape == 1) pg.noFill();
    else if (this.layer3_isFilled) pg.fill(color3);
    else pg.noFill();
    let r_inner_ext = this.radio * 0.4;
    let r_inner_int = radioInterno;
    if (this.layer3_shape == 0) {
      for (let i = 0; i < this.numPetals; i++) {
        pg.beginShape();
        pg.curveVertex(r_inner_int, 0); pg.curveVertex(r_inner_int, 0);
        pg.curveVertex(r_inner_ext * 0.8, -this.radio * 0.1);
        pg.curveVertex(r_inner_ext, 0);
        pg.curveVertex(r_inner_ext * 0.8, this.radio * 0.1);
        pg.curveVertex(r_inner_int, 0); pg.curveVertex(r_inner_int, 0);
        pg.endShape();
        pg.rotate(angleStep);
      }
    } else if (this.layer3_shape == 1) {
      for (let i = 0; i < this.numPetals; i++) {
        pg.beginShape();
        pg.curveVertex(r_inner_ext, 0); pg.curveVertex(r_inner_ext, 0);
        pg.curveVertex(r_inner_int * 1.2, -this.radio * 0.1);
        pg.curveVertex(r_inner_int, 0);
        pg.curveVertex(r_inner_int * 1.2, this.radio * 0.1);
        pg.curveVertex(r_inner_ext, 0); pg.curveVertex(r_inner_ext, 0);
        pg.endShape();
        pg.rotate(angleStep);
      }
    } else if (this.layer3_shape == 2) {
      pg.fill(color3);
      for (let i = 0; i < this.numPetals; i++) {
        let x = r_inner_ext * cos(angleStep * i);
        let y = r_inner_ext * sin(angleStep * i);
        pg.ellipse(x, y, this.strokeW * 3, this.strokeW * 3);
      }
    }
    pg.pop();
  }
}

// ---------------- Clase Estrellita (Funciones de Dibujo + Brillo Temporal) ----------------
class Estrellita {
  constructor() {
    this.baseX = width / 2;
    this.baseY = height / 2;
    this.currentX = this.baseX;
    this.currentY = this.baseY;
    this.bobTime = 0;

    this.trailLength = 30;
    this.trailStartWidth = 7;
    this.trailEndWidth = 2;
    this.trailStartAlpha = 50;
    this.trailEndAlpha = 0;
    this.tailWiggleTime = random(1000);

    this.starColor = color(255, 255, 200);
    this.starSize = 6;
    this.glowSourceSize = this.starSize * 2.5;

    this.starBrightnessMultiplier = 1.0; 

    this.zigzagTime = random(2000);
    this.offset = createVector(0, 0);
    this.vel = createVector(0, 0);
    this.mass = 1.0;
    this.damping = 0.92;
    this.springK = 0.06;
    this.repulsionTimer = 0;
    this.repulsionDuration = 18;
    this.blackoutTimer = 0;
    this.blackoutDuration = 12; // ✨ AJUSTE: 0.2 segundos

    this.lateralNoiseSeed = random(1000);
    this.lateralNoiseAmp = 6.0;
    this.lateralNoiseSpeed = 0.018;

    this.gestureActive = false;
    this.gestureDir = 1;
    this.gestureFrame = 0;
    this.gestureFramesTotal = 60;
    this.gestureScaleX = 80;
    this.gestureScaleY = 60;
  }

  applyForce(force) {
    let f = p5.Vector.div(force, this.mass);
    this.vel.add(f);
  }

  startGesture(direction, frames) {
    this.gestureActive = true;
    this.gestureDir = (direction >= 0) ? 1 : -1;
    this.gestureFrame = 0;
    this.gestureFramesTotal = frames || this.gestureFramesTotal;
    this.vel.x += this.gestureDir * 6;
  }

  teardropPoint(t, sx, sy) {
    let theta = map(t, 0, 1, -PI / 2, 3 * PI / 2);
    let r = 1 - sin(theta);
    let x = r * cos(theta) * sx;
    let y = r * sin(theta) * sy;
    return createVector(x, y);
  }

  update(velocidadMundo) {
    let velocidadBobBase = 0.05;
    let velocidadBobExtra = map(velocidadMundo, 0.5, 8, 0, 0.15);
    let velocidadBobTotal = velocidadBobBase + velocidadBobExtra;
    let amplitudBob = map(velocidadMundo, 0.5, 8, 1, 6);
    let bobY = sin(this.bobTime) * amplitudBob;
    this.bobTime += velocidadBobTotal;

    let amplitudZigzag = map(velocidadMundo, 0.5, 8, 1, 5);
    let zigzagX = map(noise(this.zigzagTime), 0, 1, -amplitudZigzag, amplitudZigzag);
    this.zigzagTime += 0.01;

    let gestureOffset = createVector(0, 0);
    if (this.gestureActive) {
      let t = this.gestureFrame / max(1, this.gestureFramesTotal);
      gestureOffset = this.teardropPoint(t, this.gestureScaleX, this.gestureScaleY);
      gestureOffset.x *= this.gestureDir;
      this.gestureFrame++;
      if (this.gestureFrame >= this.gestureFramesTotal) this.gestureActive = false;
    }

    let perlinBase = map(noise(this.lateralNoiseSeed + frameCount * this.lateralNoiseSpeed), 0, 1, -1, 1);
    let lateralPerlinX = perlinBase * this.lateralNoiseAmp;

    let targetLateral;
    if (this.gestureActive) {
      targetLateral = gestureOffset.x + lateralPerlinX * 0.25;
      this.offset.y = lerp(this.offset.y, gestureOffset.y * 0.35, 0.12);
    } else {
      targetLateral = lateralPerlinX + zigzagX * 0.6;
      this.offset.y = lerp(this.offset.y, 0, 0.06);
    }

    this.offset.x = lerp(this.offset.x, targetLateral, 0.22);

    this.offset.add(this.vel);
    this.vel.mult(this.damping);

    let spring = p5.Vector.mult(this.offset, -this.springK);
    this.vel.add(spring);

    if (this.repulsionTimer > 0) this.repulsionTimer--;
    if (this.blackoutTimer > 0) this.blackoutTimer--;

    this.currentX = this.baseX + zigzagX + this.offset.x;
    this.currentY = this.baseY + bobY + this.offset.y;

    this.currentX = constrain(this.currentX, this.baseX - wallHalf, this.baseX + wallHalf);
  }

  drawGlowSource(pg) {
    if (blackoutGlobalTimer > 0 || this.blackoutTimer > 0) return;
    pg.fill(this.starColor);
    pg.ellipse(this.currentX, this.currentY, this.glowSourceSize * this.starBrightnessMultiplier, this.glowSourceSize * this.starBrightnessMultiplier);
  }

  show() {
    noStroke();
    if (blackoutGlobalTimer > 0 || this.blackoutTimer > 0) return;
    fill(this.starColor);
    ellipse(this.currentX, this.currentY, this.starSize * this.starBrightnessMultiplier, this.starSize * this.starBrightnessMultiplier);
  }

  drawTrail() {
    if (blackoutGlobalTimer > 0 || this.blackoutTimer > 0) return;
    noStroke();
    let normX = 0, normY = 1;
    let r = red(this.starColor), g = green(this.starColor), b = blue(this.starColor);
    let perpX = normY, perpY = -normX;
    for (let i = 0; i < this.trailLength; i++) {
      let progress = i / this.trailLength;
      let baseX = this.currentX + normX * i;
      let baseY = this.currentY + normY * i;
      let wiggleAmount = map(noise(this.tailWiggleTime + i * 0.1), 0, 1, -8, 8);
      let finalWiggle = wiggleAmount * progress;
      let x = baseX + perpX * finalWiggle;
      let y = baseY + perpY * finalWiggle;
      let currentWidth = lerp(this.trailStartWidth, this.trailEndWidth, progress) * this.starBrightnessMultiplier;
      let currentAlpha = lerp(this.trailStartAlpha, this.trailEndAlpha, progress);
      fill(r, g, b, currentAlpha);
      ellipse(x, y, currentWidth, currentWidth);
    }
  }
}

// ---------------- Clase FormaPasillo ----------------
class FormaPasillo {
  constructor() {
    this.tamCuadroOrigen = width / 10;
    this.vpX = width / 2;
    this.vpY = height / 2;
    this.reset();
  }
  reset() {
    let enLadoHorizontal = random() > 0.5;
    let medioTamLados = this.tamCuadroOrigen / 2;
    let tamArriba = this.tamCuadroOrigen * 0.98;
    let tamAbajo = this.tamCuadroOrigen * 0.02;
    let bordeSuperior = this.vpY - tamArriba;
    let bordeInferior = this.vpY + tamAbajo;
    let bordeIzquierdo = this.vpX - medioTamLados;
    let bordeDerecho = this.vpX + medioTamLados;
    if (enLadoHorizontal) {
      this.x = random(bordeIzquierdo, bordeDerecho);
      this.y = random() > 0.5 ? bordeSuperior : bordeInferior;
    } else {
      this.x = random() > 0.5 ? bordeIzquierdo : bordeDerecho;
      this.y = random(bordeSuperior, bordeInferior);
    }
    let dirX = this.x - this.vpX;
    let dirY = this.y - this.vpY;
    let mag = sqrt(dirX * dirX + dirY * dirY);
    if (mag === 0) mag = 0.01;
    this.velX = dirX / mag;
    this.velY = dirY / mag;
    this.velBase = random(0.5, 1.5);
  }
  
  update(velocidadAudio, estrella) {
    // AJUSTE: Escalar la velocidad al inicio de la simulación (movimiento gradual)
    let speedScale = 1.0;
    if (initialDelayTimer > 0) {
      speedScale = map(initialDelayTimer, INITIAL_DELAY_DURATION, 0, 0.1, 1.0, true);
    }
    
    let velocidadTotal = this.velBase * velocidadAudio * speedScale;
    this.x += this.velX * velocidadTotal;
    this.y += this.velY * velocidadTotal;
    let d = dist(this.x, this.y, estrella.currentX, estrella.currentY);
    let radioRepulsion = 80;
    if (d < radioRepulsion) {
      let repelX = this.x - estrella.currentX;
      let repelY = this.y - estrella.currentY;
      if (d > 0) { repelX /= d; repelY /= d; }
      let fuerza = map(d, 0, radioRepulsion, 5, 0);
      this.x += repelX * fuerza;
      this.y += repelY * fuerza;
    }
    if (this.x < 0 || this.x > width || this.y < 0 || this.y > height) this.reset();
  }
  
  show(pg) {
    pg.colorMode(RGB, 255, 255, 255, 100);
    let distCentro = dist(this.x, this.y, this.vpX, this.vpY);
    let maxDist = dist(0, 0, this.vpX, this.vpY);
    let progreso = map(distCentro, 0, maxDist, 0, 1, true);
    
    // AJUSTE: Escalar el tamaño del punto al inicio de la simulación (crecimiento gradual)
    let sizeScale = 1.0;
    if (initialDelayTimer > 0) {
      sizeScale = map(initialDelayTimer, INITIAL_DELAY_DURATION, 0, 0, 1.0, true);
    }
    
    // AJUSTE DE TAMAÑO: Rango más sutil (0.5 a 2.5) y aplicación del factor de escala.
    let tamPunto = map(progreso, 0, 1, 0.5, 2.5) * sizeScale;
    
    let alpha = map(distCentro, 0, maxDist, 30, 100);
    let finalColor = color(currentR, currentG, currentB, alpha);
    pg.fill(finalColor);
    pg.noStroke();
    pg.ellipse(this.x, this.y, tamPunto, tamPunto);
    pg.stroke(finalColor);
    pg.strokeWeight(tamPunto * 0.7);
    let colitaX = this.x - this.velX * tamPunto * 2;
    let colitaY = this.y - this.velY * tamPunto * 2;
    pg.line(colitaX, colitaY, this.x, this.y);
    pg.noStroke();
  }
}

// ---------------- Interacción (teclado) ----------------
function mousePressed() {
  if (!song.isPlaying()) song.loop();
}

function keyPressed() {
  // velocidad global override
  if (keyCode === UP_ARROW) {
    manualSpeed = constrain(manualSpeed + manualSpeedStep, 0.1, 12);
    manualOverrideTimer = manualOverrideDuration;
  } else if (keyCode === DOWN_ARROW) {
    manualSpeed = constrain(manualSpeed - manualSpeedStep, 0.1, 12);
    manualOverrideTimer = manualOverrideDuration;
  }

  // gesturas laterales
  if (keyCode === LEFT_ARROW) estrellita.startGesture(-1, 60);
  else if (keyCode === RIGHT_ARROW) estrellita.startGesture(1, 60);

  // blackout (Solo afecta al blackout, no toca otros timers de efectos temporales)
  if (key === 'l' || key === 'L') {
    blackoutGlobalTimer = blackoutGlobalDuration; // 0.2s
    estrellita.blackoutTimer = estrellita.blackoutDuration; // 0.2s
  }

  // AJUSTE DE PALETAS TEMPORALES
  if (key === '1') {
    paletteMode = 'warm';
    temporaryEffectTimer = TEMPORARY_DURATION;
  } else if (key === '2') {
    paletteMode = 'bw';
    temporaryEffectTimer = TEMPORARY_DURATION;
  } else if (key === '3') {
    paletteMode = 'random';
    // Asigna un objeto simple {r, g, b} a cada portal
    for (let p of portales) {
      p.randomColor = { r: random(60, 255), g: random(60, 255), b: random(60, 255) };
    }
    temporaryEffectTimer = TEMPORARY_DURATION;
  } else if (key === '0') {
    paletteMode = 'normal';
    temporaryEffectTimer = 0; // Desactiva directamente el timer
  }

  // AJUSTE DE ROTACIÓN TEMPORAL
  if (key === 'q' || key === 'Q') {
    portalRotationDir = 1; // Fuerza CW
    temporaryEffectTimer = TEMPORARY_DURATION;
  } else if (key === 'w' || key === 'W') {
    portalRotationDir = -1; // Fuerza CCW
    temporaryEffectTimer = TEMPORARY_DURATION;
  }

  // ✨ NUEVO: AJUSTE DE BRILLO TEMPORAL DE LA ESTRELLA
  if (key === 'k' || key === 'K') {
    estrellita.starBrightnessMultiplier = 2.0; // Doble de brillo/tamaño
    temporaryEffectTimer = TEMPORARY_DURATION;
  }


  // evitar comportamiento por defecto (scroll con flechas)
  return false;
}
````
 2. Un enlace a tu sketch en el editor de p5.js.
    >
    > [P5.JS WEB EDITOR | FINAL SIMULACIÓN](https://editor.p5js.org/LCami-Villanueva/sketches/60PL8-6Ta)
    
    
 4. Capturas de pantalla mostrando tu pieza en acción.
    >
    > <img width="1227" height="881" alt="image" src="https://github.com/user-attachments/assets/dbd67937-a578-4a0f-b1a3-d39f491e171a" />
    >
    > <img width="1472" height="875" alt="image" src="https://github.com/user-attachments/assets/495a1b4f-7d6c-4c6a-a057-d9ad1fa0de94" />
    >
    > <img width="1620" height="870" alt="image" src="https://github.com/user-attachments/assets/162ca7f7-e6db-4173-9df6-8b637c2ff42a" />
    >
    > <img width="612" height="653" alt="image" src="https://github.com/user-attachments/assets/feb032f0-ebdb-4d5c-b62d-d2cf16346b4d" />
    
    ## Autoevalución:
    ### Nota Propuesta **5.0**. 

Esta nota se justifica porque en el proyecto final complete las **tres actividades requeridas de la rúbrica** y cumplí con el objetivo principal de la unidad: **Integrar los conceptos y técnicas para crear una pieza de arte generativo algorítmico, interactiva y en tiempo real**. La bitácora demuestra que el sistema pasó de vectores y partículas básicas a una performance controlada.

#### 2. 
* **Integración de Conceptos y Técnicas:** El código final combina con éxito la **Física de resorte** (para el movimiento elástico de la Estrella), las **Fuerzas** (para la repulsión del pasillo), los **Sistemas de Partículas**, y el **Ruido Perlin** (para la distorsión caótica).
* **Diseño e Implementación de un Sistema Generativo:** Se diseñó un sistema de visualización que interpreta la disonancia de la canción. Las **Puertas** (arte generativo) reaccionan al audio, y la **Rotación** se usa como un acto expresivo en tiempo real.
* **Interpretación Musical en Tiempo Real (Liveness):** Logré crear una narrativa controlable. Los comandos como el **Pulso de Brillo (K)**, el **Blackout Fugaz (L) de 0.2s**, y los **Efectos Temporales** me permiten interpretar la lucha por la supervivencia de la Estrellita justo en el momento que lo exige la música.








