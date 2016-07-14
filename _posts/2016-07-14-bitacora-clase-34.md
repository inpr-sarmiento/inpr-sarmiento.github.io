---
layout:     post
title:      'Repaso pal integrador'
subtitle:   "Bitácora de la clase del jueves 14/07/2016"
date:       2016-07-14 17:17:00
author:     "Alf"
---

### Enunciado y program

* [Acá el enunciado](https://docs.google.com/document/d/1ZMhqIV3u678xDCNanmoz8jeFuWeYoOJhA9YEaYeJKcw/edit?usp=sharing)
* Los puntos que se recomienda hacer en clase son: (**Igual en casa practiquen con todos**)
 * Punto 2. `diasQueAlquilo(videoclub, nroCliente)`
 * Punto 3. `seTeFueLaMano(videoclub, nroCliente)`
 * Punto 5. `cargarActor(videoclub, nroPelicula,nroActor)`
 * Punto 6. `esDocumental(videoclub,nroPelicula)`
 * Punto 14. `cuantoDebe(videoclub,nroCliente)`
 * Punto 8. `pelisPedorras(videoclub)`
 * Punto 13. `puedoAlquilar(videoclub,nroPelicula)`



El program:

```
type Videoclub is record {
	field pelis        -- [Pelicula]
	field alquileres	 -- [Alquiler]
}

type Pelicula is record {
	field nroPelicula  -- numero que identifica a la pelicula
	field actores      -- lista de numeros (cada numero identifica a un actor)
	field duracion     -- numero, indica cantidad de minutos
	field cantCopias   -- numero, indica de cuantas copias es dueño el videoclub
}

type Alquiler is record {
	field nroPelicula    -- numero que identifica a la pelicula.
	field nroCliente     -- numero que identifica al cliente.
	field diasAlquiler   -- numero que indica cuantos dias se llevo la peli
}

program {
  lasPelis := [
    Pelicula( nroPelicula <- 101, actores <- [20,45,57], duracion <- 126, cantCopias <- 4),
    Pelicula( nroPelicula <- 102, actores <- [20], duracion <- 140, cantCopias <- 2),
    Pelicula( nroPelicula <- 103, actores <- [33,57], duracion <- 50, cantCopias <- 1)
  ]

  losAlquileres := [
    Alquiler(nroPelicula <- 101, nroCliente <- 3001, diasAlquiler <- 7),
    Alquiler(nroPelicula <- 101, nroCliente <- 3005, diasAlquiler <- 4),
    Alquiler(nroPelicula <- 102, nroCliente <- 3001, diasAlquiler <- 8),
    Alquiler(nroPelicula <- 102, nroCliente <- 3005, diasAlquiler <- 4)
  ]

  elClub := Videoclub(
      pelis <- lasPelis,
      alquileres <- losAlquileres
    )

  return (diasQueAlquilo(elClub, 3001))
}
```

### Fecha integrador

* Recuerden que será el **miércoles 20/7**.
