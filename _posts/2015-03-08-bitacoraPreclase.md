---
layout:     post
title:      "Bitácora Pre Clase 2016-02-29"
subtitle:   "Bitácora de la clase del lunes 29/02/2016"
date:       2016-03-08 15:15:00
author:     "Alf"
---

¡Buenas! Lo prometido es deuda: acá está la bitácora de la "clase 0". Es decir, la clase que organizamos para conocernos, y que con Fede sentimos que fue todo un éxito.

Un éxito porque:

* **Asistencia**: ¡Estuvimos casi todos! Pasó algo raro, que es que tanto Fede como yo estuvimos juntos dando clase (eso no sucederá seguido), y hasta nos visitó Lucrecia (¡Gracias por pasarte!). 
    De las víctimas -estemmm digo, alumnos- estuvieron todos, salvo Natalia (¡No importa, che, nos ponemos a tono rápidamente!). 
    Eso sí, intenten **no perderse ninguna clase**. El curso es intensivo, y si bien haremos lo posible para brindarles material necesario, no se puede confiar en eso.
* **Desarrollo de temas**: Estamos contentos porque pudimos hacer una introducción a lo que se tratará el curso, hacer ejercicios individuales y otros juntos.
    Abajo un resumen.
* **Presentaciones**: Nos conocimos, hablamos sobre lo que hace cada uno. Igual, nos queda pendiente hablar con 3 ó 4 que llegaron más tarde y se perdieron esto. Es importante conocernos, y era el objetivo principal de la clase. Como pudimos hacerlo, decimos finalmente que fue un éxito.

Entonces, basta de preámbulo, vamos a la posta:

## Resumen administrativo
* Los **horarios** de las clases de Introducción a la Programación serán:

    Martes de 17hs a 20:45hs (profe: Fede).
    
    Jueves de 17hs a 20:45hs (profe: Alf).
* La comunicación **oficial** se hará por la lista de mails *obligatoria* [inpr-sarmiento@googlegroups.com](mailto:inpr-sarmiento@googlegroups.com).

    Deben revisar su mail *diariamente*.
* La **referencia** teórica y de material que tendrán, será *esta página actual* [http://inpr-sarmiento.github.io](http://inpr-sarmiento.github.io)

    Aquí se subirán las **bitácoras** que son resúmenes de clase, los *links* a la *bibliografía*, y a los *tutoriales* de uso de herramientas, etc.

## Resumen de teoría

* Hicimos un juego en el que Fede era nuestro **autómata** (un "robot" que sabe **ejecutar** un **programa**). El programa lo escribimos en el pizarrón **antes** de que Fede lo siga, y lo que escribimos fue una serie de **comandos**.
   Para decirlo con palabras menos chetas, primero escribimos un montón de flechitas una abajo de la otra en el pizarrón, y cuando le dábamos "play" a Fede, él las leía y daba un paso por cada flechita.
   
   Ahora bien, algunas flechitas le indicaban que debía "girar" y otras que debía "abrir una puerta". Acá una pequeña transcripción del programa:
   
   ![Primer programa](/img/2016-02-29/programaFede.png)
   
   ¿¿Y qué logramos con esto??
   Logramos concretar un **objetivo**: que Fede esquive una mesa y llegue a abrir la puerta. Todo **programa**, entonces, cuando lo *ejecutás*, **resuelve un problema**. 
* Jugamos con el [Lightbot](http://armorgames.com/play/2205/light-bot)(en la pc) y con la versión para celu ([MyBot](https://play.google.com/store/apps/details?id=com.anujraghav.mybot)).
* De este juego sacamos tres ideas muy importantes.
    1. Primero, cuando escribo un programa tengo que aprender a **imaginar qué hará mi autómata**. Esta capacidad de "ejecutar el programa en mi cabeza" es muy importante.
    Para ilustrar esto, hicimos un pequeño juego en el pizarròn, en el que había que decir què programas resolvían el problema de "subirse a la tarima":
    
        ![¿Qué programa me sube a la tarima?](/img/2016-02-29/elegirPrograma.png)
    
    2. Segundo, siempre tengo que **pensar antes mi estrategia**. ¡No vale probar hasta llegar!. Como se ve en la imagen anterior, hay **distintas estrategias** para resolver el mismo problema, y **mi programa debe ajustarse a mi estrategia elegida**.
    3. Tercero y último, aprendimos la idea de **procedimiento**. Un procedimiento es un **nuevo comando** que yo puedo agregar a mi programa, y que *podemos programar qué significa ese comando*.
    
        ¿Para qué sirven los procedimientos? Para algo muy importante:
    
        Un **procedimiento** me permite dividir mi **estrategia** en varias partes. 
    
        Recuerden el nivel 7 del Lightbot, que se ve así:
    
        ![Nivel 7](/img/2016-02-29/nivel7.png)
    
        Con dos procedimientos: uno que significa "prender 6 luces" y otro que significa "prender las dos de la punta", nuestro programa tiene sólo tres comandos:
    
        * Prender 6 luces
        * Prender las dos de la punta
        * Prender 6 luces
   
        Y eso ya resuelve nuestro problema, y **gracias a los procedimientos, podemos leer mejor nuestro programa, y dividir la estrategia en tres partes**.
    
    4. ¡Opa! Un cuarto corolario inesperado: Un programa se escribe para que **un autómata lo ejecute** pero también para que **una persona lo lea**. ¡Estamos escribiendo literatura, también! Bueno, más o menos.

Un pequeño mapa conceptual:

![Mapa Conceptual](/img/2016-02-29/mapaConceptos.png)

## Tarea Obligatoria para la clase 1 (¡El martes que viene!)
1. Sólo para Natalia, inscribirse a Mumuki, entrando a este link [http://inpr-sarmiento.classroom.mumuki.io/#/courses/2016s1/students](http://inpr-sarmiento.classroom.mumuki.io/#/courses/2016s1/students) y loguearse.
2. Para todos: si no lo hicieron ya, hacer los trece ejercicios de esta guía: [http://inpr-sarmiento.mumuki.io/chapters/1-fundamentos](http://inpr-sarmiento.mumuki.io/chapters/1-fundamentos)
    Si tienen algún problema, no duden en preguntar.
3. Opcionalmente (pero recomendado) es volver a jugar con el Lightbot ó el MyBot, ó con la nueva versión del [Lightbot](https://lightbot.com/hocflash.html) (también está para celu).

    De esto, lo más **importante** es la práctica que hagan con el uso de **procedimientos** para resolver cada **parte** de mi **estrategia**.
