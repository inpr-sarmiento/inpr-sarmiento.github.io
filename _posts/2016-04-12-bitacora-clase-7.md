---
layout:     post
title:      'Alternativa condicional'
subtitle:   "Bitácora de la clase del martes 12/04/2016"
date:       2016-04-12 21:30:00
author:     "Fede"
---

### Avisos parroquiales
- Algunos vienen flojos con la tarea, es más o menos momento de preocuparse. Muchos se estuvieron poniendo al día, bien.

### Tarea - errores comunes
- Sólo 4 personas entregaron, feo.
- El de la ELE salió bien, no vamos a decir nada para que el resto tenga la oportunidad de pensarlo.
- Con `TocoYMeVoy` hubo mambos feos. La idea era que las bolitas negras servían como "indicador", siempre hay que poner una roja. Construimos entre todos la versión `TocoYMeQuedo`, delegando en `MoverNYPoner`; con eso resuelto `TocoYMeVoy` sale más fácil (lo hacen en casa).

### Repaso y formalización de expresiones
La última vez vieron una _especie de_ procedimientos que _devuelven_ o _denotan_ valores: `nroBolitas(color)`, `opuesto(direccion)` y otros tantos que ya están en el machete; el nombre correcto para estos "procedimientos especiales" es **expresiones**. Entonces a las que ya conocían, que se llaman **expresiones literales** (`7`, `Sur`, `Rojo`) se le agregan estas otras _más inteligentes_, que hacen alguna operación, computan, pueden depender de la entrada (argumentos o estado del tablero).

Con esta noción, empezaron a hacer algunos programas y procedimientos que **dependen del tablero**. Por ejemplo, ejecutar `PasarTodoANegro()` tiene un efecto si hay bolitas y otro efecto (en particular, ninguno) si no las hay. Hoy vamos a seguir en esa línea de "lo desconocido", vamos a seguir aprendiendo a preguntarle cosas a Gobstones. 

### Alternativa condicional
Dentro de todo el universo de preguntas que podemos hacer, las que nos van a interesar son aquellas que puedan responderse por **sí** o por **no**, o siendo más formales por **Verdadero** y **Falso** (hola Lucrecia). 

Entre todos, surgieron estas preguntas:
![expresionesBooleanas.jpg](/img/2016-04-12/expresionesBooleanas.jpg)

Luego, vimos un ejemplo: `MoverMiedoso(dir)`. ¿Qué hace? Antes de moverse en la dirección dada, **pregunta** si `puedeMover` (por eso es miedoso). 

De acá en adelante, hicimos unos cuantos ejercicios, que pongo acá más abajo. Los que están (entre paréntesis) son de la [guía complementaria 3](/assets/material/Guía 3 Ejercicios - Alternativa y expresiones.pdf) y los que están [entre corchetes] son de la [práctica 3](/assets/material/Practica3-repeticion-indexada-y-alternativa-condicional.pdf).

* (3a) `AsegurarAlMenosUna(col)` - acá aparece el `not` como forma de negar una condición: `not hayBolitas(col)`. Es como el `¬p` o `~p` de Matemática.
* (3b) `AsegurarUnaDeCada()` - hay que reutilizar el anterior, con cada uno de los colores.
* [28] `DesempatarDos(c1, c2)` - acá surge la primera expresión booleana compuesta, hay que usar un and: `nroBolitas(c1) == nroBolitas(c2)`
* [30] `Desempatar()` - similar al anterior. Un truquito matemático que vimos es que alcanza con hacer 3 comparaciones para saber que los 4 son iguales.
* [27] `PonerCSiHayXeY(c, x, y)` - fácil, parecido al 28.

Hasta ahí la complejidad venía casi exclusivamente en pensar "la pregunta", la expresión booleana. A partir del ejercicio (6) surgió la necesidad de hacer algo distinto _si no se cumplía_ tal condición, y así surgió el `else`. Arrancamos entonces otra tanda de ejercicios:

* (6) `MoverPalanteOPatras(dirAdelante, colGuia)` - 
* (7) `​MoverSegunColor(dir1, dir2, col)` - en la misma línea que el anterior.
* [31] `PonerOSacarAcorde(c, acorde)` - en la misma línea que el anterior.
* (8) ​`MoverSegunCantDeColor(col)` - un embole. Moraleja: se pueden anidar `ifs` -poner uno adentro del otro- aunque es feo, conviene delegar siempre que se pueda (en este caso no se podía).
* (9) `MoverSegunColor(dir1, dir2, col)` - este salía más o menos fácil.
* (10) `DescomprimirHacia(dir, col1, col2)` - ¡reutilizar! sale usando el procedimiento anterior.

### Tarea
Quedó sólo la nueva guía de Mumuki como tarea.
