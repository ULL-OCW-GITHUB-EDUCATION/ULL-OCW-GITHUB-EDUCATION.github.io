---
layout: default
title: gh-cli, gh-teacher y gh-student
permalink:  gh-cli-for-education
classroom: 
date: 0000/07/01
toc: true
---

# {{ page.title}}

## Objetivos

* Conocer e instalar [gh-cli](https://cli.github.com/)
* Instalar y aprender a usar las extensiones [gh-teacher](https://github.com/foundation50/classroom50/wiki/CLI-Teacher-Guide) y 
[gh-student](https://github.com/foundation50/classroom50/wiki/CLI-Student-Guide).
* Descargar las entregas de una [tarea de Classroom 50](https://github.com/foundation50/classroom50/wiki/CLI-Teacher-Guide#10-download-submissions) usando `gh teacher download -d <dir> <org> <classroom> <assignment>`

## Introducción a gh

Véase las notas en [GitHub Command Line Interface]({{ site.baseurl }}/pages/gh.html)

## Uso de Classroom 50 con GitHub CLI

Una vez instalada [GitHub CLI](https://github.com/cli/cli#installation) proceda a instalar las [extensiones de Classroom 50 para profesores y estudiantes](https://github.com/foundation50/classroom50/wiki/Installation).

Lea las secciones de la wiki de Classroom 50:

- [gh-teacher guide](https://github.com/foundation50/classroom50/wiki/CLI-Teacher-Guide) y 
- [gh-student guide](https://github.com/foundation50/classroom50/wiki/CLI-Student-Guide).

Consulte también los documentos de referencias correspondientes:

- [gh teacher reference](https://github.com/foundation50/classroom50/wiki/gh-teacher) y
- [gh student reference](https://github.com/foundation50/classroom50/wiki/gh-student)

## Descargando entregas de una tarea de Classroom 50

Para descargar las entregas de una tarea de Classroom 50, primero debe autenticarse con `gh auth login` y luego ejecutar el comando:

```
➜  UHU git:(main) ✗ gh teacher download UHU-FPDU-GDI-2026 uhu-fpdu-gdi registrarse-descuentos-aula
Your github.com login is missing scopes gh teacher needs (admin:org, read:org, repo, workflow); running `gh auth refresh` to add them (your existing token is kept, not replaced)...
? Authenticate Git with your GitHub credentials? Yes

! One-time code (1F89-8A56) copied to clipboard
Press Enter to open https://github.com/login/device in your browser...
```
Hacemos click en el enlace que nos lleva a la página de GitHub para introducir el código de un solo uso mostrado en la terminal para autorizar `gh`. El navegador solicita iniciar sesión en GitHub e introducir el código de un solo uso mostrado en la terminal para autorizar `gh`.

En el navegador, confirme con que cuenta quiere autorizar `gh`

![You are crguezl. Use a different account]({{site.baseurl}}/assets/images/download-submission/1.png)

Rellene el código de un solo uso 

![fill with the key]({{site.baseurl}}/assets/images/download-submission/2.png)

y autorice a `gh` a acceder a su cuenta de GitHub

![Authorize gh]({{site.baseurl}}/assets/images/download-submission/3.png)

```
✓ Authentication complete.
✓ Cloned uhu-fpdu-gdi-registrarse-descuentos-aula-casiano-rodriguez
✓ Cloned uhu-fpdu-gdi-registrarse-descuentos-aula-coro-alumni
Wrote uhu-fpdu-gdi-registrarse-descuentos-aula_submissions_2026_09_27_T_12_59_56/scores.csv
UHU-FPDU-GDI-2026: 2 cloned, 0 already on disk, 0 missing, 0 failed (of 2 team member(s))


A new release of teacher is available: 1.55.0 → 1.56.0
To upgrade, run: gh extension upgrade teacher
https://github.com/foundation50/gh-teacher
```
