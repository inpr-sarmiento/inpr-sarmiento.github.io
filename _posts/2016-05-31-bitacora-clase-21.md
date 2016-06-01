---
layout:     post
title:      'Listas: construcción, proyección y recorrido con while'
subtitle:   "Bitácora de la clase del martes 31/05/2016"
date:       2016-05-31 12:00:00
author:     "Fede"
---

### Objetivos de la clase

* Introducir la noción de listas, como **secuencia ordenada de elementos del mismo tipo**.
* Contar que en Gobstones las listas también son **inmutables**.
* Mostrar cómo **construirlas**, con el literal `[]` y la concatenación `++`.
* Mostrar cómo **proyectarlas**, usando `head`, `tail`, `last` e `init`.
* Ver cómo **recorrer** una lista usando `while`.

### Constructores y proyectores

Las tres diferencias entre listas y registros:

* Un tipo de registro tiene una **cantidad fija** y definida de componentes. P.ej. el tipo de registro Partido tiene 5 componentes, Fecha tiene 3. Una lista puede tener **la cantidad de elementos que uno quiera**: puede haber una lista con 3 números, una con 5 números y otra con 8 números, y son todas listas de números.
* Cada componente de un registro tiene un nombre, que es el mismo nombre del proyector correspondiente. **Los elementos de una lista no tienen cada uno un nombre**, y por lo tanto no es posible acceder **directamente** al que yo quiera (ya veremos que sí podemos programarlo nosotros).
* En un mismo registro puede haber componentes de distinto tipo. P.ej. en un Partido tengo cuatro números y una Fecha. Todos los elementos de una misma lista tienen que ser del mismo tipo. Si una lista es de números, tienen que ser todos números. Puede haber listas de distinto tipo, p.ej. una lista de números, una de direcciones y otra de registros Partido, lo que no vale es que **en la misma lista** haya p.ej. un número y una dirección.

Vimos cómo construirla con `[]` y cómo proyectarla con `head`, `tail`, `last` e `init`. Algunos ejercicios sobre esto:

* `segundo(lista)` - el `head` del `tail` de la lista
* `tercero(lista)` - el `segundo` del `tail` de la lista
* `sumaDeLosPrimerosTres(lista)` - usando `head`, `segundo` y `tercero`
* `losPrimerosTres(lista)` - usando `head`, `segundo` y `tercero`
* `losExtremosCoinciden(lista)` - usando `head` y `last`
* `extremos(lista)` - usando `head` y `last`
* `anteultimo(lista)` - el `last` del `init` de la lista
* `antepenultimo(lista)` - el anteultimo del `last` de la lista
* `losUltimosTres(lista)` - usando `head`, `anteultimo` y `antepenultimo`

Otra forma de construir una lista es "pegando" otras dos: `[1, 2, 3] ++ [4, 5]` equivale a `[1, 2, 3, 4, 5]`; cuando hacemos esto decimos que estamos **concatenando** dos listas. Ojo que ambas cosas deben ser listas, `[1, 4] ++ 5` produce **BOOM**, lo correcto es hacer `[1, 4] ++ [5]`.

¡A practicar!

* `duplicar(lista)` - usando `++`
* `triplicar(lista)` - usando `++`
* `primeroPalFondo(lista)` - mezcla de `head`, `tail` y `++`
* `elUltimoSeraElPrimero(lista)` - mezcla de `last`, `init` y `++`
* `multiplicar(lista, cuantasVeces)` - usando `++` y `repeat`

También hablamos de la **lista vacía**, de la que no se puede proyectar nada, y de cómo saber si una lista es vacía o no, con `isEmpty`. Una cosa importante: el `tail` de una lista de un elemento es la lista vacía, lo mismo el `init`.

### Recorridos sobre listas

El recorrido es bastante similar al que hacíamos para un tablero, veamos dos ejemplos de funciones que computan el tamaño:

```
function tamanioTablero() {
  IrAlOrigen()
  total := 0
  
  while (haySiguiente()) {
    total := total + 1
    IrAlSiguiente()
  }

  return (total + 1)
}
```

```
function tamanioLista(lista) {
  porRecorrer := lista
  total := 0
  
  while (not isEmpty(porRecorrer)) {
    total := total + 1
    porRecorrer := tail(porRecorrer)
  }

  return (total)
}
```

Diferencias importantes:

* necesitamos que la lista venga **por parámetro**, porque ya no es global como lo era el tablero;
* como no tenemos un cabezal, hay que **recordar** por qué parte del recorrido vamos: para eso usamos una variable que vamos actualizando en cada iteración;
* cuando la lista se termina ya no hay nada más que procesar, **no hay caso borde**.

En definitiva, la gran diferencia gran es que en este caso el recorrido **lo manejamos nosotros** y por eso hace falta usar una variable para saber por dónde vamos (antes esa tarea la resolvía Gobstones con el cabezal).

Más ejercicios:

* `sumatoria(lista)` - devuelve la suma de todos los números de la lista;
* `elDobleDeCada(lista)` - devuelve una lista donde cada elemento es el doble del elemento de la lista original;
* `siguientes(lista)` - devuelve una lista con el siguiente de cada número (o sea, +1);
* `opuestos(lista)` - devuelve una lista con los opuestos de cada número;
* `reverso(lista)` - da vuelta la lista, sale recorriendo con `tail` e `init`.

Tarea:

* `enesimo(lista, posicion)` - devuelve el elemeto de la lista que está en la posición que llegó por parámetro. Por ejemplo: `enesimo([3, 8, 13], 2)` devuelve `8`, porque es el elemento que está en la posición 2.
* `repetidos(lista, cuanto)` - devuelve una lista que tiene cada elemento repetido la cantidad de veces que vino por parámetro. Por ejemplo `repetidos([6, 9, 3], 4)` devuelve `[6, 6, 6, 6, 9, 9, 9, 9, 3, 3, 3, 3]`, o sea cada elemento de la lista original repetido 4 veces. Pista: usar `multiplicar`.