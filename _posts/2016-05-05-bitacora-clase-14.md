---
layout:     post
title:      'Práctica Integradora'
subtitle:   "Bitácora de la clase del jueves 05/05/2016"
date:       2016-05-05 23:30:00
author:     "Alf"
---

### Repaso de variables

Buenas!

Antes que nada, recuerden que les subí el nuevo **machete oficial** (v1.1) en la sección de [material](/material/).

Hoy continuamos con los ejercicios que dejó Fede de la Guía 5:

* Ejercicio 6: `nroBolitasAlSiHay(dir,col)`
* Ejercicio 7: `nroBolitasEnVecinas(col)`
* Ejercicio 8: `nroBolitasYoYMisVecinos(col)`

![bolitasVecinas.jpg](/img/2016-05-05/bolitasVecinas.jpg)

Varios se equivocaron e intentaron poner `&&` en vez de `+`.  Vimos que esto era porque **no están pensando en qué me piden**. Recuerden siempre tenerlo en cuenta. En la bitácora del jueves pasado, les puse que lo que necesito saber para resolver un ejercicio es:

* Saber si me piden un _programa_, un _procedimiento_ ó una _función_.
* Entender _qué parámetros entran_ y, si es una función, el _tipo_ de que retorna.
* Por supuesto, lo importante, entender **qué me piden**, ó sea, qué significa el procedimiento ó la función. ¡Hay que tenerlo en la cabeza todo el tiempo!
* Recién después pensar una **estrategia**, se puede bocetar por arriba con código "de mentirita"
* Y recién después, tirarse a codificar bien.

#### Ejercicio adicional de variables:

Además, hicimos este ejercicio adicional:

![variables.jpg](/img/2016-05-05/variables.jpg)

En azul se ve la solución. La idea era hacer el seguimiento de cómo iban quedando las variables a medida que el programa avanza.

### Más Apuestas

Después, continuamos con la guía 5, que tiene la segunda parte de el ejercicio de Apuestas de la guía 4. Hicimos hasta el ejercicio 5 inclusive, y para esos últimos dos ejercicios hicimos una puesta en común.

* Ejercicio 1: `cuantosApostaronA(nroApostado)`
* Ejercicio 2: `cuantaPlataSeApostoA(nroApostado)`
* Ejercicio 3: `cuantaPlataAposto(nroJugador)`
* Ejercicio 4: `algunJugadorApostoMasDe(nroApostado,minimo)`
* Ejercicio 5: `algunJugadorApostoEnTotalMasDe(minimo)`

Les transcribo la solución del ejercicio 2, `cuantaPlataSeApostoA(nroApostado)`.

```gbs
function cuantaPlataSeApostoA(nroApostado){
  plata := 0
  IrAlOrigen()
  while(haySiguiente){
    if(hayApuestaA(nro)){
      plata := plata + montoApostado()
    }
    IrAlSiguiente
  }
  # ¡Caso borde! En la última celda debemos volver a chequear si hay que sumar el monto...
  if(hayApuestaA(nro)){
    plata := plata + montoApostado()
  }

  return (plata)
}

function hayApuestaA(nro){
  return (nroApostado() == nro)
}

function nroApostado(){
  return (nroBolitas(colorNumero()))
}

function montoApostado(){
  return (nroBolitas(colorMonto()))
}
```

Acá es importante notar la **estrategia de recorrido completo**:
```
while( puedo dar un paso ){
  procesar la celda actual
  dar un paso
}
procesar la celda actual
```

Notar el **caso borde** al final, necesario como se necesitaba en el repeat.

Les paso la solución de los ejercicios 4 y 5 que hicimos en el pizarrón:

![Apuestas4y5.jpg](/img/2016-05-05/Apuestas4y5.jpg)

Acá, en estos dos puntos, como justo estaba la estrategia de **búsqueda**, la refrescamos. Notar que la estrategia en ambos puntos, 4 y 5, se repite:

```
while( puedo dar un paso && no encontré ){
  dar un paso
}
```

Esta es una forma muy válida de pensar una **estrategia**. No siempre van a ser búsquedas, pero este _pseudocódigo_ me puede ayudar a pensar lo importante sin concentrarme en detalles.

### Tarea / Avisos parroquiales

* Hacer el parcial de los gusanitos **En lápiz y papel**. Llevarlo completo la clase del martes.
* El jueves lleguen 17hs puntuales, Santi les va a estar entregando el enunciado del parcial. Ese día no hace falta traer las notebooks.
