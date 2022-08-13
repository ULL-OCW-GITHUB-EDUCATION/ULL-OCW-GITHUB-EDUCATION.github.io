---
layout: default
title: GHC para Profesores
permalink:  ghc
classroom: 
date: 0000/08/01
toc: true
---

# GitHub Classroom para Profesores

## Objetivos

* Conocer que es [GitHub Classroom](https://classroom.github.com) desde la perspectiva del profesor 
* Crear una asignación Individual GHC
* Crear una asignación de grupo GHC
* Mejorar nuestra eficiencia en procesos de evaluación usando `ghc` 

## GitHub Classroom

Github Classroom (GHC) es "una herramienta para profesores que utiliza la API de GitHub para habilitar el flujo de trabajo de GitHub para la educación". GHC permite la creación de "aulas" y "asignaciones" dentro del aula. Las "aulas" o "classrooms" proporcionan los medios para organizar tareas para un curso, repositorios para las tareas y estudiantes para los repositorios.

El proceso de gestión de asignaciones es el siguiente:

1. El profesor crea una tarea, que debe estar asociada con un
repo
  * El repositorio debe ser un repositorio de plantilla. 
2. El profesor da nombre a la tarea.
  * Si la tarea es configurada como de grupo, este campo permite distinguir los diferentes conjuntos de equipos. Si ya existe un conjunto previo de equipos, aparece una opción para seleccionarlo(o bien se puede definir un nuevo conjunto de equipos). Si se elige un conjunto existente de equipos, cuando los estudiantes acepten la tarea no necesitarán seleccionar a que equipo quieren pertenecer)
