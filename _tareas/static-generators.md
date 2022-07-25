---
layout: default
title: Construyendo un Web Site con un Generador estático
permalink: generador-estatico
classroom: https://classroom.github.com/a/IOBTV2l4
date: 0000/05/01
---

# {{ page.title}}

## Objetivos

En esta tarea vamos a aprender a construir un web site usando un [generador estático de contenidos]({{ site.baseurl }}/glossary.html#static-site-generators). 

Para ello usaremos 

1. los servicios de alojamiento de websites que provee GitHub mediante [GitHub Pages](https://pages.github.com/)
2. el generador de web sites estáticos Jekyll.
3. La plantilla [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/) para Jekyll

Al aceptar se le creará un repo con los archivos y carpetas necesarios para la generación de un web site usando Jekyll. 


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

### Puesta a punto con GitPod 

Para el desarrollo usaremos [GitPod](https://www.gitpod.io/docs/getting-started).

Despliegue el repo en GitPod usando el botón GitPod. 
El contenedor/Docker/Máquina Virtual creado instalará Jekyll (lleva su tiempo, tenga paciencia) y arrancará Jekyll en modo servidor.

![]({{site.baseurl}}/assets/images/jekyll-serve.png)

Haga click en *http://127.0.0.1:4000 Follow link using forwarded port*

![]({{site.baseurl}}/assets/images/minimal-mistakes.png)

## Modificando el Web Site

A continuación lea los tutorials de [Jekyll](https://jekyllrb.com/docs/) y [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)


## References

### GitHub Pages

* [GitHub Pages](https://pages.github.com/)
{% include jekyll-references.md %}

### GitPod

{% include gitpod-references.md %}

