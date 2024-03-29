---
layout: default
title: Aprender GitHub Classroom y Markdown
permalink: aprender-markdown
classroom: https://classroom.github.com/a/PlGuI8vJ
name: aprender-markdown
date: 0000/02/01
toc: true
rubrica:
  - "Se incluyen todos los aspectos solicitados en el markdown y se visualizan correctamente"
  - "Informe elaborado correcto"
  - "Ha entregado el enlace en el campus con el repo"
---

# {{ page.title }}

La siguiente sección establece los objetivos y competencias que debes lograr.
Las subsiguientes secciones presentan los recursos para lograr estos objetivos.

## Objetivos

### Objetivo 1: Primeros Pasos con GitHub Classroom

Deberás comenzar aceptando la tarea asociada a esta parte haciendo click en el botón con el texto *"acepta la asignación de la tarea"* en la cabecera. En cada una de los temas que requieren de la creación de un repositorio de trabajo para la realización de las tareas asociadas al tema encontrarás un botón con el texto
<a href="{{ page.classroom }}" target="_blank"><button class="assign">acepta la asignación de la tarea</button></a>
en la cabecera de la página. Para aprender a aceptar una tarea sigue los pasos en [Como aceptar una tarea de grupo]({{ site.baseurl}}/pages/aceptar-tarea.html)

Un primer objetivo de esta lección/tarea es conseguir cierta familiaridad con los conceptos que conlleva Github Classroom: [asignación][assignment], asignación individual, asignación de grupo, [identificación del alumnado][identificacion], *[rosters][rosters]*, etc.

Este video en YouTube "[How to use VS Code to submit an assignment to Github Classroom (initially empty repository)](https://youtu.be/iqW_yzZkU_8)" 

{% include youtubePlayer.html id="iqW_yzZkU_8" %}

muestra como deben hacer los estudiantes para aceptar, trabajar y entregar una tarea asignada con GHC usando el editor VS Code

[rosters]: https://docs.github.com/en/education/manage-coursework-with-github-classroom/get-started-with-github-classroom/glossary#roster
[assignment]: https://docs.github.com/en/education/manage-coursework-with-github-classroom/get-started-with-github-classroom/glossary#assignment
[identificacion]: {{ site.baseurl }}/pages/github-classroom.html#el-problema-de-enlazar-las-cuentas-gh-con-las-cuentas-del-lms

### Objetivo 2: Aprender Markdown

Otro objetivo de esta tarea es aprender Markdown. Para ello, en el repositorio que se crea cuando aceptas la asignación  deberás rellenar los contenidos del fichero `README.md` con un pequeño curriculum vitae/carta de presentación usando markdown. 

* Incluye alguna imagen 
* Incluye algunos enlaces (por ejemplo un enlace a tu usuario en el campus virtual o el LMS de tu institución educativa).
* Incluya al menos una lista enumerada y una lista no ordenada (*bullets*)
* Una cita favorita (blockquote)
* Un fragmento de código inline de un lenguaje de programación 
* Incluye un trozo de código que ocupe varias líneas como este y asegúrate de que aparece coloreado:

  ```javascript
  function fancyAlert(arg) {
    if(arg) {
      $.facebox({div:'#foo'})
    }
  }
  ```
* Incluye una tabla. Puede hacerse así:

  ```md
    First Header | Second Header
    ------------ | -------------
    Content from cell 1 | Content from cell 2
    Content in the first column | Content in the second column
  ```
  y se verá así:

  First Header | Second Header
  ------------ | -------------
  Content from cell 1 | Content from cell 2
  Content in the first column | Content in the second column
* Incluye un emoji. Por ejemplo  `:+1:` se ve: :+1:
* Añade un fichero `master.md`  (puedes crearlo usando el menu o bien visitando una ruta con la sintáxis `https://github.com/:owner:/:repo:/new/main`) en el que describas tu experiencia hasta ahora en este master y lo enlazas desde el fichero `README.md`.  
1. Incluyas alguna imagen en el repo en una carpeta `img` y la muestres desde el texto
2. Añadas un segundo fichero en el repo con nombre  `objetivos.md`  contando cuáles son tus objetivos con respecto a este curso y lo referencies desde el fichero `README.md`. Añade una referencia/enlace  de vuelta en `objetivos.md` a  tu `README.md`

  * En el fichero 
`master.md` pon un enlace de vuelta al `README.md`

- Podemos hacer uso del editor que provee la interfaz web de GitHub.
- Pero hay editores alternativos mejores como [el editor web de GitHub  y GitPod]({{site.baseurl}}/pages/gitpod)
- Recuerda hacer "commits" para guardar los cambios.
- En la tarea entrega el enlace al repo con los contenidos de tu trabajo

* Añade una imagen-enlace. Se deberá ver la imagen pero esta será un enlace 
a otra página

