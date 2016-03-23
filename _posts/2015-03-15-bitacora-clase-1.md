---
layout:     post
title:      "Primeros programas y procedimientos"
subtitle:   "Bitácora de la clase del martes 15/03/2016"
date:       2016-03-15 22:10:00
author:     "Fede"
---

Arrancamos la clase recuperando el mapa conceptual de la última vez, para organizar un poco las ideas.

![Mapa Conceptual](/img/2016-02-29/mapaConceptos.png)

Como casi todos habían resuelto la guía de tarea (¡genial!), hicimos un rápido repaso del universo que nos propone Gobstones, que consta de:

* un **tablero** cuadriculado donde podemos poner y sacar bolitas de colores azul, negro, rojo y verde
* un **cabezal**, similar al de las máquinas de peluches/relojes/punteros láser, que todo el tiempo está sobre alguna celda y puede desplazarse y manipular las bolitas
* **primitivas** que nos sirven para operar el cabezal: `Poner`, `Sacar` y `Mover`.

Vimos cómo instalar PyGobstones y lo dejamos funcionando en todas las compus que llevaron. Hablamos de que esta va a ser la herramienta predilecta para trabajar en la clase, ya que nos da más libertad para explorar, sin tener una consigna asociada (aunque todavía no sabemos muy bien cómo aprovechar eso). Para la mayoría de las tareas y como repaso o introducción de los temas, vamos a seguir usando Mumuki.

Con todo esto aclarado, nos pusimos a resolver algunos ejercicios de la guía 1, que la pueden encontrar en la sección de [Material](/material). La tentación de la mayoría fue largarse a escribir código antes de pensar, lo que vimos que más o menos funcionaba para los primeros ejercicios pero se volvía tedioso para dibujos más complicados. 

Después de un rato de laburo, paramos la pelota y empezamos a discutir, entre todos, sobre qué estrategia habían usado para resolver cada uno de los problemas. Al volcar esto sobre el pizarrón, vimos que todo este cuentito de la estrategia estaba muy lindo, pero que el programa terminaba siendo un choclo de `Poner'es` y `Mover'es`, y necesitabamos alguna forma de que nuestra estrategia **quede plasmada** en el código: _si tan solo pudieramos crear nuestros propios comandos..._

Y de repente ¡pum!, nos dimos cuenta que veníamos hablando hace rato de esto de los procedimientos y que en Gobstones también se pueden escribir (y son mucho más lindos que los `f1`, `f2` del Lightbot porque les puedo poner el nombre que se me antoje). Sobre esto no vamos a decir nada más acá, les queda de tarea resolver la nueva guía sobre procedimientos, que la encuentran en [http://inpr-sarmiento.mumuki.io](http://inpr-sarmiento.mumuki.io).

Habiendo visto la luz, descubrimos que los ejercicios que habíamos hecho un rato antes se podrían reescribir con procedimientos, quedando así una solución mucho más legible y fácil de modificar. Y con esto nos despedimos hasta la semana próxima, porque este Jueves no tenemos clases.

Como tarea, quedó entonces:

* Instalar PyGobstones en casa, siguiendo las instrucciones que están en la sección [Software](/software).
* Resolver dentro de PyGobstones los ejercicios **c** y **d** de las bolitas azules, enviando los _.gbs_ a nuestros mails personales y no a la lista.
* Resolver la nueva guía sobre procedimientos, que la encuentran en [http://inpr-sarmiento.mumuki.io](http://inpr-sarmiento.mumuki.io).