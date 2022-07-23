---
layout: default
title: Aprender GitHub Classroom y Markdown
permalink: aprender-markdown
name: aprender-markdown
date: 0000/01/02
toc: true
---

# {{ page.title }}

## Objetivos

Deberás aceptar la tarea asociada a esta parte haciendo click en el [enlace de aceptación](https://classroom.github.com/a/PlGuI8vJ). Es una tarea que fue configurada por los profesores usando [GitHub Classroom](). Un primer objetivo de esta lección/tarea es conseguir cierta familiaridad con los conceptos que conlleva Github Classroom.

El otro objetivo de esta tarea es aprender Markdown. Para ello, en el repositorio que se crea cuando aceptas la asignación  deberás rellenar los contenidos del fichero `README.md` con un pequeño curriculum vitae/carta de presentación usando markdown. Es conveniente que 

1. Incluyas alguna imagen en el repo en una carpeta `img` y la muestres desde el texto
2. Añadas un segundo fichero en el repo con nombre  `objetivos.md`  contando cuáles son tus objetivos con respecto a este curso y lo referencies desde el fichero `README.md`. Añade una referencia/enlace  de vuelta en `objetivos.md` a  tu `README.md`



En este [enlace puedes visitar ejemplos de lo que han hecho algunos alumnos de la asignatura *Aprendizaje y Enseñanza de la Tecnología* del master de Formación de Profesorado en el curso 21/22](https://github.com/orgs/ULL-MFP-AET-2122/repositories?q=aprender-markdown&type=all&language=&sort=)


## Introducción a GitHub Classroom

Los profesores han configurado esta segunda tarea usando [GitHub Classroom](https://docs.github.com/es/education/manage-coursework-with-github-classroom/teach-with-github-classroom). GitHub Classroom es una aplicación web para los docentes que proporciona herramientas para la administración de cursos integradas con GitHub. 

Para aprender a usar esta herramienta es conveniente seguir el curso [Teach with GitHub Classroom](https://docs.github.com/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom). Puedes encontrar un buen número de vídeos que complementan el curso en la sección [Videos about GitHub Classroom](https://docs.github.com/en/education/manage-coursework-with-github-classroom/get-started-with-github-classroom/basics-of-setting-up-github-classroom#videos-about-github-classroom)

Esta tarea inicial ha sido configurada por el profesor como una tarea de equipo.

Eso significa que cuando hagan click en la aceptación  de la tarea les saldrá un formulario para elegir el nombre del equipo. En este caso el equipo será individual. Escriba su nombre y apellidos seguido de su ID de la ULL:

![]({{site.baseurl}}/assets/images/github-classroom-team-assignment-1.png)

{% include instrucciones-tareas-de-equipo.md %}

### Usa el Foro

Si te animas, ahora puedes ir al [foro de la organización y saludar](https://github.com/orgs/ULL-OCW-GITHUB-EDUCATION/discussions). Así practicas un poco mas de markdown. Pon en tu entrada del for un enlace a tu entrega.


## Referencias de consulta para empezar

Lee 

1. [Escrinir en GitHub](https://docs.github.com/es/get-started/writing-on-github)
1. El tutorial <a href="https://guides.github.com/features/mastering-markdown/" target="_blank">Mastering Markdown</a> para saber mas sobre esta forma de elaborar documentos
2. Para mas detalles consulta la guía de usuario
<a href="https://docs.github.com/en/free-pro-team@latest/github/writing-on-github/getting-started-with-writing-and-formatting-on-github" target="_blank">Getting started with writing and formatting on GitHub</a>

## Objetivos

Acepta la asignación de esta tarea y en el repositorio creado en GitHub edita el fichero `README.md` y rellenalo con un breve e informal CV.

* Incluye alguna imagen 
* Incluye algunos enlaces (por ejemplo un enlace a tu usuario en el campus virtual).
* Incluya alguna lista 
* Una cita favorita (blockquote)
* Un fragmento de código inline de un lenguaje de programación 
* Incluye un trozo de código que ocupe varias líneas como este y asegúrate de que aprece coloreado:

  ```javascript
  function fancyAlert(arg) {
    if(arg) {
      $.facebox({div:'#foo'})
    }
  }
  ```
* Incluye una tabla

  First Header | Second Header
  ------------ | -------------
  Content from cell 1 | Content from cell 2
  Content in the first column | Content in the second column

* Incluye un emoji. Por ejemplo: :+1:
* Añade un fichero `master.md`  (puedes crearlo usando el menu o bien visitando una ruta con la sintáxis `https://github.com/:owner:/:repo:/new/main`) en el que describas tu experiencia hasta ahora en este master y lo enlazas desde el fichero `README.md`.  
  * En el fichero 
`master.md` pon un enlace de vuelta al `README.md`

- Podemos hacer uso del editor que provee la interfaz web de GitHub.
- Pero hay editores alternativos mejores como [el editor web de GitHub  y GitPod]({{site.baseurl}}/pages/gitpod)
- Recuerda hacer "commits" para guardar los cambios.
- En la tarea entrega el enlace al repo con los contenidos de tu trabajo

* Añade una imagen-enlace. Se deberá ver la imagen pero esta será un enlace 
a otra página


## Edición en la Nube de Repositorios GitHub

Para manejar todo el proceso de edición pueden ayudarte estas notas:

* [Visual Studio Code in Browsers]({{site.baseurl}}/pages/gitpod)

## [Referencias](references)

* [Mastering (GitHub) Markdown](https://guides.github.com/features/mastering-markdown/#examples)
* [Documentación GitHub sobre la Interfaz Web]({{site.baseurl}}/pages/documentacion-github-interfaz-web)
* [Visual Studio Code in Browsers]({{site.baseurl}}/pages/gitpod)

* [GitHub Glossary](https://docs.github.com/en/free-pro-team@latest/github/getting-started-with-github/github-glossary)

<!--
* [A Simple Guide to GitHub for Non-Developers: How to Speak GitHub](https://unito.io/blog/guide-to-github-for-project-managers/#how-to-speak-github) contiene un glosario de términos
* [A guide to using GitHub for people who don't code and don't want to code.](https://github.com/tvanantwerp/github-for-non-programmers) tvanantwerp/github-for-non-programmers GitBook
-->

* [Apuntes del curso Elaboración de Material Docente con GitBook](https://casianorodriguezleon.gitbooks.io/elaboracion-de-material-docente-con-gitbook/content/)

