---
layout:     post
title:      'Modificación de registros'
subtitle:   "Bitácora de la clase del jueves 26/05/2016"
date:       2016-05-26 16:00:00
author:     "Alf"
---

### Enunciados que guiaron la clase

1. `esDiaMasAntiguo(fechaA,fechaB)` denota verdadero cuando la fecha A es más antigua que la fecha B, pero **sin mirar el año**, sólo mirando el mes y el día.
Ejemplo: Si tengo
`revolucionDeMayo := Fecha(dia <- 25, mes <- 5, anio <- 1810)`
`otraFecha := Fecha(dia <- 31, mes <- 1, anio <- 2016)`
Cuando yo pregunto `esDiaMasAntiguo(otraFecha,revolucionDeMayo)` denota `True`.
2. `cuantosAniosPasaron(fecha1, fecha2)`. Contemplar la posibilidad de que todavía no haya llegado la fecha. _Precondición:_ `fecha2` está después que `fecha1`. _¡Es el punto 9 del martes pasado! Pero ahora es obligatorio contemplar no haber llegado a la fecha._
  Por ejemplo, entre el 25/05/2013 y el 01/05/2016 pasaron 2 años (el 25/05 van a haber pasado 3).
3. `ultimoDiaInvierno(anio)` que tome un año y devuelva el último día de invierno de ese año. _¡Es el punto 11 del martes pasado!_.
4. `yaPasoMiCumple()` denota `True` si ya pasó mi cumpleaños de este año, y hace uso de la función `diaDeHoy()`. Pista: hacer una función que diga cuál es mi cumpleaños y también usarla.
5. Siguiendo con estudiantes: Hacer la función `yo()`, que retorne un estudiante, que lo represente a uds.
6. `nuevoIngresante(dni,fechaNac,sexo)` recibe los datos de un estudiante y denota un estudiante completo, con 0 materias aprobadas.
7. `ingresanteGemelo(unEstudiante)` recibe un estudiante y denota otro estudiante, su gemelo. El estudiante que devuelve tiene el DNI siguiente, la misma fecha de nacimiento, 0 materias aprobadas, y el mismo sexo.
8. `aprobarMateria(unEstudiante)` recibe un estudiante y _lo modifica_, agregándole una materia aprobada. O sea, devuelve un estudiante nuevo que es igual al original, salvo que tiene una materia aprobada más.
9. `cambioDeSexo(unEstudiante)` recibe un estudiante y lo hace más feliz: el estudiante descubrió que en realidad es del sexo opuesto y quiere cambiárselo, así que la función devuelve el estudiante con el sexo cambiado.
10. `corregirAnioNacimiento(unEstudiante, nuevoAnio)` que denota el mismo estudiante pero con el anio en el que nació corregido con el `nuevoAnio`.
11. `yaPasoElCumpleDe(unEstudiante)` denota verdadero si ya pasó **el cumple de este año** del estudiante en cuestión.

### Soluciones propuestas puntos 1 al 5

* Punto 1:

```gbs
function esDiaMasAntiguo(fechaA,fechaB){
  return(mes(fechaA) < mes(fechaB) || (mismoMes(fechaA,fechaB) && dia(fechaA) <= dia(fechaB)))
}
```

* Punto 2:

```gbs
function cuantosAniosPasaron(fecha1, fecha2){
  cuantosAnios := anio(fecha2) - anio(fecha1)
  if(esDiaMasAntiguo(fecha2,fecha1)){
    cuantosAnios := cuantosAnios - 1
  }
  return (cuantosAnios)
}

```

* Punto 3:

```gbs
function ultimoDiaInvierno(elAnio){
    return (Fecha(dia <- 20, mes <- 09, anio <- elAnio))
}
```

Acá es interesante detenerse y notar que estoy **armando y devolviendo una fecha**, como si fuera un número.

Teniendo en cuenta que ésto:

```gbs
cuenta := 5 + 3
return (cuenta)
```

es lo mismo que esto:

```gbs
return (5+3)
```

entonces decir:

```gbs
laFechaADevolver := Fecha(dia <- 20, mes <- 09, anio <- elAnio)
return (laFechaADevolver)
```

es lo mismo que:

```gbs
return (Fecha(dia <- 20, mes <- 09, anio <- elAnio))
```


* Punto 4:

