---
layout:     post
title:      'Búsquedas'
subtitle:   "Bitácora de la clase del jueves 23/06/2016"
date:       2016-06-23 13:17:00
author:     "Alf"
---

### Temas de clase

* Hicimos **modificaciones de listas**
* Integramos eso con modificaciones de registros.
* Comenzamos a hacer _en papel_ el parcial de práctica que deben terminar _en papel_ para el martes que viene.

Pensando bien _qué tipo de recorrido_ utilizar en cada caso:

1. Hacer la función `quemarPixeles(colores)` que hace que todos los `Rojo` de la lista de colores se transformen en `Negro`. Por ejemplo, `quemarPixeles([Negro,Rojo,Azul,Rojo])` denota la lista `[Negro,Negro,Azul,Negro]`.
2. Hacer la función `quemarPrimerPixel(colores)`, que hace que _sólo el primer pixel_ **Rojo** se queme. Por ejemplo, `quemarPrimerPixel([Negro,Rojo,Azul,Rojo])` denota la lista `[Negro,Negro,Azul,Rojo]`.
3. Hacer la función `sacarPrimeraOcurrencia(lista,elemento)` que recibe una lista y un elemento, y denota el resultado de sacar _sólo la primera ocurrencia_ del elemento en la lista. Por ejemplo, `sacarPrimeraOcurrencia([Rojo,Azul,Verde,Azul], Azul)` denota la lista `[Rojo,Verde,Azul]`.
4. Hacer la función `reemplazarProducto(productos, idSacar, productoNuevo)` que recibe una lista de productos, un id del producto que quiero sacar, y un _producto entero_ nuevo, y denota la lista en la que sólo cambia el producto indicado, reemplezándolo por el nuevo. Por ejemplo, si tengo una lista con una barrita de cereal (id 6), un alfajor (id 7), y un bocadito (id 3) cuando haga `reemplazarProducto(productos, 7, chocolate)` entonces voy a obtener una lista con la barrita de cereal, el chocolate y el bocadito. O sea, obtengo una lista idéntica a la original pero donde estaba el id 7 sacó el producto alfajor y puso el chocolate. _Precondición: Hay un y sólo un producto con ese id en la lista_.
5. Hacer la función `hacerLight(producto)` que recibe un producto y lo hace light. Ó sea, denota un producto idéntico al original, pero con su primer ingrediente _graso_ transformado en _harina_, y con la mitad de las calorías por gramo.

Por ejemplo, si hago que este producto se haga light:

```
Producto(id<-5, precio<-55, ingredientes<-[
  Ingrediente(tipo<-Azul,gramos<-20,caloriasPorGramo<-5),
  Ingrediente(tipo<-Rojo,gramos<-15,caloriasPorGramo<-8),
  Ingrediente(tipo<-Rojo,gramos<-20,caloriasPorGramo<-6)
])
```

obtengo:

```
Producto(id<-5, precio<-55, ingredientes<-[
  Ingrediente(tipo<-Azul,gramos<-20,caloriasPorGramo<-5),
  Ingrediente(tipo<-Verde,gramos<-15,caloriasPorGramo<-4),
  Ingrediente(tipo<-Rojo,gramos<-20,caloriasPorGramo<-6)
])
```
