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

  ### Actividad 4
  - Crea un nuevo sketch en p5.js que represente una distribución normal.
  - Copia el código en tu bitácora.
  - Coloca en enlace a tu sketch en p5.js en tu bitácora.
  - Selecciona una captura de pantalla de tu sketch y colócala en tu bitácora.
