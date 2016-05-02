---
layout:     post
title:      'Recorrido de Tablero'
subtitle:   "Bitácora de la clase del jueves 28/04/2016"
date:       2016-05-01 23:30:00
author:     "Alf"
---

### Cómo encarar un ejercicio con while y funciones
Buenas!
El jueves intentamos continuar con el ejercicio que dejó Fede de tarea. Después de intentar por un rato largo, hicimos un cambio completo, para atacar algo diferente, y no quedarnos trabados con eso.
¡Es importante eso! Nos ayuda a despejar la cabeza para luego poder atacar nuevamente el problema. Además... ejem... debíamos seguir con el tema de la clase...

Pero sé que varios se quedaron con las ganas de saber cómo se hacía. Así que aquí les traigo una pequeña explicación que espero les ayude:

#### ¿Hay soldado a la vista?

> `haySoldadoALaVista(dir, colorEjercito)` que indica si hay algún soldado de ese
ejército a la vista, o sea: si miramos en línea recta hacia dir lo primero que vemos esun soldado de ese color.

* ¿Nos piden un programa, una función ó un procedimiento? Una **función**. Entonces, lo que tenemos que hacer es **denotar** algo. (_devolver_ algo). Si hubiera sido un procedimiento, deberíamos concentrarnos en _cambiar_ el tablero, pero nos pidieron una función, así que lo que importa es lo que denotamos, porque después de lo que hagamos, el tablero al final quedará igual.
* ¿Qué **tipo** denota? Y, dice _indica si hay algún soldado_... O sea... Verdadero o Falso! entonces, el tipo de lo que devuelvo es _booleano_.
* Lo más importante es entender **qué** es lo que me denota. Ya sabemos el _tipo_, pero _¿Qué significa `haySoldadoALaVista`?_ ... Significa imaginarse que estoy parado mirando hacia adelante, y si "veo" un soldado, entonces _es cierto_.
* Una vez que sabemos que queremos una función, que tiene de denotar booleano, y lo que significa, debemos pensar la **estrategia**. Si quiero "ver si hay lejos", mi estrategia puede tener dos pasos: 1- ir. 2- fijarme y devolver.

Ahora sí un poco de código:

```
function haySoldadoALaVista(dir, colorEjercito){
  # paso 1: intentar ir hasta el soldado
  # paso 2: devolver si en la celda a la que llegué hay soldado del colorEjercito.
}

```

¡Cuidado! ¡Hay que **pensar antes** de largarse a escribir! Vale usar lápiz y papel para plantear borradores.

Y recién ahora podemos desglosar esos pasos: ¿Hay algún procedimiento previo que me sirva para alguno de los dos pasos?

* Para el paso 1: no. Lamentablemente voy a tener que hacerlo.
* Para el paso 2: SSssss casi. Tenemos una función `haySoldado()`, pero se fija si hay soldado de _cualquier_ ejército, no del color indicado. También vamos a tener que hacerlo.

Entonces, una vez que ya sabemos que estamos obligados a codificar porque no tenemos cosas hechas...

```
function haySoldadoALaVista(dir, colorEjercito){
  while( # no llegué a donde quiero... ){
    Mover(dir)
  }
  return (#si estoy parado en el soldado ó no)
}
```

Y para saber si estoy ó no parado en el soldado que quiero, puedo inventarme una función `haySoldadoDe(color)`, que me diga si hay un soldado de ese color, de manera que me queda todo así:

```gbs
function haySoldadoALaVista(dir, colorEjercito){
  while( puedeMover(dir) && not haySoldadoDe(color) ){
    Mover(dir)
  }
  return (haySoldadoDe(color))
}

function haySoldadoDe(dir,color){
  return (hayBolitas(color))
}
```

La condición del while, `puedeMover(dir) && not haySoldadoDe(color)`, que parece sacada de la galera, no lo es: significa que _mientras pueda moverme y no haya encontrado lo que quiera, sigo moviéndome_. Ese while con esa condición y el `Mover` adentro, es el paso 1. Cuando finalmente "llegué", no sé si llegué porque me choqué con el final ó porque encontré lo que quiero, por lo que el paso 2 es fijarme cuál de esas dos situaciones es.

