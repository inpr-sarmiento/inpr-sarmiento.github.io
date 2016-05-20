---
layout:     post
title:      'Registros'
subtitle:   "Bitácora de la clase del jueves 19/05/2016"
date:       2016-05-20 10:00:00
author:     "Alf"
---

### Enunciados que guiaron la clase

1. Hacer la función `doble(numero)`, que recibe un número y denota el doble del mismo.
2. Hacer la función `max(nro1,nro2)`, que denota el máximo entre ambos números.
3. Hacer la función `dobleDelMaximo(nro1,nro2)`, que denota el doble del máximo entre ambos números.
4. Hacer la función `quienGano`, que denota el color del equipo ganador de un partido.
En un partido juegan dos equipos (hay dos colores) y cada uno mete una cantidad de goles.
_Para pensar: ¿Cuántos parámetros debe recibir la función?_, pero también, _¿Cuántas cosas necesito?_.
5. Hacer la función `diferenciaDeGoles`, que recibe un partido y denota la diferencia de goles.
6. Hacer la función `jugoEn(colorEquipo,partido)`, que dice si el equipo indicado jugó en ese partido.
7. Hacer la función `puntosDe(colorEquipo,partido)`, que dice cuántos puntos sacó.
Recordemos que en un campeonato de fútbol, los puntos en un partido son: si el equipo ganó,
tiene 3 puntos. Si empató tiene 1 punto, y si perdió tiene 0 puntos.
8. Ahora juguemos con un tipo `Fecha`, que tiene día, mes y año: hacer la función `esPrimerCuatri(fecha)`,
que dice si esa fecha es del primer cuatrimestre.
9. Hacer la función `esNavidad(fecha)` que dice si esa fecha es el 25 de diciembre.

### Repaso de variables y funciones

Bueno, en principio arrancamos con los primeros tres ejercicios.

```gbs
function doble(numero){
  return (2*numero)
}
function max(nro1,nro2){
  maximo := nro1
  if(nro2 > nro1){
    maximo := nro2
  }
  return (maximo)
}
```

Ahora bien, al llegar al tercer punto, esta es una solución **incorrecta**:

```
function dobleDelMaximo(nro1,nro2){
  maximo := nro1
  if(nro2 > nro1){
    maximo := nro2
  }
  return (2*maximo)
}
```

Porque hay que reutilizar las funciones de arriba. Recordemos que si primero quiero hacer
el max, y luego quiero hacer el doble, puedo **usar la función max** y **mandarle el resultado
a la función doble**.

Eso se hace así:

![dobleMax.jpg](/img/2016-05-19/dobleMax.jpg)

Y si yo quisiera saber _"el cuadrado del doble del máximo"_, eso se hace así: `cuadrado(doble(max(nro1,nro2)))`. ¿Se entiende cómo se van pasando los valores a cada función?

### Intro a Registros

Ahora nos topamos con el punto 4:

> Hacer la función `quienGano`, que denota el color del equipo ganador de un partido.
En un partido juegan dos equipos (hay dos colores) y cada uno mete una cantidad de goles.
_Para pensar: ¿Cuántos parámetros debe recibir la función?_, pero también, _¿Cuántas cosas necesito?_.

Con lo que sabemos hasta ahora, para poder hacer `quienGano` necesitamos 4 parámetros: el color y los goles que metió el equipo 1, y el color y los goles del equipo 2.

Entonces, podríamos por ejemplo hacer estas pruebas en el program:

![usoQuienGano.jpg](/img/2016-05-19/usoQuienGano.jpg)

Y para eso la función queda definida así:

![quienGano.jpg](/img/2016-05-19/quienGano.jpg)

Ahora bien, nos hacemos la pregunta: **¿Dónde está el partido?**.

El _partido_ está representado por esos cuatro datos: `colorEq1`, `colorEq2`, `goles1` y `goles2`.

Lo que aprendimos hoy es que los lenguajes de programación tienen siempre una forma de crear **mi propio tipo** para hacer que nuestra función reciba sólo **una cosa**, ó sea, **un partido** entero, y no desmembrado.

### Un poco de teoría

![mapaTipos.jpg](/img/2016-05-19/mapaTipos.jpg)

Se llaman **estructuras de datos** a los datos que están **compuestos** por otros datos. En nuestro caso,
los partidos están compuestos por colores y números. Pero podríamos tener también **fechas**, que van
a estar compuestas por día, mes y año, ó también podríamos tener calles, que pueden tener altura y sentido.

Para crear nuestro propio tipo **Partido** (lo vamos a escribir con **mayúscula**), vamos a necesitar
poner _arriba de todo_ en nuestro archivo lo siguiente:

```gbs
type Partido is record {
  field colorEq1
  field colorEq2
  field cantGolesEq1
  field cantGolesEq2
}
```

Fíjense que se llaman **campos** a cada una de las **componentes de un registro**. Cada componente tiene un nombre.

