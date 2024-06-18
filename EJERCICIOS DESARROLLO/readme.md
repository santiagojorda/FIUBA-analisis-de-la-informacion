# Comentarios de los profesores sobre los ejercicos:

## Ejercicio 1
~~~
1) La estructura utilizada no son las esperadas para un trabajo universitario. No se justifica nada.

2) No se incluyen datos del alumno, materia, año, ejercicio, etc. No hay formato.

3) No se identifican stakeholders negativos

4) Los desarrolladores y otros roles del equipo de construcción de la aplicación no corresopnden a la capa 1 sino a la de "Wider Envoronment", que es la 4ta.

5) Los alumnos y empleados administrativos no son beneficiarios funcionales sino usuarios del sistema.
~~~


## Ejercicio 2
~~~
1) Administración de Sedes y Aulas
OK. Podría ser "actualiza sede" y no "sedes". Lo mismo con las aulas. No se actualiza todo junto, ¿no?

Adicionalmente, es importante recordar que cada historia debe tener sus propios objetos (Aulas debería dibujarse dos veces)

Además, un aula no es de un curso (se entiende que se comparte entre varios) No parece relevante establecer ese vínculo en la oración.

2) Administración de Alumnos
OK. Quedaría mejor "actualiza alumno" y no "datos de alumnos"

3) Administración de Docentes
OK. Mismo comentario con respecto al uso del plural y del prefijo "datos" (a la larga, los objetos de trabajo son datos)

4) Administración de Planes de Estudio
Misma observación con respecto al uso del plural.

5) Administración de Oferta Académica
Mismo comentario que más arriba: no se pueden compartir objetos de trabajo entre historias. Hay que repetirlos.

6) Administración de Inscripciones
Mismo comentario del punto anterior. Curso debería dibujarse más de una vez.

Adicionalmente, las historias están fuera de su secuencia lógica.

Hay que corregir la redacción. Hay historias que suenan mal: por ejemplo, "Alumno consultar historia académica contiene materias aprobadas" -> Mejor: "Alumno consulta historia académica"

La consulta de facturas no parece ser de este dominio...

7) Administración de Cursos
OK

8) Administración de Aranceles

Incompleto.
~~~


## Ejercicio 3
~~~
1) Tangerine debe primero entregar las transacciones para que el Administrador las pueda consultar.

2) Cada historia debe tener sus propios objetos de trabajo. "Cuotas" se comparte entre tres historias diferentes.

3) No queda claro qué implica asignar cuotas a la factura. ¿Cómo se lee la historia? "Administrador establece cuota se le asigna a factura"? En ese caso, "se le asigna" es una acción -> no puede haber actividades entre objetos. Siempre es un actor en que ejecuta una actividad empleando uno o varios objetos de trabajo.

4) No se modeló el tratamiento de los recargos (debería ser una historia separada)
~~~

## Ejercicio 4
~~~
(MC: muy crítico; C: crítico; NC: no crítico)

No era necesario "particionar" el modelo.

1) ✅ Se modelan incorrectamente las asociaciones. Como se explicó varias veces en clase (y en el vídeo) las asociaciones no son flechas. Una asociación que termina con una punta de flecha tiene un significado muy preciso en UML, que tiene que ver con la implementación y no con el modelado conceptual. Adicionalmente, faltan algunos nombres de asociaciones (C)

2) ✅ No se resuelve el requisito de identificar en qué aulas, días y horarios se da un curso en un cuatrimestre determinado. Si bien hay dos atributos en curso, día y horario, no se puede determinar la correlación entre los días y los horarios. Adicionalmente, no se puede saber, para cada día-horario, qué aulas tocan, ya que todo el curso está asociado a 1..* sedes, y cada sede tiene 0..* aulas. (MC).

3) Se modelan incorrectamente las materias aprobadas y las no aprobadas. Por la aclaración, se supone que es una estructura de generalización/especialización, pero la notación es incorrecta. Dejando de lado la notación, no es posible que las materias aprobadas sean una especialización de materia: no es así que funcionan estas estructuras. Para cada instancia del "supertipo" habrá siempre una instancia de uno de los "subtipos" En este caso, se entiende que se quiso modelar que para una instancia de materia hay muchas instancias de materia aprobada.Esto no funciona así. Por favor, consultar [Larman]
Adicionalmente, no se sabe qué alumnos aprobaron (MC)

4) ✅ Se modela incorrectamente la correlatividad entre materias. La asociación debe ser 0..* a 0..*. Tal como está, es infinita (esto se explicó en clase y en el vídeo correspondiente)

5) ✅ Se modelan incorrectamente las actas, ídem punto anterior. Adicionalmente, no se sabe a qué alumnos corresponden las notas (MC)

6) ✅ El recargo por pago tardío se debe aplicar a la factura, no a la cuota.
~~~

## Ejercicio 5
~~~
a) Actualización de cuotas
El objetivo de la historia no es adecuado (siempre vamos querer actualizar algo para mantenerlo actualizado...Hay que tratar de determinar cuál es el valor para el usuario)