En este [enlace puedes visitar ejemplos de lo que han hecho algunos alumnos de la asignatura *Aprendizaje y Enseñanza de la Tecnología* del master de Formación de Profesorado en el curso 21/22](https://github.com/orgs/ULL-MFP-AET-2122/repositories?q=aprender-markdown&type=all&language=&sort=)

### Objetivo 3: Aprender a Usar un Editor en la Nube

Hay múltiples formas de editar en la nube un repositorio GitHub.
en estas [notas]({{site.baseurl}}/pages/gitpod) recogemos estas alternativas:

1. Editar directamente usando el [editor on-line de GitHub](https://docs.github.com/es/repositories/working-with-files/managing-files/editing-files)
2. [Usar el editor GitHub.dev][githubdev]. Véase también las [notas en estos apuntes sobre GitHub.dev][githubdev]. Véase también las [notas en estos apuntes sobre GitHub.dev]({{site.baseurl}}/pages/gitpod#editing-with-githubdev-editor): se activa simplemente  tecleando el punto cuando se está visitando el repo
4. Usar [Codespaces][codespaces] (Probablemente la opción mas recomendable si dispones de este servicio)
3. Usar [GitPod]({{ site.baseurl }}/pages/gitpod#gitpod), una alternativa a [Codespaces][codespaces]

[githubdev]: https://docs.github.com/en/codespaces/the-githubdev-web-based-editor
[codespaces]: /pages/gitpod#codespaces

### Objetivo 4: Aprender a Usar GitHub Discussions

Cuando termines esta tarea puedes ir al [foro de la organización y saludar](https://github.com/orgs/ULL-OCW-GITHUB-EDUCATION/discussions). Así practicas un poco mas de markdown.

Publica tu entrada en la categoría **Cuéntanos lo que haces** (tienes un ejemplo de entrada en <https://github.com/orgs/ULL-OCW-GITHUB-EDUCATION/discussions/2>). 

Si quieres saber mas sobre como añadir un foro de debate a tus repos y como administrar los foros puedes consultar la documentación en [GitHub Discussions](https://docs.github.com/en/discussions)


## Introducción a GitHub Classroom (como estudiante)

Los profesores de este curso han configurado la tarea asociada usando [GitHub Classroom  (que abreviaremos a veces como GHC)](https://docs.github.com/es/education/manage-coursework-with-github-classroom/teach-with-github-classroom). GitHub Classroom es una aplicación web para los docentes que proporciona herramientas para la administración de cursos integradas con GitHub. 

En este capítulo tu contacto con GHC es como alumno.
Para aprender a usar esta herramienta como profesor es conveniente que 

1. Hagas posteriormente la tarea [GHC para Profesores]({{ site.baseurl}}/ghc.html)
2. Sigas el curso [Teach with GitHub Classroom](https://docs.github.com/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom). 
3. Puedes encontrar un buen número de vídeos que complementan el curso en la sección [Videos about GitHub Classroom](https://docs.github.com/en/education/manage-coursework-with-github-classroom/get-started-with-github-classroom/basics-of-setting-up-github-classroom#videos-about-github-classroom)

Verás que con GHC permite crear [asignaciones individuales](https://docs.github.com/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom/create-an-individual-assignment) y de grupo. 


## Introduccion al Lenguaje de Marcas MarkDown

Lee 

1. [Escribir en GitHub](https://docs.github.com/es/get-started/writing-on-github)
1. El tutorial <a href="https://guides.github.com/features/mastering-markdown/" target="_blank">Mastering Markdown</a> para saber mas sobre esta forma de elaborar documentos
2. Para mas detalles consulta la guía de usuario
<a href="https://docs.github.com/en/free-pro-team@latest/github/writing-on-github/getting-started-with-writing-and-formatting-on-github" target="_blank">Getting started with writing and formatting on GitHub</a>

## Introducción a la Edición en la Nube de Repositorios GitHub

Para manejar todo el proceso de edición pueden ayudarte estas [notas sobre Edición en la Nube]({{site.baseurl}}/pages/gitpod).

**Si no tienes mucha experiencia y no estás familiarizado con VSCode lo mas sencillo es 
que en esta tarea uses el [editor on-line de GitHub]({{ site.baseurl }}/pages/gitpod#editor-on-line-de-github)**.

Si estás familiarizado con VSCode, basta con pulsar un punto en tu navegador cuando estás visitando tu repo de trabajo para que se active una version reducida de VSCode que es conocida como [GitHub.dev Editor]({{ site.baseurl }}/pages/gitpod#editing-with-githubdev-editor). Aún mejor, usa [GitPod]({{ site.baseurl }}/pages/gitpod#gitpod) o [CodeSpaces]({{ site.baseurl }}/pages/gitpod#codespaces)

## Rúbrica

{% include rubrica.md -%}


## [Referencias](references)

* [Mastering (GitHub) Markdown](https://guides.github.com/features/mastering-markdown/#examples)
* [Documentación GitHub sobre la Interfaz Web]({{site.baseurl}}/pages/documentacion-github-interfaz-web)
* [Visual Studio Code in Browsers]({{site.baseurl}}/pages/gitpod)
* [How to use VS Code to submit an assignment to Github Classroom (initially empty repository)](https://youtu.be/iqW_yzZkU_8) Vídeo que muestra como deben hacer los estudiantes para aceptar, trabajar y entregar una tarea asignada con GHC usando el editor VS Code
* [GitHub Glossary](https://docs.github.com/en/free-pro-team@latest/github/getting-started-with-github/github-glossary)

<!--
* [A Simple Guide to GitHub for Non-Developers: How to Speak GitHub](https://unito.io/blog/guide-to-github-for-project-managers/#how-to-speak-github) contiene un glosario de términos
* [A guide to using GitHub for people who don't code and don't want to code.](https://github.com/tvanantwerp/github-for-non-programmers) tvanantwerp/github-for-non-programmers GitBook
-->

* [Apuntes del curso Elaboración de Material Docente con GitBook](https://casianorodriguezleon.gitbooks.io/elaboracion-de-material-docente-con-gitbook/content/)

