---
layout:     post
title:      "Errores comunes con procedimientos y parámetros"
subtitle:   "Bitácora de la clase del martes 29/03/2016"
date:       2016-03-30 15:48:00
author:     "Fede"
---

A partir de lo que laburaron durante la semana, dedicamos esta clase a recuperar errores comunes que la mayoría había cometido.

### Reutilización de herramientas
Programar se trata de constantemente construir herramientas de cada vez más alto nivel que nos ayuden a resolver nuestro problema. A medida que avancemos en las clases y en la dificultad, el `Poner` y `Mover` van a quedar cada vez más enterrados, porque sino es imposible construir cosas más interesantes que una línea.

Muchos teclearon en el `e` y el `f` de la tarea; cuando se les pidió el `DibujarFila`, que era de más alto nivel, se olvidaron del Rojo y Azul salteado y volvieron a `Poner` y `Mover`: ¡NO! Siempre construimos sobre lo anterior, los ejercicios están incluso planteados así. En programación copiar y pegar es un indicio de que algo estamos haciendo mal.

### Confusión entre definición y uso
* Cuando lo **defino**, no sé qué valor va a tener, justamente ese es el chiste. Por eso, nunca nunca nunca un parámetro se va a poder llamar `Norte` ni `Rojo`, porque eso espero que me lo pase quien lo va a usar.
* Cuando lo **uso**, _tengo que_ darle un valor, que por ahora se puede hacer de 2 formas: con un **literal** (`Azul`, `Negro`, `Este`, `Sur`) o "pasándole" otro **parámetro** (sólo vale cuando un procedimiento llama a otro, no se puede hacer esto en el `program`, porque no puede tener parámetros).

### _Parametritis_
Es un mal que aqueja tanto a aprendices como a profesionales. Cada vez que aprendemos una herramienta nueva, tendemos a querer usarla por todos lados, aún cuando esto complejiza nuestro código. 

En programación, la mejor solución es **siempre** la más sencilla, y aprender a hacer eso es toda una habilidad. Nosotros tenemos una ventaja que no tienen otras disciplinas: cambiar no nos cuesta casi nada, y tenemos que aprender a aprovecharlo. Moraleja: parametricen si y sólo si eso les hace escribir menos código, y no más.

### Ejercitación

**Banderas.**
Armamos pseudo-banderas de Argentina, Italia, Francia y Perú, con la condición de que para construir una bandera tenía que haber 3 llamados al mismo procedimiento. El código, con alguna que otra variante, terminó quedando así:

```gbs
procedure Argentina() {
  FranjaHorizontal(Azul)
  Mover(Norte)
  FranjaHorizontal(Negro)
  Mover(Norte)
  FranjaHorizontal(Azul)
}

procedure Italia() {
  FranjaVertical(Verde)
  Mover(Este)
  FranjaVertical(Negro)
  Mover(Este)
  FranjaVertical(Rojo)
}
```

Una vez construidas las 4 banderas, nos dimos cuenta que podíamos generalizar todavía un poco más: para armar una bandera horizontal o vertical de 3 franjas basta simplemente con elegir los 3 colores. La segunda versión quedó entonces así:

```gbs
procedure Argentina() {
  BanderaHorizontal(Azul, Negro, Azul)
}

procedure Italia() {
  BanderaVertical(Verde, Negro, Rojo)
}
```

Como cierre, concluimos en que esto simplemente era un ejercicio para usar parámetros y más parámetros, y por eso seguimos abstrayendo hasta llegar a generalizar la construcción de las banderas. De nuevo, la solución más simple siempre es la mejor, y sólo vamos a intentar hacer algo "más genérico" si la situación lo amerita.

**Cuadrado relleno.**
La siguiente tarea fue armar un procedimiento que permitiera construir un cuadrado de 4x4 con un color para el contorno y otro para el relleno. Surgieron de nuevo algunas dudas, varixs confundieron el ejemplo que yo di (borde rojo y contorno verde) e hicieron un procedimiento que sólo construía cuadrados de esos colores.

La estrategia sugerida fue pensar el contorno por un lado y el relleno por otro, quedando como solución propuesta la siguiente:

```gbs
procedure Cuadrado(colorRelleno, colorContorno) {
  Contorno(colorContorno)
  Mover(Este)
  Mover(Norte)
  Relleno(colorRelleno)
}
```

**Varios dibujos con líneas negras.**
Lo último, que además **quedó como tarea**, fue resolver los ejercicios que están desde la página 9 de la guía en adelante, con dos pequeños cambios: 

* en vez de implementar los `LineaNorte4`, `LineaEste4`, `LineaSur4` y `LineaOeste4` que se pedían, la idea es hacerlo todo con un `Linea4(direccion)`;
* lo mismo para los `LineaNorte4V`, `LineaEste4V`, `LineaSur4V` y `LineaOeste4V`, pero esta vez van a necesitar parametrizar la dirección de la ida y la de la vuelta `Linea4V(direccionIda, direccionVuelta`. Obviamente, la de la vuelta siempre tiene que ser la opuesta a la de la ida (todavía no conocemos una mejor forma de manejar esto, paciencia...).

Para quienes terminen todos los que están ahí, les queda como desafío hacer este hermoso dibujo de un numeral o _hashtag_, alusivo a los tiempos digitales que corren:

![hashtag.png](/img/2016-03-30/hashtag.png)

Pista: sale pensándolo como dos pasillos (ver ejercicio **c**).