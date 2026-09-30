---
layout: default
title: Generación de pdfs a partir de Github Markdown
permalink: latex-markdown
classroom: 
date: 0000/03/01
---

# {{ page.title }}

La mejor herramienta para producir un pdf desde un fichero GH markdown  depende de tu flujo de trabajo habitual (editor visual, línea de comandos o automatización). Las siguientes son opciones para convertir **GitHub Flavored Markdown (GFM)** —con soporte para tablas, listas de tareas, bloques de código estilizados y diagramas— a PDF:

### 1. Extensión de VS Code

Si ya escribes Markdown en Visual Studio Code, la forma más sencilla es usar una extensión:

* **Markdown PDF** (`yzane.markdown-pdf`)
* **Ventajas:** Convierte directamente con un clic o desde la paleta de comandos (`Ctrl+Shift+P` / `Cmd+Shift+P` $\rightarrow$ *Markdown PDF: Export (pdf)*). 


* **Markdown Preview Enhanced** (`shd101yyy.markdown-preview-enhanced`)
* **Ventajas:** Soporta sintaxis de GFM completa, gráficos con Mermaid.js y MathJax para fórmulas.



---

### 2. Grip + Chrome (Fidelidad 100% estilo GitHub)

**Grip** (GitHub Readme Instant Preview) utiliza la propia API pública de GitHub para renderizar el documento. Es una opción ideal si necesitas que el PDF se vea exactamente igual a un `README.md` en GitHub.

```bash
# 1. Instalar Grip
pip install grip

# 2. Iniciar el servidor local
grip tu_archivo.md

```

> **Paso final:** Abre la URL que genera en el navegador (`http://localhost:6419`), presiona `Ctrl+P` / `Cmd+P` y selecciona **Guardar como PDF**.

```
➜  gh-cli-template git:(main) grip README.md
 * Serving Flask app 'grip.app'
 * Debug mode: off
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on http://localhost:6419
Press CTRL+C to quit
```
---


## Objetivos

Genera un pdf a partir del fichero `test.md` que forma parte del template.  

## Entrega

Añade el pdf generado `test.pdf`al control de versiones y enlázalo en este documento.


