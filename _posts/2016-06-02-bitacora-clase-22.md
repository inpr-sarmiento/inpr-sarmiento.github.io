---
layout:     post
title:      'Listas: más recorridos con while'
subtitle:   "Bitácora de la clase del jueves 02/06/2016"
date:       2016-06-02 12:00:00
author:     "Alf"
---

### Temas de clase: Recorridos

* Repaso de **recolección** (ó "mapeo").
* **Filtro**.
* **Recolección con filtro**.
* **Búsqueda**.

### Enunciados de clase:

1. `siguientes(direcciones)` - devuelve una lista donde cada elemento es el siguiente del elemento de la lista original. Si le paso una lista `[Norte, Este, Este, Sur]`, denota la lista `[Este, Sur, Sur, Oeste]`.
2. Pregunta teórica: ¿Puedo pasarle una lista de números al punto anterior?
3. Pregunta teórica: ¿Puedo pasarle una lista de direcciones al punto `opuestos` de la clase pasada?
4. `fuerzas(colores)` - devuelve una lista de números donde cada elemento representa la fuerza del color de la lista original. La fuerza del Rojo es 17, igual que la del Negro. La fuerza del Azul es 15, igual que la del Verde. En una lista `[Negro, Rojo, Verde]` el resultado es `[17, 17, 15]`.
5. `decapitar(listaDeListas)` - devuelve una lista con las cabezas de cada elemento de la lista original. Por ejemplo, `decapitar([[1,2,3,4],[66,77,88],[9,0,9]])` denota la lista `[1,66,9]`.
6. `mayoresA(unNumero, numeros)` - recibe un número y una lista, y denota una lista con aquellos números que son mayores al indicado. Por ejemplo, si quiero saber los `mayoresA(5,[16,3,4,56,7,1,8])` denota la lista `[16,56,7,8]`.
7. `losLindos(colores)` - recibe una lista de colores y denota una lista con los colores lindos de la lista original. El Azul es un color feo, los demás son lindos. Por ejemplo, `losLindos([Rojo, Rojo, Azul, Verde, Azul])` denota la lista `[Rojo,Rojo,Verde]`.
8. `losPares(nros)` - recibe una lista de números, y denota una lista conteniendo sólo los números pares de la lista original.
9. `tripleDeLosMenoresA(numero,nros)` - recibe un número y una lista de números y retorna una lista, cuyos elementos son el triple de cada elemento menor al indicado. Por ejemplo `tripleDeLosMenoresA(6,[3,8,4,7])` denota la lista `[9,12]`.
10. `fuerzaDeLosLindos(nros)` - recibe una lista de colores, y denota la fuerza de cada uno de los colores lindos de la lista original.
11. ¡No todo son recorridos! Hacer la función `multiplosDe3Hasta(tope)` - devuelve la lista de los múltiplos de 3 empezando de 0 hasta llegar al tope. Por ejemplo, `multiplosDe3Hasta(14)` da la lista `[0,3,6,9,12]`.


<!---
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
-->
