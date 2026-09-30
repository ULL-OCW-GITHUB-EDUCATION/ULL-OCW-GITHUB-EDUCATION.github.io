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

### Objetivo 1: Classroom 50

Como en la tarea anterior, para crear el repositorio de trabajo deberás comenzar aceptando la tarea asociada a esta parte haciendo click en el correspondiente botón en el campus virtual de este curso. Para repasar el proceso de aceptar una tarea vuelve a estudiar las secciones:

- [Accept an assignment](https://github.com/foundation50/classroom50/wiki/Web-Student-Guide#accept-an-assignment)
del capítulo de la wiki de Classroom 50 [Web Student Guide](https://github.com/foundation50/classroom50/wiki/Web-Student-Guide).
- Repasa el vídeo en la sección [Classroom 50 Training Session]({{ site.baseurl }}/pages/classroom50-training-session).

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

### Objetivo 3: Aprender a Usar Codespaces

Hay múltiples formas de editar en la nube un repositorio GitHub:

#### Objetivo 3.1. Editar directamente usando el [editor on-line de GitHub](https://docs.github.com/es/repositories/working-with-files/managing-files/editing-files)

#### Objetivo 3.2. Usar [GitHub Codespaces](https://docs.github.com/en/codespaces)

#### Objetivo 3.3: GitHub Copilot en Codespaces

Utiliza el chat  con la IA (lado derecho de la pantalla) para consultar tus dudas y para que te ayude a escribir código. 

![assets/images/codespace-copilot.png]({{ site.baseurl }}/assets/images/codespace-copilot.png)


### Objetivo 4: Aprender a Usar GitHub Discussions

Cuando termines esta tarea puedes ir al [foro de la organización y saludar]({{ site.organization.url }}/discussions). Así practicas un poco mas de markdown.

Publica tu entrada en la categoría **Cuéntanos lo que haces** (tienes un ejemplo de entrada en <https://github.com/orgs/ULL-OCW-GITHUB-EDUCATION/discussions/2>). 

Si quieres saber mas sobre como añadir un foro de debate a tus repos y como administrar los foros puedes consultar la documentación en [GitHub Discussions](https://docs.github.com/en/discussions)

## Referencias 

1. <a href="https://guides.github.com/features/mastering-markdown/" target="_blank">Mastering Markdown</a> 
2. [Writing on GitHub](https://docs.github.com/es/get-started/writing-on-github)
3. <a href="https://docs.github.com/en/free-pro-team@latest/github/writing-on-github/getting-started-with-writing-and-formatting-on-github" target="_blank">Getting started with writing and formatting on GitHub</a>
4. [Editing Files](https://docs.github.com/es/repositories/working-with-files/managing-files/editing-files) 
5. [GitHub Codespaces](https://docs.github.com/en/codespaces)


## Rúbrica

{% include rubrica.md -%}