3. El profesor toma otras decisiones para la tarea: 
  * Si los estudiantes tienen derechos de administrador sobre los repos creados. 
  Para cursos pequeños y en los que los alumnos no tengan conocimientos puede que sea preferible no darles derechos de admin, sin embargo, en general es una buena idea darles permisos de admin.
  Aunque los estudiantes tengan derechos de admin sobre sus repos, [es posible aplicar restricciones sobre los miembros a nivel de organización](https://docs.github.com/en/organizations/managing-organization-settings/setting-permissions-for-deleting-or-transferring-repositories). Por ejemplo evitar que  los estudiantes pueden eliminar un repositorio, transferirlo a otra cuenta o cambiar su visibilidad.
  * Si los repos serán públicos o privados. Los repositorios deben ser privados cuando se quiera evitar el plagio. 
  * Si se usará la versión de VSCode en la nube de GitHub denominada CodeSpaces
  * etc.
3. Una vez que el profesor rellena los detalles de la tarea, GHC genera una
enlace de invitación (URL)
4. Este enlace se pone a disposición de los estudiantes via el LMS (Moodle u otro) u otro mecanismo
5. Cuando los estudiantes hacen click en el enlace y aceptan la invitación, obtienen su propio clon del repositorio plantilla. Los repositorios tienen nombres consistentes formados por el nombre de la tarea y el nombre de usuario del alumno.
6. Los estudiantes completan el trabajo en el repo creado
7. Los profesores  tienen acceso completo a todos los repositorios y pueden dar retroalimentación al alumno y evaluarle

## El problema de Enlazar las Cuentas GH con las cuentas del LMS

Si bien los repositorios creados al aceptar una invitación de asignación de GHC tienen
un esquema de nombres consistente, **parte del nombre es la cuenta de GH
nombre elegido por el estudiante**. La siguiente figura muestra un ejemplo para una tarea denominada `p5-t3-websockets`: 

<img src ="{{site.baseurl}}assets/images/github-classroom-naming-scheme.png" width="70%"/>


Mientras que el problema de encontrar el repositorio de un estudiante en particular se hace más fácil debido a la consistencia del esquema, en una clase grande aún puede requerir bastante tiempo. Por ejemplo, en la imagen anterior:

¿Que alumno es `dreamz11`? ¿Cual es su identificador en el LMS?
¿Como se llama el alumno?

El problema de identificación es mas fácil con la tarea `p5-t3-websockets-alu0101037653` ya que el alumno ha hecho coincidir su login GitHub `alu0101037653` con su identificador dentro de nuestra Universidad. Tendré ahora que ver que alumno es `alu0101037653`. 
De hecho una solución parcial al problema es solicitar a los alumnos que tengan una cuenta github cuyo login coincida con su identificador en el LMS. Obviamente no todos los alumnos van a seguir esas instrucciones.

### Primera Soluciòn: GHC Rosters


GHC aborda este problema permitiendo que los profesores suban una [lista o GHC roster](https://docs.github.com/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom/manage-classrooms#about-classroom-rosters)
para cada GHC classroom.

Los profesores pueden cargar la lista de los estudiantes en su curso a
el correspondiente GHC classroom, y posteriormente en las aceptaciones de las subsiguientes
asignaciones los repositorios de los estudiantes son  vinculados
al GHC roster. Esto permite que los repositorios se encuentren usando el
identidad universitaria.

Hay dos maneras para que los profesores creen la lista de
los alumnos en sus cursos.

1. Los profesores pueden importar manualmente una lista cargando un CSV o un archivo de texto que contiene el ID en la institución del estudiante.
2. Pueden importar la lista de un sistema de gestión de aprendizaje (LMS) como Canvas o Moodle.

Para asociar los alumnos a sus cuentas de GH, los estudiantes deben identificarse en el roster y manualmente
vinculan sus cuentas cuando aceptan por primera vez la asignación de GHC.

Sin embargo, hay varios problemas: 

* La conexión entre el LMS y GHC no vincula automáticamente las cuentas de GH de los estudiantes con la lista de GHC. Se requiere que los estudiantes vinculen manualmente sus cuentas. 
* Si los estudiantes eligen accidental o maliciosamente el nombre de la lista, entonces los instructores tendrían que desvincular las cuentas.
* Otro problema es que solo hay tres opciones para identificar cada estudiante en la lista:

                 ID de usuario, nombres, correos electrónicos.

  En el caso de nuestra universidad el  correo electrónico de la universidad es consistente 
  con los identificadores de los estudiantes en el LMS, pero sabemos de casos en otras instituciones en los que el ID importados del LMS no siempre es equivalente al carnet de estudiante.

  A veces, encontramos  que los estudiantes no pueden encontrar sus correos electrónicos en la lista si la clase es grande. Además, a veces no son solo los estudiantes los que aparecen en la lista sino que pueden aparecer profesores y otro personal vinculado.

  Para manejar el GHC roster es mejor crear la lista manualmente, utilizando una combinación 
  nombre-del-estudiante-identificador-usuario. De hecho no hay necesidad de crear la lista 
  desde cero: Los profesores descargamos el roster del LMSs en CSV y lo procesamos con unas cuantas sustituciones (¡expresiones regulares al rescate!). 


### Segunda Solución: Asignaciones de Grupos 

Una solución equivalente a la anterior es hacer que todas las asignaciones individuales sean asignaciones de un grupo de tamaño uno e instruir al alumno para que cuando cree el grupo individual siga el esquema 
`nombre-apellidos-identificador`. Una vez creado ese conjunto de equipos será utilizado para el resto de tareas individuales del curso. La siguiente imagen muestra cuan sencillo es así obtener las tareas de un alumno si se recuerda el nombre o los apellidos del alumno o se dispone de su identificador:

<img src="assets/images/github-classroom-group-assignment-naming-scheme.png" width="70%"/>

## Branch Protection

En cursos donde los estudiantes trabajan en equipos y todos los miembros del equipo
tiene derechos de administrador en sus repositorios,
es conveniente aconsejar a los estudiantes  que añadan [reglas de protección de las ramas importantes](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/managing-a-branch-protection-rule) que les blinden 
contra una pérdida de datos debida a un `push --force`. 

Lo habitual en estos casos es que la configuren a 
**require pull request reviews before merging**
en la rama `main`. 


## Evaluación con GHC

El uso de Git, GitHub y GHC abre posibilidades de cómo el proceso de evaluación
puede llevarse a cabo. Es importante que el estudiante mantenga
su repositorio remoto actualizado. Es necesario recordarles a los estudiantes la conveniencia de 
hacer `git push` a menudo.

Hay una serie de opciones para que los profesores evalúen los repositorios.

Siempre que los instructores tengan acceso, es posible
clonar el repositorio de cada estudiante con alguna herramienta como 
[`gh org-clone -s iaas -n ULL-ESIT-DMSI-1920`](https://github.com/gh-cli-for-education/gh-org-clone)
o mejor [`gh submodule-add -C -o ULL-MFP-AET-2122 -s latex-markdown -r 'marrero|maury|coell'`](https://github.com/crguezl/gh-submodule-add).

La ventaja de `gh submodule-add` es que permite facilmente realizar con un sólo comando acciones sobre todos los repos de los alumnos usando `gh submodule foreach` (por ejemplo actualizarlos)

### Calificación Automática con GHC: autograding

GHC ofrece la opción, llamada *autograding*, que permite aplicar pruebas automatizadas a los envíos de los estudiantes. Esto lo hace añadiendo al repo del estudiante [GitHub Actions]({{ site.baseurl}}pages/github-actions) de manera que cada vez que el estudiante ejecuta un `push` se ejecutan las pruebas. 

En estos casos, lo habitual es que el profesor recicle las pruebas que tenga y las añada al template proporcionado y especifique en la asignación el lenguaje de las pruebas y como estas se ejecutarán. La figura muestra un caso para una asignación en la que el alumno desarrolla con node:

![]({{ site.baseurl }}assets/images/github-classroom-specify-autograding.png)

Esto no solo permite una guía mas cerrada y desacoplada 
con una evaluación “formativa”,
aumentando las posibilidades de que los estudiantes se ajusten a lo solicitado.

Además, los profesores también pueden añadir mediante un script en la fase de evaluación pruebas privadas no publicadas en sus clones/submódulos de los repositorios de estudiantes que darán lugar a la calificación final.


## Instrucciones para la Tarea

* Crea una asignación Individual GHC para tu clase
* Crea una asignación de grupo GHC para tu clase

Te será útil leer el artículo

* [GitHub in the Classroom: Lessons Learnt]({{ site.baseurl}}/assets/pdfs/github-in-the-classroom-lessons-learnt.pdf) por Yu-Cheng Tu, Valerio Terragni, Ewan Tempero, Asma Shakil,
Andrew Meads, Nasser Giacaman, Allan Fowler, Kelly Blincoe. University of Auckland, [The Australasian Computing Education Conference](https://aceconference.wordpress.com/previous-conferences/), February 14–18, 2022, Virtual Event, Australia


## Referencias

{% include github-education-references.md %}