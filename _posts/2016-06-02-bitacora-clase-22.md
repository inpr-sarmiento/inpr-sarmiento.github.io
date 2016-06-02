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

<!---

. ¡No todo son recorridos! Hacer la función `multiplosDe3Hasta(tope)` - devuelve la lista de los múltiplos de 3 empezando de 0 hasta llegar al tope. Por ejemplo, `multiplosDe3Hasta(14)` da la lista `[0,3,6,9,12]`.
* `siguientes(lista)` - devuelve una lista con el siguiente de cada número (o sea, +1);
* `opuestos(lista)` - devuelve una lista con los opuestos de cada número;
* `reverso(lista)` - da vuelta la lista, sale recorriendo con `tail` e `init`.
-->

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
