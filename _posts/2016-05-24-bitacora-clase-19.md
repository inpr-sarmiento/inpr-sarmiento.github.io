---
layout:     post
title:      'Registros recargados'
subtitle:   "Bitácora de la clase del martes 24/05/2016"
date:       2016-05-24 15:30:00
author:     "Fede"
---

# Práctica Universidad - registros

### Parte 1: más sobre registros

Ahora juguemos con un tipo `Fecha`, que tiene día, mes y año:

```gbs
type Fecha is record {
  field dia
  field mes
  field anio
}
```

1. Hacé la función `esAniversarioRevolucionDeMayo(fecha)` que dice si esa fecha es el 25 de Mayo.
2. Hacé la función `esDiaIndependencia(fecha)` que dice si esa fecha es el 9 de Julio.
3. Hacé la función `esPrimerCuatri(fecha)`, que dice si esa fecha es del primer cuatrimestre.
4. Codificá `esFeriado(fecha)`, asumiendo que sólo son feriados el Aniversario de la Revolución de Mayo y el Día de la Independencia. 
5. `finDeMes(fecha)`, que indique si nos acercamos al fin del mes (digamos, del 20 en adelante).
6. `esDiaDeNioquis(fecha)`, que mire si el día es 29.
7. `mismoAnio(fecha1, fecha2)` y `mismoMes(fecha1, fecha2)`.
8. Usando las dos anteriores: `esMasAntigua(fecha1, fecha2)`. Ojo, es un poco largo, pensá bien la estrategia y todos los casos posibles.
9. `cuantosAniosPasaron(fecha1, fecha2)`. Bonus: contemplar la posibilidad de que todavía no haya llegado la fecha.
10. `primerDiaInvierno(anio)` que tome un año y devuelva el primer día de invierno de ese año.
11. `ultimoDiaInvierno(anio)` que tome un año y devuelva el último día de invierno de ese año.
12. `esInvierno(fecha)` que denote si es un día de invierno en Argentina (21 de Junio - 20 de Septiembre). Sale fácil con `esMasAntigua` y las dos anteriores.
13. Siguiendo la misma estrategia de los últimos ejercicios, hacé `esVerano()`, `esOtonio()` y `esPrimavera()`.
14. Usando todo lo anterior, implementá `estacion(fecha)` que devuelva el color correspondiente a la estación del año que ocurre en esa fecha: **Rojo** para el verano, **Negro** para el otoño, **Azul** para el invierno y **Verde** para la primavera.

### Parte 2: registros con registros

Tenemos ahora un `Estudiante`, modelado con fecha de nacimiento, DNI, número de materias aprobadas y un campo que nos indica si es mujer.

```gbs
type Estudiante is record {
  field fechaNacimiento
  field dni
  field nroMateriasAprobadas
  field esMujer
}
```

1. Asumiendo que existe una función `diaDeHoy()` que devuelve qué día es hoy, escribí `edad(estudiante)`, usando `cuantosAniosPasaron`. Para poder probarlo, escribí efectivamente la función `diaDeHoy()` con cualquier fecha que te quede cómoda para hacer las cuentas (como por ejemplo, el día en el que estés haciendo estos ejercicios).
2. `elMasViejo(estudiante1, estudiante2)`, que devuelva al estudiante más viejo.
3. Se lanzó una beca para estimular las vocaciones TIC, destinada a mujeres de entre 18 y 35 años. Codificá `puedeRecibirBeca(estudiante)` que indique si un estudiante podría pedir la beca.
4. `esIngresante(estudiante)`, que nos indique si es ingresante: no tiene que tener materias aprobadas.
5. `estaAvanzado(estudiante)` que nos indique si un estudiante está avanzado en la carrera. Esto es así si ya aprobó más de la mitad de las materias, que son 30 en total.
6. En la búsqueda de auxiliares académicos, nos pidieron encontrar una pareja pedagógica que cumpla ciertos requisitos: ambos estudiantes avanzados, de la misma edad y distinto sexo. Programá la función `puedenSerParejaPedagogica(estudiante1, estudiante2)` que indique eso.
7. `podriaSerElPadre(estudiante1, estudiante2)` que indique si la primera persona podría ser el padre de la segunda. Digamos que para que esto sea cierto debe ser **al menos** 18 años más grande.
8. `nacioEnArgentina(estudiante)` que nos indique si un estudiante nació en Argentina. ¿Cómo darse cuenta? Fácil, los ciudadanos extranjeros tienen DNIs con números mayores a 90.000.000.
9. Desde la Secretaría de Inclusión de la Universidad nos pidieron desarrollar una función que determine si un estudiante se encuentra dentro del grupo vulnerable, para poder realizar un seguimiento especial sobre ellos. Escribí la funcion `estaEnGrupoVulnerable(estudiante)` teniendo en cuenta las siguientes reglas (te conviene **mucho** dividir en subtareas y prestar especial atención a **todo lo definido** hasta ahora): 
    * los migrantes menores de 21 años lo son, por el riesgo de no poder sustentarse económicamente y tener que volver a sus países;
    * las mujeres entre 25 y 35 años también están incluidas, por la posibilidad de quedar embarazadas y tener que dejar la Universidad;
    * todos los ingresantes lo son, porque pueden sentirse abrumados por la exigencia y verse tentados a abandonar.
