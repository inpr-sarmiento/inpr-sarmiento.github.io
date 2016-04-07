---
layout:     post
title:      'Expresiones v1'
subtitle:   "Bitácora de la clase del jueves 07/04/2016"
date:       2016-04-07 16:48:00
author:     "Alf"
---
Buenas!

practica
caso borde (linea comun) (-1)

Hoy hicimos los siguientes ejercicios:
1. Volver a definir el procedimiento que hicieron con Fede de la guía 2 (`PonerConDobleYTriple(cantRojas)`), que pone en la celda actual, la cantidad indicada de celdas rojas, el doble de negras, y el triple de verdes. Esta vez, sin usar repeat, usando `PonerN` (que ya la tienen definida) y usando _expresiones_.
1. Hacer el procedimiento `ReplicarAzulesConRojas()`, que pone tantas bolitas rojas en el casillero actual como cantidad de bolitas azules. Para ilustrar lo que hace, tres ejemplos:
![replicar.png](/img/2016-04-07/replicar.png)
1. Hacer el procedimiento `SacarTodas(color)` que saca todas las bolitas del casillero actual que son del `color` indicado.
1. Decir qué hace lo siguiente:
```gbs
program {
	PonerN(nroBolitas(Verde), Negro)
	Mover(Este)
	PonerN(nroBolitas(Verde), Negro)
	PonerN(nroBolitas(Rojo), Negro)
	Mover(Este)
	PonerN(nroBolitas(Azul), Negro)
}
```
![evaluar.png](/img/2016-04-07/evaluar.png)

1. `DuplicarCelda()`, que duplica todos los colores.
1. `PasarTodoANegro()`  “transforma” todas las bolitas de la celda actual en negras.
1. `DejarExactamente(color,n)`, cuando hay muchas bolitas de un color, este procedimiento sirve para sacar las necesarias para llegar a `n`. (No vale SacarTodas!!)
1. Hacer el procedimiento `Linea(long,dir,color)` que sea como LineaVa (ejem, usarla), pero que al finalizar deje el cabezal en la posición inicial.
1. Hacer el procedimiento `Ele3(direccion)` que hace una "L" de 3 bolitas de ancho y 3 bolitas de alto. La dirección indica el sentido de la "L". Por ejemplo, si ejecutamos: `Ele3(Norte)` dibuja una clásica "L", y si ejecutamos: `Ele3(Oeste)` dibuja una "L" acostada, mirando hacia arriba. El casillero inicial es la esquina de la L, y el cabezal debe volver a la posición inicial. Por ejemplo, `Ele3(Oeste)` produce lo siguiente:
![ele.png](/img/2016-04-07/ele.png)