Se debe ser más específico en la formulación de los escenarios. Por ejemplo:

"Dado que hay una cuota para el periodo 2024/04 con un arancel de $XXX

Cuando se modifica el arancel de la cuota a $YYY

Entonces se registra el nuevo arancel de la cuota como $YYY"

"Dado que hay una cuota para el periodo 2024/04 y que ya se han generado las facturas para dicho periodo
Cuando se quiere modificar el arancel de la cuota
Entonces se informa que no es posible modificar el arancel de una cuota ya facturada a los alumnos"


b) Generación de facturas
La historia plantea la generación de facturas de a un alumno por vez. Este es un proceso por lotes.

No se explica cómo se calcula el recargo.

c) Envío de facturas
Forma parte de la emisión.

d) Recargos
Se incluye -correctamente- en la historia de generación de la factura (aunque no se indica claramente cómo es el cálculo del recargo) Pero también se incluye en la historia de recepción de las transacciones.

e) Regularidad
"Dado una administrador de cobranzas" no es un contexto.
No se indica que información contiene la notificación.
Hay una historia para la reincorporación, pero se habla en los CA de "iniciar el trámite de reincorporación" pero no se describe cómo es ese trámite.

f) Envío de transacciones de pago
Hay varias validaciones que habría que hacer y que no están reflejadas. Por ejemplo, que las transacciones correspondan a alumnos/facturas válidas; que correspondan a facturas que estaban impagas hasta el momento; etc.

Se aplica un recargo del 5% en la siguiente factura...¿Cómo se hace si la factura aún no se emitió? Por otro lado, el recargo se indica en la historia correspondiente a la generación de la factura. ¿Se aplica dos veces?
~~~

## Ejercicio 6
~~~
a) General
Buen layout. Se emplearon datos reales.

b) Definición y actualización de cuotas
Se podría haber arrancado con una lista de cuotas para que el usuario elija cuál modificar. Bien los controles. Faltaría la opción de crear una cuota (es lo que sucede a principios de año)

c) Generación y envío de facturas
Falta la generación y envío de las facturas.
Los alumnos reciben notificación cuando hay una nueva factura disponible.

d) Transacciones Tangerine
Hay una consulta de las transacciones.

e) Regularidad
Hay una pantalla para consultar cuáles alumnos pierden la regularidad.

f) Recargos
Se muestra en las facturas.


Ej.4: MDD

Hay varios temas que no están bien.
a) Factura no puede ser asociativo si tiene identificador propio.

b) Historia académica no tiene atributos. No puede haber objetos sin atributos.

c) Acta no puede ser asociativo entre curso y docente. Cada curso tiene varios docentes. Por consiguiente, para un mismo curso habrá tantas actas como docentes haya asignados.

E5: HDU

1) Actualización de cuotas: replantear el propósito. No se puede justificar la actualización de algo para que esté actualizado.

"Dado un administrador..." no es un estado del sistema.

2) Se debe ser más preciso en los criterios, en general.

3) Falta la generación de las facturas. No se sabe de dónde salen.
~~~


## Ejercicio 7
~~~
"en el diseño de base de datos relacional debería haber una tabla para cada teléfono (alumno, sede y docentes) y no una cadena como lo incluí en el trabajo entregado."

a) En tabla_factura falta la FK a tabla_cuota.

b) No hay manera de saber a qué alumno corresponde una factura (falta la FK)

c) Se plantean varias relaciones muchos a muchos entre dos tablas (no es posible en una BDR)

d) Se modela incorrectamente la relación entre las correlativas y las materias.

e) Se arrastra el error de inscribir al alumno en un curso y no a un curso y a un cuatrimestre.

f) Adicionalmente, hay una tabla_inscripción entre tabla_cuatrimestre y tabla_curso. No se entiende para qué sirve.


Ejercicio 4: MDD

a) Pago no puede ser OA, ya que las facturas primero se generan y luego se pagan. Tal como está, el pago existe siempre que exista la factura.

b) Si el Acta es de cursada, no tiene sentido tener asociado un objeto con dos atributos, una de final y otra de cursada.

c) Un Alumno debe poder inscribirse en un Curso de un Cuatrimestre (tal como está, no sabemos cuándo cursará la materia)

d) No se normalizan los teléfonos.

Ejercicio 5: HDU

a) El "Dado" debe describir el estado del sistema, no las acciones o los eventos.
~~~


## Ejercicio 8
~~~
a) Buena elección de fuentes y colores base.

b) Algunas pantallas podrían tener mejor diseño. Por ejemplo, Mis Facturas plantea botones. Hubiera sido mejor plantear una grilla y seleccionar desde ahí cuáles visualizar.

c) Algo similar ocurre con el menú de Administración. ¿No se podría haber optado por un menú más tradicional, en la parte superior de la pantalla?


Ejercicio 5: HDU
"Dado que un empleado está en el sistema" no es una precondición válida.
~~~