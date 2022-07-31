---
title: Usando Contenedores Remotos desde VSCode
---

# {{ page.title }}

En VSCode es posible clonar un contenedor remoto y empezar a trabajar en el mismo.

En este ejemplo usaremos el contenedor para $$\LaTeX$$ descrito en:

* [hegerdes/VSCode-LaTeX-Container](https://github.com/hegerdes/VSCode-LaTeX-Container)
  * Lee el post asociado [Getting started with LaTex as a Dev](https://henrikgerdes.me/articles/2022-01-vscode-latex)

Primero instalamos las extensiones Docker y Remote Containers. Después pulsamos F1 y escribimos `Remote-containers`eligiendo la opción `Clone repository in Container Volume`:

![]({{ site.baseurl}}/assets/images/remote-containers/remote-containers-vscode-package.png)

le indicamos la url del repositorio que aloja el contenedor, que en este ejemplo es <https://github.com/hegerdes/VSCode-LaTeX-Container>:

![]({{ site.baseurl}}/assets/images/remote-containers/clone-repository-from-github-in-a-container-volume.png)

VSCode nos advierte que instalar y ejecutar código externo es una operación peligrosa:

![]({{ site.baseurl}}/assets/images/remote-containers/cloning-from-a-dev-container-may-be-dangerous.png)

Si todo va bien, después de un ratito tendremos el contenedor montado y estaremos editándo la jerarquía de ficheros:

![]({{ site.baseurl}}/assets/images/remote-containers/container-is-open.png)

Cuando abres una terminal observarás que este contenedor tiene una errata, pero que se arregla arrancando una bash.

Una vez arrancada, podemos compilar con `pdflatex`:

![]({{ site.baseurl}}/assets/images/remote-containers/pdflatex-compiling.png)

Para trabajar con $$\LaTeX$$ es conveniente tener instaladas las extensiones [LateX WorkShop]() y [LaTeX Utilities]()

![]({{ site.baseurl}}/assets/images/remote-containers/latex-extensions-installed.png)

Haciendo click sobre el pdf generado podemos visualizarlo:

![]({{ site.baseurl}}/assets/images/remote-containers/pdf-view.png)