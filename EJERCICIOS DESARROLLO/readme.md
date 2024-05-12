# Comentarios de los profesores sobre los ejercicos:

### Ejercicio 1
La estructura utilizada no son las esperadas para un trabajo universitario. No se justifica nada.
No se incluyen datos del alumno, materia, año, ejercicio, etc. No hay formato.
No se identifican stakeholders negativos
Los desarrolladores y otros roles del equipo de construcción de la aplicación no corresopnden a la capa 1 sino a la de "Wider Envoronment", que es la 4ta.
Los alumnos y empleados administrativos no son beneficiarios funcionales sino usuarios del sistema.

### Ejercicio 2
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

### Ejercicio 3
1) Tangerine debe primero entregar las transacciones para que el Administrador las pueda consultar.

2) Cada historia debe tener sus propios objetos de trabajo. "Cuotas" se comparte entre tres historias diferentes.

3) No queda claro qué implica asignar cuotas a la factura. ¿Cómo se lee la historia? "Administrador establece cuota se le asigna a factura"? En ese caso, "se le asigna" es una acción -> no puede haber actividades entre objetos. Siempre es un actor en que ejecuta una actividad empleando uno o varios objetos de trabajo.

4) No se modeló el tratamiento de los recargos (debería ser una historia separada)

### Ejercicio 4
Van nuestros comentarios:
(MC: muy crítico; C: crítico; NC: no crítico)

No era necesario "particionar" el modelo.

1) Se modelan incorrectamente las asociaciones. Como se explicó varias veces en clase (y en el vídeo) las asociaciones no son flechas. Una asociación que termina con una punta de flecha tiene un significado muy preciso en UML, que tiene que ver con la implementación y no con el modelado conceptual. Adicionalmente, faltan algunos nombres de asociaciones (C)

2) No se resuelve el requisito de identificar en qué aulas, días y horarios se da un curso en un cuatrimestre determinado. Si bien hay dos atributos en curso, día y horario, no se puede determinar la correlación entre los días y los horarios. Adicionalmente, no se puede saber, para cada día-horario, qué aulas tocan, ya que todo el curso está asociado a 1..* sedes, y cada sede tiene 0..* aulas. (MC).

3) Se modelan incorrectamente las materias aprobadas y las no aprobadas. Por la aclaración, se supone que es una estructura de generalización/especialización, pero la notación es incorrecta. Dejando de lado la notación, no es posible que las materias aprobadas sean una especialización de materia: no es así que funcionan estas estructuras. Para cada instancia del "supertipo" habrá siempre una instancia de uno de los "subtipos" En este caso, se entiende que se quiso modelar que para una instancia de materia hay muchas instancias de materia aprobada.Esto no funciona así. Por favor, consultar [Larman]
Adicionalmente, no se sabe qué alumnos aprobaron (MC)


4) Se modela incorrectamente la correlatividad entre materias. La asociación debe ser 0..* a 0..*. Tal como está, es infinita (esto se explicó en clase y en el vídeo correspondiente)

5) Se modelan incorrectamente las actas, ídem punto anterior. Adicionalmente, no se sabe a qué alumnos corresponden las notas (MC)

6) El recargo por pago tardío se debe aplicar a la factura, no a la cuota.

### Ejercicio 5