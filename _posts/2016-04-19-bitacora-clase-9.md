---
layout:     post
title:      'Funciones'
subtitle:   "Bitácora de la clase del martes 19/04/2016"
date:       2016-04-19 23:30:00
author:     "Fede"
---

### La importancia de nombrar las cosas

La semana anterior estuvieron hablando con Alf sobre qué importante es **ponerle nombre** a las partes de nuestro problema y que esos nombres aparezcan en nuestro programa. Eso nos ayuda en varios aspectos:

* sólo mirando el código podemos entender de qué va nuestro problema, lo que **reduce la distancia** entre el problema real y el programa que lo resuelve;
* al **olvidarnos de las bolitas**, el universo de problemas que podemos resolver es mucho más grande;
* nos "despegamos" de la **representación**, haciendo que la misma sea más fácil de cambiar.

Todo muy lindo, pero con lo que sabemos hasta ahora se nos está escapando la tortuga... veamos un ejemplo. 

En el ejercicio **El bosque** de la guía 3, se pedía lo siguiente:

> Escribir el procedimiento `Germinar()`, que transforma una semilla en planta en la celda actual. La germinación consume tres unidades de nutrientes. Si en la celda no hay semilla, o no hay suficientes nutrientes, no se hace nada.

y nosotros propusimos esta solución:

```gbs
procedure Germinar() {
  if (hayBolitas(Rojo) && nroBolitas(Azul) >= 3) {
    TransformarSemillaEnArbol()
  }
}
```

Se ve que los conceptos de "hay semilla" y "hay suficientes nutrientes" que estaban en la definición del problema _se perdieron_ en la representación: nuestro procedimiento sólo  habla de bolitas de colores. Pero también se ve que con lo aprendido hasta ahora no podemos mejorarlo, ya que lo que necesitamos es poder **crear nuestras propias expresiones**. ¿Y entonces qué hacemos? :fearful:

### Funciones, ¡al poder! :fist:

Vamos a sumar a unas nuevas invitadas a nuestra fiesta de la programación: las **funciones**. En cierta forma, podemos decir que son primas de los procedimientos, pero tienen una diferencia fundamental, **siempre nos dan algo**. Pensemos en las funciones que conocemos hasta ahora: 

|Nombre|¿Qué nos da?|
|------|------------|
|`nroBolitas(color)`|Un número|
|`puedeMover(dir)`|Un booleano (V/F)|
|`hayBolitas(color)`|Un booleano (V/F)|

A este "algo" que "nos dan" las funciones lo solemos llamar, más formalmente, **valor de retorno**, y decimos que una función **denota**, **devuelve** o **retorna** un valor. Si miramos la tablita también podemos reconocer que estos valores en el universo Gobstones pueden ser de distintos **tipos**: números, booleanos y colores (ok, no está en la tabla, pero creanmé que también se puede).

¡Basta de charla! Empecemos a mejorar el código de `Germinar()`. Lo primero que vamos a querer hacer es una función `colorSemillas()`, para poder poner ahí el color que elegimos para representarlas. 

```gbs
function colorSemillas() {
  return (Rojo)
}
```

Veamos un poco la sintaxis de esto:

* la primera línea es similar a la definición de un `procedure`, sólo que acá la palabra clave es `function` y **el nombre empieza con una minúscula** (como ya habíamos visto que pasaba con las expresiones primitivas y los parámetros). Podemos tener también parámetros en las funciones, de hecho todas las que habíamos visto los tenían, aunque en este caso no hay ninguno;
* la última línea (y única en este caso) tiene otra palabrita nueva: el `return`. Básicamente, eso se lee como _"devolvé Rojo"_ y **siempre** nuestras funciones tienen que tener exactamente un `return`, el cual debe estar en la **última línea** de la definición. Entre los paréntesis va aquello que querramos que nuestra función retorne, que en este caso es simplemente `Rojo`.

Para ejercitarlo, releimos el enunciado de "El bosque" y propusimos funciones que nos ayudaran a abstraer aún más el problema. Más o menos entre todos salieron las siguientes:

* `cantidadNutrientes()`
* `cantidadArboles()`
* `hayNutrientesNecesarios()`

De ahora en adelante, ya no vale usar `hayBolitas` o `nroBolitas` cuando podamos en su lugar escribir una función que abstraiga nuestro problema.

### Las invitadas ideales

Volviendo a nuestra metáfora de la fiesta de la programación, las funciones tienen otro aspecto importantísimo en el cual se diferencian de los procedimientos: antes de irse, limpian todo y **lo dejan igual que como lo encontraron** (quién pudiera tener invitados así...).

Pero qué mejor que comprobarlo uno mismo, volvamos por un rato al mundo de las bolitas y escribamos la función `hayBolitasAl(dir, color)`, que nos indica si hay alguna bolita del color dado en la celda vecina correspondiente. Importante: **el cabezal tiene que quedar donde empezó**.

Antes de largarnos a implementarla, vamos a ver un truquito para poder probarlas, ya que ahora lo que nos interesa no es mirar el tablero sino el retorno. Como hacíamos antes, se puede escribir un `program`, pero esta vez agregándole un `return` al final.

```gbs
program {
  return (miFuncionLoca())
}
```

Luego, podemos ver el valor en la pestaña **Valores de retorno**.

Ahora sí, hagamos la función. Probablemente lo primero que surja es esta solución:

```gbs
function hayBolitasAl(dir, color) {
  Mover(dir)
  return (hayBolitas(color))
}
```

Pero, si el `return` tiene que ser la última línea entonces ¿cómo hago para volver? El punto es que no hace falta, porque como dijimos recién las funciones son limpias o **puras**, en el sentido de que al terminar **deshacen los efectos** producidos sobre el tablero.

* Ejercitamos todo esto haciendo todos los ejercicios de la página 2, guía 4.
* Quedaron como tarea los ejercicios del 10 al 14 de Farmville (o sea, los que piden funciones).