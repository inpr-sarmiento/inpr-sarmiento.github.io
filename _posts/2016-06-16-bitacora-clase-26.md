---
layout:     post
title:      'Búsquedas'
subtitle:   "Bitácora de la clase del jueves 16/06/2016"
date:       2016-06-16 20:17:00
author:     "Alf"
---

### Temas de clase

* Seguimos trabajando sobre **registros con listas** y **listas con registros**.
* Hicimos varios tipos de **búsquedas**.
* Proponemos una introducción a la idea de si **alguno cumple**.

### Cambio de dominio:

```gbs
type Producto is record {
  field id            // número
  field precio        // número
  field ingredientes  // lista de ingredientes
}

type Ingrediente is record {
  field tipo    // color. Rojo es grasa, Azul es azúcar, Verde es harina.
  field gramos  // número
  field caloriasPorGramo     // número
}
```

1. Hacer la función `costoTotal(productos)`, que recibe una lista de productos y denota la suma de todos los precios.
1. Hacer la función `encontrarProducto(productos, id)` que recibe una lista de productos y un id de producto y denota el producto (_registro entero_) que tiene ese id. _Precondición: Hay un y sólo un producto con ese id en la lista_
1. Hacer la función `ingredienteCalorico(ingredientes)` que recibe una lista de ingredientes y denota el primer ingrediente (_registro entero_) que tiene más de 100 calorías totales.
1. Hacer la función `productoDeMasDe(productos,valor)` que recibe la lista de productos y un valor y denota el primer producto cuyo precio es mayor al `valor`.
1. Hacer la función `cantIngredientesDelProducto(producto, id)` que recibe una lista de productos y un id de producto y denota la cantidad de ingredientes que tiene.
1. Hacer la función `ingredienteConGrasa(producto)` que recibe _un producto_ y denota el primer _ingrediente_ que tiene grasa. _Precondición: El producto tiene varios ingredientes, uno de los cuales tiene grasa_

### Alguno cumple....
1. Hacer una función genérica `contieneA(lista,elemento)` que recibe una lista y un elemento, y denota un booleano: verdadero cuando el elemento está en la lista, y falso cuando no está.
1. Hacer la función `ingredienteConHarina(producto)` que denota el primer _ingrediente_ (registro completo) que tiene harina. _Precondición: el producto tiene un ingrediente con harina_.
1. Hacer la función `tieneGrasa(producto)` que recibe un producto y denota booleano, verdadero si tiene grasa.
1. Hacer la función `aptoParaCeliacos(producto)` que recibe un producto y denota booleano, verdadero si es apto para celíacos (ó sea, no tiene ningún ingrediente con harina)

### Tarea - Más sobre Universidad
1. Hacer la función `estudianteConDni(alumnos,dni)`, que dada una lista de estudiantes y un dni, obtiene el _registro_ entero que representa al estudiante que tiene ese dni. _Precondición: en la lista está el estudiante con ese dni._
1. Hacer la función `cantAplazosDe(estudiantes,dni)`, que, dada una lista de estudiantes y un dni, obtiene la cantidad de aplazos del estudiante indicado. _Precondición: en la lista está el estudiante con ese dni._
1. Hacer la función `primerAlumnoConDiez(estudiantes)`, que dada una lista de estudiantes denota el primer estudiante (registro completo) que tiene un 10 entre sus examenes aprobados.

<!--

1. Hacer la función `hayAlguienConMasPromedio(estudiantes,promedio)`, que dada una lisa de estudiantes y un promedio, denota verdadero si existe alguien con más promedio que el indicado.

-->
