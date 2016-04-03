---
layout:     post
title:      'Repetición Simple (o sea "repeat")'
subtitle:   "Bitácora de la clase del jueves 31/03/2016"
date:       2016-04-03 17:48:00
author:     "Alf"
---

La clase del jueves se enfocó en aprender a usar una nueva herramienta: la **repetición simple**.
En gobstones, esto lo conocemos como `repeat`.

### Motivación

Hicimos un procedimiento Poner37Verdes, que hace justamente eso, poner 37 bolitas verdes en el casillero actual. Para ello, no escribimos 37 veces el `Poner` , sino que usamos el `repeat`, que es la nueva herramienta que tenemos.

```gbs
program {
  Poner37Verdes()
}

procedure Poner37Verdes(){
    repeat(37){
      Poner(Verde)
    }
}
```

![repetir.png](/img/2016-03-31/repetir.png)

Dijimos también que la repetición simple cambia el **flujo de ejecución**. Antes era recto, lineal (una línea atrás de la otra), y ahora, cuando aparece un `repetir`, aparece lo que se llama un **ciclo**.

![flujoRepeat.png](/img/2016-03-31/flujoRepeat.png)


## Jugando un poco
**A.** Hacer un procedimiento `Poner10AlLado`, que pone 10 bolitas Negras, todas en el casillero que está al Este del casillero actual.

**B.** Hacer un procedimiento `PonerLejos` que ponga 1 bolita Negra 7 casilleros al Este, y vuelva a la posición original.

> Estos dos ejercicios A y B nos sirvieron para entender que se pueden poner instrucciones antes y después del repeat.

**C.** Teniendo en cuenta este tablero inicial:

![tinicial.png](/img/2016-03-31/tinicial.png)

Hacer corresponder estos 4 programas con sus tableros finales:

<table><tr>
<td>
  program {
    Poner(Azul)
    repeat(3){
      Mover(Norte)
    }
  }
</td>
<td>
  program {
    repeat(3){
      Poner(Azul)
    }
    Mover(Norte)
  }
</td>
<td>
  program {
    repeat(3){
      Poner(Azul)
      Mover(Norte)
    }
  }
</td>
<td>
  program {
    repeat(3){
      Mover(Norte)
      Poner(Azul)
    }
  }
</td>
</tr></table>

**Desordenadas**:
![tFinal1.png](/img/2016-03-31/tFinal1.png) ![tFinal2.png](/img/2016-03-31/tFinal2.png) ![tFinal3.png](/img/2016-03-31/tFinal3.png) ![tFinal4.png](/img/2016-03-31/tFinal4.png)

> En este ejercicio vimos, sobretodo con los últimos dos programas, que **sigue importando el orden** de las instrucciones _dentro_ del repeat así como ya importaba _fuera_.
>
> ![orden.png](/img/2016-03-31/orden.png)

## El cuadrado ahora es fácil

**D.** Hacer el procedimiento `Cuadrado5x5Negro`, que dibuja un cuadrado de esas medidas, relleno, todo con una bolita negra en cada casillero.

![cuadrado.png](/img/2016-03-31/cuadrado.png)

Se nos ocurrieron **dos posibles estrategias**.
* La primera, hacer un zigzag hacia arriba. Como si fuera una impresora, imprimo hacia el Este, subo, e imprimo hacia el Oeste, y así.
* La segunda estrategia es la que elegimos, porque **aprovecha que algo se repita**. Es así: Dibujo una línea, vuelvo sin dibujar, y subo. Y así.


```gbs
procedure Cuadrado5x5Negro() {
  repeat(5){
    HacerLinea5()
    MoverOeste5()
    Mover(Norte)
  }
}

procedure HacerLinea5(){
  repeat(5){
    Poner(Negro)
    Mover(Este)
  }
}

procedure MoverOeste5(){
  repeat(5){
    Mover(Oeste)
  }
}
```

> **BOOM! Tu tablero no es suficientemente grande...**
Muchos intentaron hacer el cuadrado _en un tablero de 5x5_, pero tenían el problema de que en su estrategia _el cabezal necesitaba un casillero más_, porque se pasaba.
> **Mucho cuidado con esto**. Con Fede el Martes van a profundizar esto, que les adelanto, se llama _caso borde_.


## Más ejercitación
**E.** Hacer el procedimiento `Diagonal4x23()`, que haga lo siguiente con bolitas azules:

![23.png](/img/2016-03-31/23.png)

**F.** Hacer el procedimiento `MoverN(cant,direccion)` que mueva el cabezal tantas veces como se indique en la dirección que se indique

**G.** Hacer el procedimiento `PonerN(cant,color)` que ponga en la celda actual tantas bolitas como indique cant, del color indicado.

**H.**  Hacer _de nuevo_ el ejercicio E, pero ahora haciendo que `Diagonal4x23()` **use** el procedimiento `PonerN(...)`.

**I.** Hacer el procedimiento `LineaVa(long, dir, color)` para que dibuje  una "línea" de bolitas en la dirección `dir`, del `color` indicado y de la `longitud` indicada.

**J.** Hacer _nuevamente_ el ejercicio que hicieron con Fede de `ContornoYRelleno()`, para que **use** los procedimientos anteriores donde convenga.

### Nombres de las variables

Hicimos un pequeño apartado en el que hablamos sobre los nombres.
Por ejemplo, si quiero

| Si queremos | Le ponemos | Pero no le ponemos | y tampoco |
|---|---|
| Un procedimiento que se llame "Mover hacia arriba" |  `MoverHaciaArriba` | `Moverhaciaarriba` (porque debemos  separar visualmente las palabras) |  `moverHaciaArriba` (porque un procedimiento debe empezar con mayúscula) |
| Un parámetro que se llame "cantidad de pasos" |  `cantidadDePasos` | `cantidaddepasos` (porque debemos  separar visualmente las palabras)  | `CantidadDePasos`  (porque los parámetros comienzan con minúscula) |

### Tarea

* Enviar el _Ejercicio I y el ejercicio J_ hechos en Gobstones, por mail a sus docentes amigos. La fecha de entrega es **el martes**. Con esta fecha somos rígidos porque es tarea que se dio el Jueves.
* Ya está lista la [nueva guía de repetición simple](http://inpr-sarmiento.mumuki.io/guides/34-fundamentos-repeticion-simple). La idea es que la hagan para el jueves que viene entera.
