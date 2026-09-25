---
layout: default
title: Aprender Classroom 50 y Markdown
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

### Objetivo 1: Primeros Pasos con Classroom 50

Para crear el repositorio de trabajo deberás comenzar aceptando la tarea asociada a esta parte haciendo click en el correspondiente botón en el campus virtual de este curso. Para aprender a aceptar una tarea sigue los pasos en la sección 
[Accept an assignment](https://github.com/foundation50/classroom50/wiki/Web-Student-Guide#accept-an-assignment)
del capítulo de la wiki de Classroom 50 [Web Student Guide](https://github.com/foundation50/classroom50/wiki/Web-Student-Guide).

Un primer objetivo de esta lección/tarea es conseguir cierta familiaridad con los conceptos que conlleva Classroom 50: 
[asignación][assignment], 
[asignación individual](https://github.com/foundation50/classroom50/wiki/Glossary#individual-assignment), [asignación de grupo](https://github.com/foundation50/classroom50/wiki/Glossary#group-assignment), 
*[rosters][rosters]*, 
etc.

Como estudiante, tu entrega se realiza haciendo "[commit](https://github.com/git-guides/git-commit)" y "[push](https://github.com/git-guides/git-push)" al repositorio que obtienes cuando aceptas la asignación. Para más detalles lea la sección de la wiki de Classroom 50 [Submit your work](https://github.com/foundation50/classroom50/wiki/Web-Student-Guide#submit-your-work)

Este video en YouTube "[Classroom 50 Training Session](https://youtu.be/gpIz6XEVlEE?si=spbnHJnVeQZFglR3)"  contiene una introducción a Classroom 50.

{% include youtubePlayer.html id="gpIz6XEVlEE" %}

[rosters]: https://github.com/foundation50/classroom50/wiki/Glossary#roster
[assignment]: https://github.com/foundation50/classroom50/wiki/Glossary#assignmentget-started-with-github-classroom/glossary#assignment
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

Cuando termines esta tarea puedes ir al [foro de la organización y saludar]({{ site.organization.url }}/discussions). Así practicas un poco mas de markdown.

Publica tu entrada en la categoría **Cuéntanos lo que haces** (tienes un ejemplo de entrada en <https://github.com/orgs/ULL-OCW-GITHUB-EDUCATION/discussions/2>). 

Si quieres saber mas sobre como añadir un foro de debate a tus repos y como administrar los foros puedes consultar la documentación en [GitHub Discussions](https://docs.github.com/en/discussions)

## Introduccion al Lenguaje de Marcas MarkDown

Lee 

1. [Escribir en GitHub](https://docs.github.com/es/get-started/writing-on-github)
1. El tutorial <a href="https://guides.github.com/features/mastering-markdown/" target="_blank">Mastering Markdown</a> para saber mas sobre esta forma de elaborar documentos
2. Para mas detalles consulta la guía de usuario
<a href="https://docs.github.com/en/free-pro-team@latest/github/writing-on-github/getting-started-with-writing-and-formatting-on-github" target="_blank">Getting started with writing and formatting on GitHub</a>

## Edición en la Nube de Repositorios GitHub

* La sección de la documentación [Editar archivos](https://docs.github.com/es/repositories/working-with-files/managing-files/editing-files) sobre como editar archivosdirectamente en GitHub
* [GitHub Codespaces](https://docs.github.com/en/codespaces) en docs.github.com


## Rúbrica

{% include rubrica.md -%}



