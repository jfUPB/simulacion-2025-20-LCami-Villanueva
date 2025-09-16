# Evidencias de la unidad 5
🧐🧪✍ Para cada una de las simulaciones: ¿Cómo se está gestionando la creación y la desaparción de las partículas y cómo se gestiona la memoria en cada una de las simulaciones?
### Ejemplo 4.2
> **Las partículas se crean con particles.push(new Particle(width / 2, 20));. Dentro de la clase Particle hay un método llamado isDead(), que revisa un atributo llamado lifespan. Ese valor va disminuyendo cada vez que se ejecuta update(), y cuando llega a ser menor que 0, la partícula se elimina con splice. Así, las partículas que ya no sirven desaparecen y la memoria se va liberando de manera progresiva.**
### Ejemplo 4.4
> Aquí funciona de forma parecida al ejemplo anterior, solo que ahora se hace mediante otra clase llamada Emitter(). Esta clase se encarga de controlar tanto la generación como la desaparición de las partículas. Además, cada vez que haces click se crea un nuevo Emitter, el cual se encarga de gestionarse por sí mismo.
### Ejemplo 4.5
> La forma de generar las partículas es parecida al ejemplo anterior, pero con una diferencia: después de crear el Emitter, al momento de generar cada partícula se usa un random para decidir si será un círculo o un cuadrito (que corresponde a la clase Confetti). La eliminación sigue siendo igual, usando splice para quitar las partículas cuando ya no sirven.
### Ejemplo 4.6
> La gestión funciona de la misma manera que en el ejemplo anterior: se crea un Emitter en el setup y, en cada frame, este va generando una nueva partícula. Luego, gracias a la revisión con isDead(), cada partícula se elimina en el momento adecuado, lo que evita que se acumulen infinitas partículas y asegura que la memoria se libere progresivamente.
### Ejemplo 4.7
> La gestión vuelve a ser la misma: se crea un Emitter y en cada frame este genera una nueva partícula. Después, con la función isDead(), se eliminan las que ya cumplieron su ciclo.
