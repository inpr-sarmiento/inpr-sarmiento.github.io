---
layout:     post
title:      'Registros con listas y listas de registros'
subtitle:   "Bitácora de la clase del martes 14/06/2016"
date:       2016-06-14 23:17:00
author:     "Fede"
---

### Temas de clase
* Repaso de los esquemas vistos hasta el momento, miren la guía de recorridos de listas que está en la sección Material.
* Introdujimos el `foreach` como una herramienta útil para realizar **recorridos completos** sobre listas. Básicamente resuelve por nosotros el problema de recorrer una lista **de izquierda a derecha** y en cada iteración podemos "mirar por dónde va" accediendo a la variable.
* Vimos que los registros pueden tener **campos que guardan listas** y las listas pueden **estar compuestas por registros**. Para ejercitar esto, continuamos con la práctica de los estudiantes universitarios.

Deben terminar de resolver **los primeros cuatro ejercicios de la segunda parte** y enviarlos por mail - incluyan también las funciones que utilicen en su resolución.

# Práctica Universidad - listas

### Parte 3: registros con listas y listas con registros
Vamos a reemplazar el campo `nroMateriasAprobadas` por una lista de las notas obtenidas, y agregamos también otra lista para registrar los aplazos:

```gbs
type Estudiante is record {
  field fechaNacimiento         // Fecha
  field dni                     // número
  field notasMateriasAprobadas  // lista de números
  field aplazos                 // lista de números
  field esMujer                 // booleano
}
```

1. Escribí funciones que sirvan para calcular la `longitud`, `sumatoria` y el `promedio` de una lista de números y guardalas en tu Biblioteca. Tenelas muy en cuenta para programar los siguientes ejercicios.
1. Para que siga funcionando todo lo que ya escribimos hasta ahora, programá la función `nroMateriasAprobadas` que indique cuántas materias aprobó un estudiante. **Para pensar, cuando hayas terminado:** al modificar la estructura de nuestro registro, la cantidad de materias aprobadas ya no está explícitamente en ningún campo pero aún así se puede calcular, reemplazando lo que antes era un _proyector_ por una función que escribimos nosotros. Lo interesante es que ¡todo sigue funcionando! - después de todo, los _proyectores_ también son funciones.
2. Para realizar distintos trámites dentro de la Universidad, el Departamento de Alumnos necesita poder determinar el `promedioSinAplazos` y el `promedioConAplazos` de un estudiante. Programá ambas funciones.
3. El Consejo Interuniversitario Nacional otorga becas de Estímulo a las Vocaciones Científicas para aquellos estudiantes que deseen iniciar su formación en la investigación. Como requisitos, piden que quien se presente esté avanzado en la carrera (ver parte anterior), tenga a lo sumo 30 años y un promedio con aplazos de al menos seis puntos. Escribí la función `aptoBecaEvcCin` que determine si un estudiante podría postularse.

A partir de la lista de todos los estudiantes de TPI, queremos obtener una serie de estadísticas. Desarrollá una función para cada uno de los siguientes puntos:

1. una lista con los `promediosConAplazosDe` todos ellos;
1. el `promedioHistoricoConAplazos`, un número que se calcula sacando el promedio de los promedios de todos los estudiantes;
1. la lista de `estudiantesMujeres` que estudian la carrera;
1. el `porcentajeDeMujeres` que estudian la carrera. Recordá que para calcular un porcentaje tenés que dividir la porción que te interesa (en este caso las mujeres) con el total de elementos (en este caso todos los estudiantes) y multiplicar eso por 100.
1. una lista con las `edades` de todos los estudiantes;
1. una lista con las `edadesMigrantesVarones`;
2. la lista de los `estudiantesAvanzados`;
3. la lista de los `estudiantesIngresantes`;
4. la `cantidadEstudiantesEnGrupoVulnerable`.