##### Casos borde
¿Otra vez con ésto? ¡Sí! Hay que pensar siempre en los casos borde. Las preguntas que hay que hacerse en este caso son:

* ¿Qué pasa si no hay un soldado?
Y, por el código que planteamos, llegará al borde del tablero, el while cortará, y el paso 2 `return (haySoldadoDe(color))` retornará falso.
* ¿Qué pasa si en el primer casillero hay un soldado del color que busco?
Ah, esto es interesante: Si en el primer casillero hay un soldado, entonces al preguntar `while( puedeMover(dir) && not haySoldadoDe(color) )` (_mientras no haya soldado_) ya no se cumpliría... ¡Porque apenas empecé ya hay soldado de ese color! Entonces, **nunca se mueve**, ¡Porque ya encontré mi soldado, está acá mismo!.

Ejemplo: ![haySoldado.jpg](/img/2016-04-28/haySoldado.png)

En ese caso, `haySoldadoALaVista(Este, Rojo)` ¡Denota True! ¡Pero si no hay al Este...! Ah, sí que hay: es el soldado sobre el que está parado el cabezal. ¡Nunca entró al while! Es importante notar este caso borde.

#### Búsquedas
Éste recorrido se lo conoce normalmente como **Búsqueda**. Las búsquedas tienen la siguiente estructura:

```
while( puedo dar un paso && no encontré ){
  dar un paso
}
```

Se llama búsqueda, porque da pasos hasta encontrar, y cuando encuentra para. Esto me puede servir después tanto para hacer procedimientos como funciones muy útiles.

#### ¿Hay superior a la vista?

> `haySuperiorALaVista(dir, colorEjercito)` que indica si hay algún superior a la vista en esa dirección. Para saber si hay un superior, hay que comparar con el rango del soldado que está en la celda actual (se puede asumir que hay uno). Si en el trayecto hacia el superior hay algún enemigo, la función debería devolver False.

Bueno, empecemos como con el otro ejercicio:

* ¿Nos piden un programa, una función ó un procedimiento? Una **función**. Hay que devolver algo.
* ¿De qué **tipo** es? Y, el nombre es _hay...._, así que tengo que denotar True si hay, y False si no.
* ¿**Qué** significa lo que me piden? Ah, en este hay que pensar más: Al decir "a la vista" parece similar al anterior... Pero ¡ojo! que las apariencias engañan. Lo que quiero saber es, no sólo si hay a la vista un soldado, sino que además _su rango debe ser superior al mío_.
* Entonces, ahora podemos plantear una **estrategia** que, puede describirse igual que recién hicimos: 1- Fijarme si hay soldado a la vista. 2. Fijarme si su rango es mayor al mío. ¡y el resultado es un _Y_ lógico entre ambos!

Borrador:

```gbs
function haySuperiorALaVista(dir, colorEjercito){
  return (hay soldado a la vista && su rango es superior al mío)
}
```

¿Se ve cómo está pensada la función? Acá, si hay que recorrer, se hará ese recorrido en una función auxiliar. La primera parte (hay soldado a la vista) es del punto anterior, y podemos reusarlo:

```gbs
function haySuperiorALaVista(dir, colorEjercito){
  return (haySoldadoALaVista(dir,colorEjercito) && su rango es superior al mío)
}
```

y la segunda parte , lo podemos resolver haciendo `rango de él > rango mío`, ¡y para eso **se puede usar otra función que hicimos antes**! Estoy hablando de `gradoSoldadoMasCercano` (para el rango de él) e inventarnos una función `gradoActual(color)` que diga el rango de la celda actual...

Entonces quedaría:

```gbs
function haySuperiorALaVista(dir, colorEjercito){
  return (haySoldadoALaVista(dir,colorEjercito) && gradoSoldadoMasCercano(dir,colorEjercito) > gradoActual(colorEjercito))
}

function gradoActual(color){
  return (nroBolitas(color))
}
```

Peeeeeero hay un problema: ¿Recuerdan el **caso borde** del que hablamos antes? ¡Tanto `haySoldadoALaVista` como `gradoSoldadoMasCercano` tienen el mismo caso inicial! Esto significa que _si ya hay un soldado del color indicado en la celda actual, **no van a buscar otro lejos, se quedan acá**_.

