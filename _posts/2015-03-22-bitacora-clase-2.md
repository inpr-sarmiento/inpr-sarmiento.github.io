---
layout:     post
title:      "Procedimientos con y sin parámetros"
subtitle:   "Bitácora de la clase del martes 22/03/2016"
date:       2016-03-22 22:10:00
author:     "Fede"
---

### Primera parte: Procedimientos

Recuperamos las distintas estrategias al problema del cuadrado y el reloj de arena (o moño). Vimos que a grandes rasgos las soluciones se parecían, aunque algunas utilizaban algún procedimiento más de una vez. Sin saber todavía bien por qué, dijimos que _en general_ vamos a preferir aquellas soluciones cuya estructura se pueda contar como "hacer esto, eso y aquello 3/5/1000 veces".

Luego hablamos brevemente de cómo probar los programas que escribimos. Distinguimos esto según la herramienta con la cual estemos trabajando:

* en **Mumuki** las pruebas ya las escribió alguien más (el profe), entonces yo como estudiante sólo tengo que mandar mi ejercicio y ver si cumple o no cumple. Ojo, como Mumuki es una máquina se puede equivocar, siempre la última palabra la tiene el profe de carne y hueso;
* en **PyGobstones** las pruebas las tengo que pensar yo, porque no hay nada que me impida hacer y deshacer a mi antojo. Relacionado con esto, vimos cómo configurar el tablero inicial en 3 de sus dimensiones: posición del cabezal, bolitas iniciales y tamaño. Al final no nos dio el tiempo para aprovechar esto, pero lo ensayamos con algunos ejemplos sencillos.

Hecho ese (no tan) pequeño paréntesis, nos abocamos a la tarea de interpretar un código feo, sin procedimientos, que dibujaba "algo":

![escalera-azul.png](/img/2016-03-22/escalera-azul.png)

La tarea era entonces reescribir el programa, eligiendo una estrategia y armando procedimientos que dieran cuenta de ella. Se complicó un poco porque "faltaba un `Mover(Norte)`" que hacía que el programa no fuera _exactamente_ repetir lo mismo 4 veces. Entre todas las propuestas, preferimos la que manejaba los movimientos al norte por fuera del procedimiento `DibujarEscalon()`, por esta misma razón misteriosa que mencioné al principio de esta bitácora. Otra cosa que reforzamos: los procedimientos **se definen una única vez** y **se pueden usar infinitas**, en este caso cuatro.

En lo que quedaba hasta el recreo, practicamos esto de usar varias veces un mismo procedimiento con los dibujos que están en las páginas 5 y 6 de la guía inicial (que, como ya saben, está en la sección [Material](/material)). **Quedó como primera tarea terminar del a al f y mandarlo por mail a ambos profes.**

### Segunda parte: Parámetros
Lo que queríamos hacer ahora era construir un cuadrado hueco, sin rellenar. Haciendo un poco de trampa, forcé la estrategia para que fuera "sin levantar el lápiz" y nos quedó un programa que pedía a gritos ser parametrizado porque hacía lo mismo para cada uno de los bordes, sólo cambiaba la dirección en la cual lo dibujaba. 

Charlamos un poco sobre cómo escribir los nombres de los parámetros (con primera letra minúscula) y jugamos al "anda o no anda" con distintas variantes, sacando como conclusión que a la computadora lo único que le importa es que respetemos orden y cantidad, los nombres son sólo para nosotros.

Para saber más de esto, **les queda como segunda tarea resolver los ultimos ejercicios de la guía 3 de Mumuki y la guía 4 completa**.
