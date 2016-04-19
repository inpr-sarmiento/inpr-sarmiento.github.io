---
layout:     post
title:      'Dominios'
subtitle:   "Bitácora de la clase del jueves 14/04/2016"
date:       2016-04-14 23:30:00
author:     "Alf"
---

### Repaso de estado del tablero

Hoy vimos un truquito para solucionar el problema de TocoYMeVoy. El truquito no es tan importante, lo importante es entender por qué no salía el ejercicio:

#### Solución incorrecta:

```gbs

procedure TocoYMeVoy(dir,color){
  MoverN(nroBolitas(Negro),dir)
  Poner(color)
  MoverN(nroBolitas(Negro),opuesto(dir))
}

```

Acá el paso a paso que explica que cuando _ya estoy lejos_, no sé cuánto volver, porque el `nroBolitas` es una expresión que sí o sí tengo que usar en el casillero inicial. ¡Allá lejos no hay bolitas negras, están acá!

![Seguimiento.jpg](/img/2016-04-14/Seguimiento.jpg)

#### Solución con truquito (lee el tablero sólo una vez):

```gbs

procedure TocoYMeVoy(dir,color) {
  TocoYMeVoyConCant(nroBolitas(Negro),dir,color)
}

procedure TocoYMeVoyConCant(cant,dir,color) {
  MoverN(cant,dir)
  Poner(color)
  MoverN(cant,opuesto(dir))
}

```

### Dominios: Escapando del Incendio

Hoy introdujimos dominios, lo que significa que de ahora en más vamos a empezar a usar el tablero, las bolitas y el cabezal para **representar ideas de la realidad**, como ser un reloj, una persona escapando del fuego, ó un bosque con árboles.

Esto implica que **deben aparecer las abstracciones del dominio en mi programa**. En otras palabras, si hay una persona que debe escapar de un incendio, la palabra "Tipo" ó "Persona" tiene que aparecer en el procedimiento que corresponda. En nuestro caso de "Escapando del incendio", hicimos un procedimiento que se llamaba `AvanzarUnPaso`, que representaba un paso en el camino de la persona, y el procedimiento `MoverTipito` que justamente movía a las personas. **Dar un paso** es una abstracción de dominio, y la hicimos aparecer en nuestro programa como un procedimiento, y lo mismo pasa con la idea de **Persona**, que estaba representada por una bolita Negra pero escondimos ese hecho detrás del procedimiento `MoverTipito`.

La **estrategia** siempre primero:

![Estrategia.jpg](/img/2016-04-14/Estrategia.jpg)

La versión final fue:

```gbs

procedure AvanzarUnPaso(){
  Mover(Este)
  if(hayBolitas(Rojo)){
    VolverYMoverTipito(Norte)
  } else {
    VolverYMoverTipito(Este)
  }
}

procedure VolverYMoverTipito(dir){
  Mover(Oeste)
  Sacar(Negro)
  Mover(dir)
  Poner(Negro)
}

```

### Dominios: El bosque

Hicimos también el ejercicio del Bosque, que está al final de la Guía 3.

Aquí vuelve a ser importante que aparezcan las **abstracciones de dominio en nuestro programa**. En otras palabras, si el enunciado habla de _semillas_, habla de _nutrientes_ y de _árboles_, entonces tiene que haber procedimientos acordes. No vale que nuestro programa hable sólo de bolitas.

![germinar.jpg](/img/2016-04-14/germinar.jpg)

Miren acá, por ejemplo: usamos **UsarSemilla** en vez de **Sacar(Rojo)**. ¡Importantísimo!

![auxGerm.jpg](/img/2016-04-14/auxGerm.jpg)

![alimentar.jpg](/img/2016-04-14/alimentar.jpg)

![auxAli.jpg](/img/2016-04-14/auxAli.jpg)

### Tarea
- Reentregar **toda la tarea que figure pendiente**
- Hacer el punto 3 y 4 de El Bosque

¡Saludos!

Alf