Ahora que tenemos eso en nuestro archivo, en nuestro program debo **crear** el partido. Para **crear** el partido, se escribe `Partido(....)` y ahí en el medio se pone lo que tiene el partido adentro, separado por comas, y con una notación medio extraña, que es así: `nombreDelCampo <- valor`. Eso significa que en ese campo, el registro tendrá ese valor.

Rápidamente un ejemplo para no confundirnos:

```gbs
program {
  boliviaArgentina := Partido(colorEq1 <- Verde, colorEq2 <- Azul, cantGolesEq1 <- 6, cantGolesEq2 <- 1)
  riverBoca := Partido(colorEq1 <- Verde, colorEq2 <- Azul, cantGolesEq1 <- 6, cantGolesEq2 <- 1)
}
```

Ahí hemos creado dos partidos, y los metimos cada uno en una variable distinta. ¡Todo el partido entra dentro de una variable!

Ahora podemos usarlo para pasarle a `quienGano` **sólo una cosa**:

```gbs
program {
  boliviaArgentina := Partido(colorEq1 <- Verde, colorEq2 <- Azul, cantGolesEq1 <- 6, cantGolesEq2 <- 1)
  riverBoca := Partido(colorEq1 <- Verde, colorEq2 <- Azul, cantGolesEq1 <- 6, cantGolesEq2 <- 1)
  return(quienGano(boliviaArgentina))
}
```

Ahora veamos cómo cambia `quienGano`:

```gbs
function quienGano(elPartido){
  ganador := colorEq1(elPartido)
  if(cantGolesEq2(elPartido) > cantGolesEq1(elPartido)){
    ganador := colorEq2(elPartido)
  }
  return (ganador)
}
```

Notar que la _estrategia_ y el _algoritmo_ son exactamente los mismos que en nuestra primer versión de quienGano. Pero hay algo diferente:

Antes `colorEq1` llegaba por parámetro. Pero ahora ¡Por parámetro llega `elPartido`!

**¿Dónde está colorEq1?** -> Está **dentro del partido**.

Lo que es interesante de saber, es que cuando escribimo `type Partido is record {...` **se generan automáticamente cuatro funciones** que me permiten **acceder** al registro:

* La función `colorEq1(partido)`, que _saca_ el color del equipo 1 _de adentro_ del partido, y me devuelve ese color.
* La función `colorEq2(partido)`, que _saca_ el color del equipo 2 _de adentro_ del partido, y me devuelve ese color.
* La función `cantGolesEq1(partido)`, que _saca_ el la cantidad de goles del equipo 1 _de adentro_ del partido, y me devuelve ese número.
* La función `cantGolesEq2(partido)`, que _saca_ la cantidad de goles del equipo 2 _de adentro_ del partido, y me devuelve ese número.

¡No hace falta codificarlas, ya me las dan!. Estas funciones se denominan **accessors** ó **proyectores** de un registro. Fíjense que esas funciones **tienen el mismo nombre que el nombre de las componentes**.

Entonces, así se explica por qué ahora tengo que poner:

`ganador := colorEq1(elPartido)`

en lugar de:

`ganador := colorEq1`.

Eso es porque ¡Tengo que _sacar_ el colorEq1 de _adentro_ del partido! Y usando las funciones que me dan, puedo hacerlo. Volvé a leer el código de arriba, de la función `quienGano(partido)`, que vas a ver cómo estamos usando esas cuatro funciones para acceder a las cosas que están dentro del partido.

### Más práctica

> Hacer la función `diferenciaDeGoles`, que recibe un partido y denota la diferencia de goles.

```gbs
function diferenciaDeGoles(unPartido){
  return (cantGolesEq1(unPartido) - cantGolesEq2(unPartido))
}
```

> Hacer la función `jugoEn(colorEquipo,partido)`, que dice si el equipo indicado jugó en ese partido.

```gbs
function jugoEn(colorEquipo,partido){
  return (colorEquipo == colorEq1(partido) || colorEquipo == colorEq2(partido))
}
```

> Hacer la función `puntosDe(colorEquipo,partido)`, que dice cuántos puntos sacó.
Recordemos que en un campeonato de fútbol, los puntos en un partido son: si el equipo ganó,
tiene 3 puntos. Si empató tiene 1 punto, y si perdió tiene 0 puntos.

```gbs
function puntosDe(colorEquipo,partido){
  puntos := 0
  if(gano(colorEquipo,partido)){
    puntos := 3
  }
  if(empato(partido)){
    puntos := 1
  }
  return (puntos)
}
```

**¡Delegamos!** en funciones auxiliares. ¡No olvidarse de dividir en subtareas!

```gbs
function gano(colorEquipo,partido){
  return (colorEquipo == quienGano(partido))
}
function empato(partido){
  return (diferenciaDeGoles(partido)==0)
}
```

En la sección de [material](/material/) les acabo de subir:

* los [apuntes teóricos de la UNQ](/assets/material/Practica7-Registros.pdf)
* la [Práctica de registros de la UNQ](/assets/material/Practica7-Registros.pdf), para que tengan ejercicios para practicar.

### Tarea

* De tarea les han quedado los puntos que no llegaron a hacer. No se entrega por mail,
sino que se lleva hecho a clase para mirarlo con Fede.
