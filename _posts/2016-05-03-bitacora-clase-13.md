---
layout:     post
title:      'Más recorridos + intro variables'
subtitle:   "Bitácora de la clase del martes 03/05/2016"
date:       2016-05-03 23:00:00
author:     "Fede"
---

### Metodología Alf para la resolución de problemas complejos
Nos hacemos las cuatro preguntas:

* ¿Nos piden un **programa** (raro a esta altura), una **función** ó un **procedimiento**?
* En caso de que sea una función, ¿qué **tipo** denota? Recordemos que los tipos posibles en Gobstones son: **número**, **color**, **dirección** y **booleano**.
* ¿Qué tiene que **hacer**? Ojo acá con los casos borde.
* ¿Qué **estrategia** vamos a seguir? Vale pensar: ¿se parece a alguno de los esquemas (búsqueda, recorrido de tablero completo, etc) con los que ya trabajamos?

### Seguimos con las apuestas
**Ejercicio 2.** 
Respondamos las preguntas:

1. Es un procedimiento.
2. No aplica.
3. Recorrer toda la mesa, haciendo lo que corresponda con cada apuesta.
4. Como el tablero puede estar lleno de apuestas, hay que recorrerlo por completo: eso ya vimos cómo hacerlo. Pensemos ahora lo que hay que hacer en cada celda:

* Lo primero, ver si efectivamente hay alguna apuesta.
* Si la hay, decidir si ganó o perdió, esto se logra mirando el número apostado.
* Si corresponde, `Pagar()`: paga 5 veces el monto de la apuesta.
* Si no, `Cobrar()`: se queda con todo lo apostado.

```gbs
procedure PagarYCobrar(nroQueSalio) {
  IrAlInicio()
  while (haySiguiente()) {
    if (hayApuesta()) {
      ProcesarApuesta(nroQueSalio)
    }
    IrAlSiguiente()
  }
}

procedure ProcesarApuesta(nroQueSalio) {
  if (esApuestaGanadora(nroQueSalio)) {
    Pagar()
  } else {
    Cobrar()
  }
}
```

### La necesidad de recordar
Teniendo en cuenta la restricción de _el `return` tiene que estar en la última línea_, ¿cómo hacemos para que una función retorne cosas diferentes? Ejemplos de esto son: ¿de qué bando hay más soldados? ¿hacía qué dirección hay un superior? ¿qué número es más grande entre a y b?

Surge así la necesidad de **recordar** valores en algún lado, para poder usarlos más tarde o incluso para poder modificarlos (por ejemplo, para contar algo o hacer una suma de muchas cosas). Básicamente, lo que hacemos es **darle un nombre** a un valor, para poder utilizarlo más tarde en otro punto del programa.

Como ejemplo, pensemos SIN EJECUTARLO EN GOBSTONES cuántas bolitas rojas pone cada uno de estos programas:

```gbs
program {
  numerito := 2
  PonerN(numerito, Rojo)
}
```

```gbs
program {
  numerito := 2
  numerito := 5
  PonerN(numerito, Rojo)
}
```

```gbs
program {
  numerito := 2
  numerito := numerito + 2
  PonerN(numerito, Rojo)
}
```

A estos nombres, que se escriben con minúscula inicial y son también expresiones, los llamaremos **variables**. Algunos tips para tener en cuenta:

* a la acción de darle un valor la conocemos como **asignación**: _asigno el valor 5 a la variable `numerito`_;
* podemos hacer tantas asignaciones como querramos, cada una sobreescribe (pisa) a la anterior;
* si intento usar una variable a la cual nunca le asigné un valor: ¡BOOM!