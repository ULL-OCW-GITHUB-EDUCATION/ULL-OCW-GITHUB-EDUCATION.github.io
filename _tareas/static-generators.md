---
layout: default
title: Construyendo Web Sites con un Generador estático
permalink: generador-estatico
classroom: https://classroom.github.com/a/IOBTV2l4
date: 0000/05/01
video: "8KwoKgYz85k"
toc: true
---

# {{ page.title}}

## Objetivos

En esta tarea vamos a aprender a construir dos web sites usando un [generador estático de contenidos]({{ site.baseurl }}/glossary.html#static-site-generators). 

Para ello usaremos 

1. los servicios de alojamiento de websites que provee GitHub mediante [GitHub Pages](https://pages.github.com/)
2. el generador de web sites estáticos Jekyll.
3. La plantilla [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/) para Jekyll

Al aceptar esta asignación se creará un repo con los archivos y carpetas necesarios para la generación de un web site usando Jekyll. 

1. En este primer web site deberás construir tu página personal en GitHub y la publicarás en un repo con nombre `<usuario>/<usuario>.github.io`.
2. Deberás también crear un segundo web site en un repo con nombre `<organization>/<organization>.github.io` para la organización que creaste en la tarea [Registrarse en GitHub]({{ site.baseurl }}/registrarse-en-github)  con una estructura similar al  web site de este curso conteniendo temas, tareas, comentarios, enlaces, etc. 
3. Deberás alojar todo el HTML generado en el paso anterior en el Moodle de tu asignatura siguiendo las instrucciones en la sección [Desplegando el Web Site de la Asignatura en Moodle]()

## Puesta a punto en CodeSpaces

En el repo de la asignación , procedemos a abrir CodeSpaces. Para ello, en el repo, 
nos vamos a la etiqueta "Code" y elegimos la pestaña "CodeSpaces":

![]({{ site.baseurl }}/assets/images/codespaces.png)

Elegimos la opción `Create codespace on master` y hacemos click

![]({{ site.baseurl }}/assets/images/codespaces-create-on-master.png)

La consecuencia es que se nos abre una página con el editor CodeSpaces. 
En la ventana de la terminal escribimos el comando para instalar las dependencias: 

```
bundle install
```

este comando hace que se instalen las librerías necesarias para que el generador estático de contenidos Jekyll pueda funcionar:

![]({{ site.baseurl }}/assets/images/codespaces-bundle-install.png)

A continuación ponemos a correr el servidor `jekyll` en el contenedor creado. Para ello escribimos en la terminal:

```
bundle exec jekyll build
```

o bien aprovechar que dicho comando a sido como abreviado como tarea en el fichero `Rakefile`:

```
rake serve
```

Se nos abre una ventana emergente `Open in Browser`:

![]({{ site.baseurl }}/assets/images/codespaces-rake-serve.png)

El servidor web ha arrancado y esta a la escucha de las peticiones.

Hacemos click en `Open in Browser` y abrimos una nueva pestaña en la que visitamos la página web servida. 
Veremos algo similar a esto:

![]({{ site.baseurl }}/assets/images/codespaces-deployed.png)

¡Nuestra página web esta funcionando!

Si no hubieramos tenido ya instalado `bundler` podríamos haber hecho:

```
gem install bundler jekyll
bundle update
bundle exec jekyll serve
```

### Como Configurar un Repo para usar Jekyll en CodeSpaces

Ver el vídeo [GitHub Codespaces with GitHub Pages](https://youtu.be/8KwoKgYz85k) por 
Jon Gallant

{% include video-youtube.html %}


### Puesta a punto con GitPod 

Para el desarrollo usaremos [GitPod](https://www.gitpod.io/docs/getting-started).

Despliegue el repo en GitPod usando el botón GitPod. 
El contenedor/Docker/Máquina Virtual creado instalará Jekyll (lleva su tiempo, tenga paciencia) y arrancará Jekyll en modo servidor.

![]({{site.baseurl}}/assets/images/jekyll-serve.png)

Haga click en *http://127.0.0.1:4000 Follow link using forwarded port*

![]({{site.baseurl}}/assets/images/minimal-mistakes.png)

## Modificando el Web Site

A continuación lea los tutorials de [Jekyll](https://jekyllrb.com/docs/) y [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)

## Desplegando nuestro Web Site como nuestra página Web personal en GitHub


```
@casiano ➜ /workspaces/construyendo-un-website-casiano-rodriguez-leon-alumnoudv4 (master) $ git remote -v
origin  https://github.com/ULL-OCW-GITHUB-EDUCATION/construyendo-un-website-casiano-rodriguez-leon-alumnoudv4 (fetch)
origin  https://github.com/ULL-OCW-GITHUB-EDUCATION/construyendo-un-website-casiano-rodriguez-leon-alumnoudv4 (push)
```

```
@casiano ➜ /workspaces/construyendo-un-website-casiano-rodriguez-leon-alumnoudv4 (master) $ gh --version
gh version 2.13.0 (2022-06-22)
```

## Web Site de tu Asignatura

Crea un segundo web site dentro de la organización de la asignatura y despliégalo en GitHub.

## Desplegando el Web Site de la Asignatura en Moodle

Siga las instrucciones en el artículo [Importing a Website into Moodle]({{site.baseurl}}/pages/moodle.html)


## Entrega

Deja en el fichero `README.md` de este repositorio los enlaces a tu página web en GitHub y a la web de tu asignatura. Si tienes acceso a un curso Moodle despliega tu web site de la asignatura en el curso Moodle.

Publica en el foro los enlaces.

## References

### GitHub Pages

* [GitHub Pages](https://pages.github.com/)
{% include jekyll-references.md %}

### GitPod

{% include gitpod-references.md %}

