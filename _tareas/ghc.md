---
layout: default
title: GHC para Profesores
permalink:  ghc
classroom: 
date: 0000/08/01
toc: true
---

# {{ page.title}}

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
2. El profesor da nombre a la tarea y toma otras decisiones para
la tarea, 
  * si los estudiantes tienen derechos de administrador sobre los repos creados
  * si los repos serán públicos, 
  * Si se usará la versión de VSCode en la nube de GitHub denominada CodeSpaces
  * etc.
3. Una vez que el profesor rellena los detalles de la tarea, GHC genera una
enlace de invitación (URL)
4. Este enlace se pone a disposición de los estudiantes via el LMS (Moodle u otro) u otro mecanismo
5. Cuando los estudiantes hacen click en el enlace y aceptan la invitación, obtienen su propio clon del repositorio plantilla. Los repositorios tienen nombres consistentes formados por el nombre de la tarea y el nombre de usuario del alumno.
6. Los estudiantes completan el trabajo en el repo creado
7. Los profesores  tienen acceso completo a todos los repositorios y pueden dar retroalimentación al alumno y evaluarle

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


## Instrucciones para la Tarea

* Crea una asignación Individual GHC para tu clase
* Crea una asignación de grupo GHC para tu clase

Te será útil leer el artículo

* [GitHub in the Classroom: Lessons Learnt]({{ site.baseurl}}/assets/pdfs/github-in-the-classroom-lessons-learnt.pdf) por Yu-Cheng Tu, Valerio Terragni, Ewan Tempero, Asma Shakil,
Andrew Meads, Nasser Giacaman, Allan Fowler, Kelly Blincoe. University of Auckland, [The Australasian Computing Education Conference](https://aceconference.wordpress.com/previous-conferences/), February 14–18, 2022, Virtual Event, Australia


## Referencias

{% include github-education-references.md %}