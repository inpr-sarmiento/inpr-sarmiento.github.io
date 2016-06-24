---
layout:     post
title:      'Recorridos con while'
subtitle:   "Bitácora de la clase del martes 26/04/2016"
date:       2016-04-26 22:30:00
author:     "Fede"
---

### Distribución de mercadería

1. Fácil
2. Búsqueda - fácil, usar las funciones de 1
3. Búsqueda, hay que usar `opuesto`, usar las funciones de 1
4. Usar 2 y 3 + un `if` y una función para ver si hay suficiente
5. Idem 4
6. Combinación de 4 y 5
7. No lo hacemos - necesita recorrer el tablero
8. Función de búsqueda con retorno
9. Combinación del anterior

### Unitarios y federales
Vamos a usar el tablero para representar un campo de batalla, donde intervienen dos ejércitos: los unitarios (representados con bolitas azules) y los federales (representados con bolitas rojas). 

En cada celda puede haber o no combatientes, y de cada uno de ellos nos va a interesar conocer su rango. Los rangos están representados por la cantidad de bolitas de colores, respetando la siguiente codificación:

|Cant. bolitas|Rango|
|:---:|---|
|1|Soldado raso|
|2|Teniente|
|3|Capitán|
|4|Comandante|

#### Parte 1: inteligencia

Lo primero que vamos a necesitar es una serie de funciones que nos sirvan para "hacer inteligencia" sobre el campo de batalla. 

1. `haySoldado()` que indica si hay algún soldado en la celda actual.
1. `rangoSoldado(colorEjercito)` que indica el rango del soldado perteneciente al ejército dado que hay en la celda actual.
1. `haySoldadoHacia(dir)` que indica si hay algún soldado en dirección `dir`.
1. `gradoSoldadoMasCercano(dir, colorEjercito)` que devuelve el grado del soldado más cercano en dirección `dir`, perteneciente al ejército correspondiente.
1. `haySoldadoALaVista(dir, colorEjercito)` que indica si hay algún soldado de ese ejército a la vista, o sea: si miramos en línea recta hacia `dir` lo primero que vemos es un soldado de ese color.
1. `haySuperiorALaVista(dir, colorEjercito)` que indica si hay algún superior a la vista en esa dirección. Para saber si hay un superior, hay que comparar con el rango del soldado que está en la celda actual (se puede asumir que hay uno). Si en el trayecto hacia el superior hay algún enemigo, la función debería devolver `False`. 
**Ayudín:** lo primero que hay que mirar es si hay un soldado de mi bando a la vista en la dirección requerida.
1. `puedeAvanzarHacia(colorEjercito, dirAvance)` que indica si un soldado ubicado en la celda actual podría avanzar en una dirección dada. Para poder avanzar, es necesario que haya aliados a mis costados: por ejemplo para poder moverme al `Norte` tiene que haber un soldado de mi mismo bando hacia el `Este` y hacia el `Oeste`. 
**Ayudín:** revisar las funciones del machete que trabajan con direcciones.

#### Parte 2: estrategia

En esta segunda parte nos vamos a encargar de mover distintos soldados por el campo de batalla. 

1. `MoverSoldado(colorEjercito, dir)` que mueva al soldado de la celda actual en la dirección dada. **Ayudín:** como no sabemos el rango del soldado, una vez que nos movamos no sabremos cuántas bolitas había en la posición original. El truco acá es construir primero otro procedimiento `MoverBolitas(color, cantidad, direccion)` y con ese definir el que se pide.
1. `AvanzarLoQuePuedaHacia(colorEjercito, dirAvance)` que avance al soldado de la celda actual todo lo que pueda en la dirección dada, teniendo en cuenta lo ya mencionado sobre los movimientos de los soldados.
1. `ReportarseConSuperiorHacia(colorEjercito, dir)` asumiendo que hay un superior en la dirección dada, avanzar hasta quedar al lado de él.
1. `ReportarseConSuperior(colorEjercito)` asumiendo que hay un superior en alguna de las cuatro direcciones, avanzar hasta quedar al lado de él.