Ejemplo: ![gradoCerca.jpg](/img/2016-04-28/gradoCerca.png)

En ese caso, `gradoSoldadoMasCercano(Este, Rojo)` ¡Denota 2! ¡y yo quería que denote 4! Ah, el truco es _moverse antes_ de chequear....

Entonces, para no complejizarnos demasiado, vamos a suponer que siempre voy a poderme mover al menos un paso en la dirección indicada. Y vamos a resolver así nuestro problema:

_Como yo quiero saber si hay un soldado más allá de mi casilla actual, y el grado que quiero tampoco es el de la casilla actual, entonces voy a moverme de la casilla actual para comenzar a chequear desde la casilla de al lado_

La solución final queda:

```gbs
function haySuperiorALaVista(dir, colorEjercito){
  Mover(dir) # Salgo de la casilla actual
  return (haySoldadoALaVista(dir,colorEjercito) && gradoSoldadoMasCercano(dir,colorEjercito) > gradoAnterior(dir,colorEjercito))
}

function gradoAnterior(dir,color){
  Mover(opuesto(dir)) # Como me moví, tengo que volver a buscar el grado
  return (nroBolitas(color))
}
```

### Apuestas

Ahora, pensemos el ejercicio de Apuestas, de la Guía 4 Parte 2.

> El procedimiento `AgregarApuesta(nroJugador,nroApostado,monto)` que agrega la apuesta indicada en alguna celda vacía. Precondición: hay al menos una celda vacía.

* ¿Programa, función ó procedimiento? **Procedimiento**. O sea, me piden _cambiar_ algo.
* No tiene sentido pensar un tipo de retorno, así que pasamos directamente a **qué** me piden: El tablero tiene bocha de apuestas, y casillas que están vacías. El objetivo es poner una nueva apuesta en una de esas vacías. ¡Guarda! El cabezal puede estar en cualquier lado...
* Y ahora, podemos pensar **estrategia**: 1- Ir hasta una celda vacía. 2- Poner la información en la celda encontrada.

```gbs
procedure AgregarApuesta(nroJugador,nroApostado,monto){
  # Paso 1: ir hasta celda vacía
  # Paso 2: poner la info
}
```

Lo cual más o menos quedó así:

![agregarApuesta.jpg](/img/2016-04-28/agregarApuesta.jpg)

### Recorrido del tablero

Y ahora tenemos que resolver el problema de **buscar una celda vacía**. ¡Sabemos hacerlo! ¡Es una búsqueda!
Sólo que ahora, cada uno de los pasos cambian, porque **debo recorrer todo el tablero**, y no sólo una línea.

Entonces, vamos a **mantener la estrategia de la búsqueda**, pero vamos a cambiar **el pasito** que damos en el while, para que cada pasito sea en una nueva celda del tablero, con el dibujo que se indica a continuación:

![recorridoTablero.jpg](/img/2016-04-28/recorridoTablero.jpg)

Y ahora que tenemos una idea de cómo realizar esa búsqueda, podemos plantearla así:

![buscarVacia.jpg](/img/2016-04-28/buscarVacia.jpg)

![esVacia.jpg](/img/2016-04-28/esVacia.jpg)

Les dejamos acá escrito cómo serían los procedimientos y funciones `IrAlOrigen()`, `haySiguiente()` y `IrAlSiguiente()`, que les sirven para **recorrer el TODO el tablero** de abajo hacia arriba, con la estrategia planteada arriba.

¡**A la biblioteca directo**!

```gbs
procedure IrAlOrigen(){
  IrAlBorde(Oeste)
  IrAlBorde(Sur)
}

procedure IrAlSiguiente(){
  if(puedeMover(Este)){
    Mover(Este)
  } else {
    IrAlBorde(Oeste)
    Mover(Norte)
  }
}

function haySiguiente(){
  return (puedeMover(Este) || puedeMover(Norte))
}
```

### Tarea

* Ejercicio 7 del dominio de apuestas (`estaElJugador(nroJugador)`)
* Ejercicio 8 del dominio de apuestas (` alguienJugoMasDe(nroApostado,cantMinima)`)
