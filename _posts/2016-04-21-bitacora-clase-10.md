---
layout:     post
title:      'Repetición Condicional'
subtitle:   "Bitácora de la clase del jueves 21/04/2016"
date:       2016-04-21 23:30:00
author:     "Alf"
---

### Repaso de Funciones

Rehicimos el ejercicio de escapando del incendio:

![modificoIncendio.jpg](/img/2016-04-21/modificoIncendio.jpg)

```gbs

procedure AvanzarUnPaso(){
  if(hayIncendioAlEste()){
    MoverTipito(Norte)
  } else {
    MoverTipito(Este)
  }
}

procedure MoverTipito(dir){
  Sacar(Negro)
  Mover(dir)
  Poner(Negro)
}

function hayIncendioAlEste(){
  Mover(Este)
  return (hayIncendio())
}

function hayIncendio(){
  return (hayBolitas(colorFuego()))
}

function colorFuego(){
  return (Rojo)
}

```
Es importante que puedan hacer funciones como:
* `hayIncendioAlEste`
* `hayIncendio` ¡no vale usar `nroBolitas(Rojo)` directamente!
* `colorFuego` ¡no vale poner `Rojo` en todos lados!

### While (Repetición condicional)
Si ahora queremos **escapar por completo** del tablero, necesitamos saber el tamaño del tablero, ¿no?.... ¡NO! Podemos usar un _repeat_ que _en vez de tomar un número, toma una condición_.

Entonces, queda:

```
program {
  while(puedoMover(Este)){
    AvanzarUnPaso()
  }
}
```

¡Y listo! Eso **repite mientras se cumpla** que se puede mover al Este. En cuanto deja de cumplirse... ¡para!.

La estructura del `while` (que es nuestra _repetición condicional_), entonces, es así:

 ![while.jpg](/img/2016-04-21/while.jpg)

Hicimos el ejercicio `LimpiarHacia(dir)`, que limpiaba tooodas las celdas en la dirección indicada:

![limpiar.jpg](/img/2016-04-21/limpiar.jpg)

#### La Montaña
Hay una montaña (representada por bolitas azules), cuya ladera tiene sectores verticales.
El escalador (representado por una bolita negra), debe escalar la montaña, y también puede hacer túneles y encontrar oro.

1. Definir el procedimiento `EncontrarSaliente`, que hace que hace que el escalador se mueva hacia el norte siguiendo la montaña (nunca parado en una casilla de la montaña, sino de costado) hasta encontrarse con una saliente hacia el Este, y se sube y se frena ahí a descansar. Ejemplo de tablero inicial y final:

 ![saliente1.jpg](/img/2016-04-21/saliente1.png) ![saliente2.jpg](/img/2016-04-21/saliente2.png)

 (Debe funcionar para **cualquier montaña**, por alta que sea)

2. Definir el procedimiento `CavarTunel(dir)`, que cava un túnel (saca bolitas de montaña) desde donde está parado el escalador, en línea recta y hasta que **se acabe la montaña**, que puede ser:
* bien porque salí del otro lado de la montaña
* o bien porque llegué al fin del tablero.

3. Estos van de yapa para que practiquen: Definir la función `hayOroAl(dir)`, que busca oro (representado por bolitas rojas) en esa dirección, y denota si en esa "línea" hay oro ó no. No hace falta mover al escalador, se puede sólo mover el cabezal. Por ejemplo, en el siguiente tablero `hayOroAl(Este)` denota `True`, pero `hayOroAl(Sur)` denota `False`.

![veta.jpg](/img/2016-04-21/veta.png)

4. Definir el predicado `RecogerOroDeVeta(dir)`, que recoge todo el oro de una veta sobre la que está el cabezal. `dir` me dice si la veta es vertical ú horizontal: `Norte` implica que la veta es **vertical**, y `Este` que la veta es **horizontal**. Acá tampoco hace falta mover al escalador, supongamos que el cabezal es su robot minero. El escalador se queda donde está. El cabezal debe volver al origen.
Por ejemplo, si hago`RecogerOroDeVeta(Norte)` en este tablero:

![recojo1.jpg](/img/2016-04-21/recojo1.png)

Obtengo este otro tablero:

![recojo2.jpg](/img/2016-04-21/recojo2.png)

_Precondición: el cabezal ya está sobre una veta, y el escalador está en esa misma celda_

#### Soluciones ejs 1 y 2

![solucion1.jpg](/img/2016-04-21/solucion1.jpg)

¡Saludos!

Alf