```gbs
function yaPasoMiCumple(){
    return (esDiaMasAntiguo(miCumple(),diaDeHoy()))
}

function diaDeHoy(){
  return (Fecha (dia <- 26, mes <- 5, anio <- 2016))
}

function miCumple(){
  return (Fecha (dia <- 13, mes <- 11, anio <- 1986))
}
```

* Punto 5

(lo hace cada uno, pero puede tener esta forma:)

```gbs
function yo(){
  return (Estudiante(fechaNacimiento <- miCumple(), dni <- 33333333, nroMateriasAprobadas <- 43, esMujer <- False))
}
```

* Punto 6:

```gbs
function nuevoIngresante(dni, fechaNac, sexo){
  return Estudiante(dni <- dni, fechaNacimiento <- fechaNac, esMujer <- sexo, nroMateriasAprobadas <- 0)
}
```

Acá es importante mirar esta parte:

function nuevoIngresante(dni, fechaNac, sexo){

  return Estudiante(**dni** <- **dni**, ....

¿Cuál es la diferencia entre esos dos **dni**? Fácil: recordemos que la sintaxis es:

`nombreDelCampo <- valor`

Entonces, el que está a la **izquierda** es el nombre del **campo** donde estoy queriendo poner el valor, y el que está a la **derecha** es el **nuevo valor** que me viene por parámetro.

#### Bonus

Una nueva versión de `esDiaMasAntiguo`, usando la siguiente estrategia: Para saber si el dia es más antiguo que el otro, puedo cambiar los años de las fechas para que sean iguales, y luego usar la función `esMasAntigua`, que recibe dos fechas y me dice cuál es la más antigua. Ella es la encargada de revisar el día y el mes. ¡Ya lo habíamos hecho la clase pasada!

```gbs
/* Versión 2, reeee fumeta BONUS considerando temas que vienen después: */
function esDiaMasAntiguo(fechaA,fechaB){
  return esMasAntigua(Fecha( dia <- dia(fechaA), mes <- mes(fechaA) , anio <- anio(fechaB)) , fechaB),
}
```

### Cambiando el dominio: Compus

```gbs
type Computadora is record {
  field memoria       // es una Memoria
  field tamanioDisco  // es un número
  field procesador    // es un Procesador
  field esNotebook    // es un booleano
}

type Procesador is record {
  field velocidadNucleo  // es un número
  field cantNucleos      // es un número
  field marca            // es un color (Rojo: AMD, Azul: Intel, Verde: ARM)
}

type Memoria is record {
  field velocidad   // es un número
  field tamanio     // es un número
}
```
1. Hacer las funciones `colorARM()`, `colorIntel()`, `colorAMD()` que denoten los colores correspondientes.
2. Hacer la función `notebookGrosa()` que denote una computadora que es una notebook con una RAM de 8Gb y 1200 MHz de velocidad, un disco de 500 Gb y un procesador AMD de 4 núcleos con 2300 MHz de velocidad.
3. Hacer la función `pcTranca()` que denote una computadora de escritorio con una RAM de 4Gb y 800 MHz de velocidad, un disco de 500 Gb y un procesador Intel de 2 núcleos con 1600 MHz de velocidad.
4. Hacer la función `estaBienArmada(unaCompu)` que reciba una computadora y diga si está bien armada. Esto sucede cuando la velocidad del procesador es la misma que la velocidad de la memoria. Ojo, las notebooks están siempre bien armadas, sin importar las velocidades.
5. Hacer la función `velocidadReal(unaCompu)` que reciba una compu y diga la velocidad real, que es el mínimo entre las velocidades de la RAM y el procesador.
6. Hacer la función `duplicarMemoria(unaRAM, unTamanio)` que reciba una memoria y un tamanio y _cambie_ el tamanio de la RAM al doble.
7. Hacer la función `cambiarProcesador(unaCompu,unProcesador)` que reciba una compu y un procesador y _cambie_ el procesador por el indicado.
8. Hacer la función `cambiarMemoria(unaCompu,unaMemoria)` que reciba una compu y una Memoria y _cambie_ la memoria entera por la indicada.
9. Hacer la función `overclockear(unaCompu)` que reciba una compu y aumente la velocidad de su procesador en 300 MHz. (debe denotarse la compu).
10. Hacer la función `quemarMemoria(unaCompu)` que reciba una compu y disminuya a la mitad el tamanio de la memoria (debe denotarse la compu)
