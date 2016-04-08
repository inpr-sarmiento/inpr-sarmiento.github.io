---
layout:     post
title:      'Expresiones v1'
subtitle:   "Bitácora de la clase del jueves 07/04/2016"
date:       2016-04-07 16:48:00
author:     "Alf"
---
Buenas!


Hoy hicimos los siguientes ejercicios:

1. Volver a definir el procedimiento que hicieron con Fede de la guía 2 (`PonerConDobleYTriple(cantRojas)`), que pone en la celda actual, la cantidad indicada de celdas rojas, el doble de negras, y el triple de verdes. Esta vez, sin usar repeat, usando `PonerN` (que ya la tienen definida) y usando _expresiones_.

1. Hacer el procedimiento `ReplicarAzulesConRojas()`, que pone tantas bolitas rojas en el casillero actual como cantidad de bolitas azules. Para ilustrar lo que hace, tres ejemplos:
![replicar.png](/img/2016-04-07/replicar.png)

1. Hacer el procedimiento `SacarTodas(color)` que saca todas las bolitas del casillero actual que son del `color` indicado.

1. Ejecutar **a mano**, a partir del tablero inicial propuesto, este programa, y obtener **el tablero final**: ¡NO VALE EJECUTARLO en Gobstones!
![queHace.png](/img/2016-04-07/queHace.png)
![evaluar.png](/img/2016-04-07/evaluar.png)

1. `DuplicarCelda()`, que duplica todos los colores. Es decir, si en el tablero inicial en la celda actual ya hay 2 bolitas rojas y 5 azules, cuando el procedimiento DuplicarCelda() se ejecute, el tablero final tendrá 4 bolitas rojas y 10 azules.

1. `PasarTodoANegro()`  “transforma” todas las bolitas de la celda actual en negras.

1. `DejarExactamente(color,n)`, cuando hay muchas bolitas de un color, este procedimiento sirve para sacar las necesarias para llegar a `n`. (**No vale Poner** en ningún momento, sólo sacar)

1. Hacer el procedimiento `Linea(long,dir,color)` que sea como LineaVa (usarla), pero que al finalizar deje el cabezal en la posición inicial.

### Fotos de la clase
¡Recuerden que no hay que repetir código! En particular en `PasarTodoANegro()` deberían reusar `SacarTodas()`

![introExp.png](/img/2016-04-07/introExp.png)
![replicarsol.png](/img/2016-04-07/replicarsol.png)
![teoria.jpg](/img/2016-04-07/teoria.jpg)
![seguimiento.png](/img/2016-04-07/seguimiento.png)
![dejarExactamente.png](/img/2016-04-07/dejarExactamente.png)
![linea.png](/img/2016-04-07/linea.png)

### Tarea
1. Hacer el procedimiento `TocoYMeVoy(dir,color)`, que viaja en la dirección `dir`, pone una bolita del `color` indicado, y vuelve. Para saber cuántas veces moverse,  _cuenta las bolitas negras del casillero inicial_. ¡Reusar procedimientos que ya hayamos hecho!
O sea, Si parto de este tablero: ![inicial1.png](/img/2016-04-07/inicial1.png) y hago `TocoYMeVoy(Este,Rojo)`, obtengo este tablero: ![final1.png](/img/2016-04-07/final1.png) Porque había 3 bolitas negras en la posición inicial.
Si parto de este tablero: ![inicial2.png](/img/2016-04-07/inicial2.png) y hago `TocoYMeVoy(Oeste,Verde)`, obtengo este tablero: ![final2.png](/img/2016-04-07/final2.png) Porque había 2 bolitas negras en la posición inicial.

1. Hacer el procedimiento `Ele3(direccion)` que hace una "L" de 3 bolitas de ancho y 3 bolitas de alto. La dirección indica el sentido de la "L". Por ejemplo, si ejecutamos: `Ele3(Norte)` dibuja una clásica "L", y si ejecutamos: `Ele3(Oeste)` dibuja una "L" acostada, mirando hacia arriba. El casillero inicial es la esquina de la L, y el cabezal debe volver a la posición inicial. Por ejemplo, `Ele3(Oeste)` produce lo siguiente:
![ele.png](/img/2016-04-07/ele.png)
_Pista: necesitan una expresión que está en el machete de Gobstones y que todavía no vieron_
