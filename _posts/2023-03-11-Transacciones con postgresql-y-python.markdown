---
title:  "Transacciones con PostgreSQL"
date:   2023-11-02 22:38:00
categories: [Video-Tutoriales]
tags: [Video-Tutoriales]
---

Una transacción de base de datos es una serie de una o más operaciones ejecutadas como una única unidad atómica de trabajo. Esto significa que, o bien todas las operaciones de la transacción se completan con éxito, o bien ninguna de ellas se aplica a la base de datos.

<img class="centrar" src="/images/rollback.jpg" alt="Rollback">

En la siguiente imagen veremos el estado actual de una tabla de nuestra base de datos a la que posteriormente editaremos un registro y añadiremos otro dentro de una operación de transacción conjunta mediante un script de python.

<img class="centrar" src="/images/bd001.png" alt="postgresql admin1">

En el siguiente script pueden ver el código utilizado para la transacción de las dos operaciones que modifican la tabla, pero añadimos un error para ver como se se realiza el Rollback y la tabla no sufre alteración alguna. 


<img class="centrar" src="/images/bd002.png" alt="Rollback_001">

En la siguiente imagen vemos el resultado de la ejecución

<img class="centrar" src="/images/bd003.png" alt="Rollback_001">

Ahora pueden comprobar que la base de datos sigue tal cual estaba.

<img class="centrar" src="/images/bd004.png" alt="Rollback_001">

En la siguiente imagen corregimos el error generado a proposito.

<img class="centrar" src="/images/bd005.png" alt="Rollback_001">

Ahora pueden ver la ejecución del script.

<img class="centrar" src="/images/bd006.png" alt="Rollback_001">

finalmente le muestro la imagen de los cambios efectuados.

<img class="centrar" src="/images/bd007.png" alt="Rollback_001">

Esto es una pequeña demostración. Para ver otras publicaciones al respecto
pueden encontrarme en  [LinkedIn][linkedin]

[linkedin]: https://www.linkedin.com/in/e-cabrera-blazquez/





