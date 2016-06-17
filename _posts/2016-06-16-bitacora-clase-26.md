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

program {
  producto1 := Producto(id<-1, precio<-15, ingredientes<-[
    Ingrediente(tipo<-Azul,gramos<-100,caloriasPorGramo<-2)
  ])
  producto2 := Producto(id<-2, precio<-25, ingredientes<-[
    Ingrediente(tipo<-Verde,gramos<-50,caloriasPorGramo<-2),
    Ingrediente(tipo<-Rojo,gramos<-50,caloriasPorGramo<-5)
  ])
  producto3 := Producto(id<-3, precio<-10, ingredientes<-[
    Ingrediente(tipo<-Verde,gramos<-36,caloriasPorGramo<-1),
    Ingrediente(tipo<-Azul,gramos<-24,caloriasPorGramo<-5),
    Ingrediente(tipo<-Verde,gramos<-36,caloriasPorGramo<-3)
  ])
  producto4 := Producto(id<-4, precio<-55, ingredientes<-[
    Ingrediente(tipo<-Rojo,gramos<-34,caloriasPorGramo<-3),
    Ingrediente(tipo<-Rojo,gramos<-34,caloriasPorGramo<-6)
  ])
  losProdus := [producto1, producto2, producto3, producto4]
}
```

1. Hacer la función `costoTotal(productos)`, que recibe una lista de productos y denota la suma de todos los precios.
2. Hacer la función `encontrarProducto(productos, id)` que recibe una lista de productos y un id de producto y denota el producto (_registro entero_) que tiene ese id. _Precondición: Hay un y sólo un producto con ese id en la lista_
3. Hacer la función `ingredienteCalorico(ingredientes)` que recibe una lista de ingredientes y denota el primer ingrediente (_registro entero_) que tiene más de 100 calorías totales.
4. Hacer la función `productoDeMasDe(productos,valor)` que recibe la lista de productos y un valor y denota el primer producto cuyo precio es mayor al `valor`.
5. Hacer la función `cantIngredientesDelProducto(productos, id)` que recibe una lista de productos y un id de producto y denota la cantidad de ingredientes que tiene.
6. Hacer la función `ingredienteConGrasa(producto)` que recibe _un producto_ y denota el primer _ingrediente_ que tiene grasa. _Precondición: El producto tiene varios ingredientes, uno de los cuales tiene grasa_

Hicimos todas las funciones menos la 4 y la 6.

Algunas soluciones:

#### Punto 1:
![comparaForeach.jpg](/img/2016-06-16/comparaForeach.jpg)

Aprovechamos para hacer una comparación entre resolverlo con **foreach** y resolverlo con while. Algo importante que cambia entre ambas soluciones es lo que está **remarcado en verde**: El elemento actual. El elemento actual al recorrer con while, es la cabeza de la lista recorrido. En cambio, con el foreach ese elemento es la variable que usemos en el foreach.

> **Importante**: Dijimos que **se les va a evaluar** que usen foreach y while cuando corresponda.

El truco es:

* Si necesito **recorrer por completo** la lista, entonces **va foreach**.
* Si no hace falta recorrer toda la lista, y **debo cortar el recorrido**, entonces **va while**.

| Recorrido **completo** | Recorrido **con corte** |
| --- | --- |
| Con foreach | Con while |
| Recolección, filtro, recolección con filtro, Totalización (contar, acumular) | Búsquedas, Alguno cumple, todos cumplen |

> En la sección de [Material](/material) están **los esquemas de recorrido** explicados. **¡A leer!**

#### Punto 2:

Es el primer ejemplo de búsqueda en listas que vemos:

![encontrarProd.jpg](/img/2016-06-16/encontrarProd.jpg)

#### Punto 4:

Vimos que podemos hacerlo de forma muy parecida al punto 2:

![cantIngNotOK.jpg](/img/2016-06-16/cantIngNotOK.jpg)

¡Pero **no hay que repetir código**!

Así que se puede reusar el punto 2:

![cantIngOK.jpg](/img/2016-06-16/cantIngOK.jpg)

### Tarea - Más sobre Universidad
1. Hacer la función del punto 6 de arriba.
1. Hacer la función `estudianteConDni(estudiantes,dni)`, que dada una lista de estudiantes y un dni, obtiene el _registro_ entero que representa al estudiante que tiene ese dni. _Precondición: en la lista está el estudiante con ese dni._
1. Hacer la función `cantAplazosDe(estudiantes,dni)`, que, dada una lista de estudiantes y un dni, obtiene la cantidad de aplazos del estudiante indicado. _Precondición: en la lista está el estudiante con ese dni._
1. Hacer la función `dniDelGroso(estudiantes)`, que dada una lista de estudiantes, denota _el dni_ del primer estudiante groso. Un estudiante es groso cuando no tiene aplazos y tiene más de 9 de promedio. _Precondición: en la lista hay al menos un estudiante groso_


<!--

### Alguno cumple....
1. Hacer una función genérica `contieneA(lista,elemento)` que recibe una lista y un elemento, y denota un booleano: verdadero cuando el elemento está en la lista, y falso cuando no está.
1. Hacer la función `ingredienteConHarina(producto)` que denota el primer _ingrediente_ (registro completo) que tiene harina. _Precondición: el producto tiene un ingrediente con harina_.
1. Hacer la función `tieneGrasa(producto)` que recibe un producto y denota booleano, verdadero si tiene grasa.
1. Hacer la función `aptoParaCeliacos(producto)` que recibe un producto y denota booleano, verdadero si es apto para celíacos (ó sea, no tiene ningún ingrediente con harina)

universidad...
1. Hacer la función `primerAlumnoConDiez(estudiantes)`, que dada una lista de estudiantes denota el primer estudiante (registro completo) que tiene un 10 entre sus examenes aprobados.
1. Hacer la función `hayAlguienConMasPromedio(estudiantes,promedio)`, que dada una lista de estudiantes y un promedio, _denota booleano_, verdadero si existe alguien con más promedio que el indicado.
-->
