---
toc: true
---

### Alias `cd`

```
➜  ocw git:(main) ✗ gh alias list | grep cd
cd:	!gh config set current-org "$1" 2>/dev/null
```

### Alias `pwd` 

```
➜  ocw git:(main) ✗ gh alias list | grep pwd
pwd:	!gh config get current-org
```

Ejemplo:

```
➜  ocw git:(main) ✗ gh pwd
ULL-MFP-AET-2122
```

### Comprobando la asistencia y participación de los alumnos via los commits

1. Abrimos  una nueva ventana en el navegador
2. `gh org-browse-repo -CS static -P 25`


### Creando un super-repo con todos los repos de la práctica:
 
```
gh submodule-add -n -s markdown ULL-MFP-AET-2122
gh submodule-add ULL-MFP-AET-2122 -s markdown
```

### Determinando quien va mas avanzado en la tarea

```
git submodule foreach 'wc README.md'
```

or, if you are a really nerd hacker:

```
git submodule foreach 'wc README.md ' | xargs -n 6 | sort -gk 3
```

### Abriendo pestañas en cada uno de los proyectos de los alumnos.

Abrimos primero una nueva ventana en el navegador por defecto y ...

```
git submodule foreach 'gh browse'
```

### Generando incidencias con los fallos la práctica 

Usamos un programa que haga un diagnóstico de la calidad del trabajo:

Instalamos una herramienta adecuada:

```
npm install -g markdownlint-cli
```

Generamos los informes:

```
$ git submodule foreach 'markdownlint README.md -o issues.txt || :'
```

y creamos las incidencias:

```
$ git submodule foreach 'gh issue create -F issues.txt'
```

### Visitando todas las páginas de profile de los alumnos en 10 minutos

```
➜  github-profile-readme gh org-members ULL-MFP-AET-2122
AdelaGM
Alex100260076
alu0100108859
... etc.
NoeliaRguezHdez
Ramallin
```

```
➜  github-profile-readme gh org-members ULL-MFP-AET-2122 | sed -ne 's#^#https://github.com/#p'
https://github.com/AdelaGM
https://github.com/Alex100260076
... etc.
https://github.com/magodelnorte
https://github.com/ManCurTru
https://github.com/NoeliaRguezHdez
https://github.com/Ramallin
```

```
➜  github-profile-readme gh org-members ULL-MFP-AET-2122 --jq '.[].login' | sed -ne 's#^#https://github.com/#p' > profiles-urls
```

```
➜  github-profile-readme # abro nueva ventana en el navegador ...
➜  github-profile-readme xargs open < profiles-urls
```

## gh-activity Nº de commits etc.

Véase  [gh-cli-for-education/git-developer-contribution-analysis](https://github.com/gh-cli-for-education/git-developer-contribution-analysis) que es un fork del repo de @bloombar @jayamundra. 

First, let us get the urls of the repos of one assignment using `gh submodule -n`:

```
➜  gh-activity git:(master) gh pwd
ULL-MFP-AET-2122
➜  gh-activity git:(master) gh submodule-add -n -s aprender-markdown > REPOFILE 
```

that leaves `REPOFILE` having these contents:

``` 
https://github.com/ULL-MFP-AET-2122/aprender-markdown-adela-gonzalez-maury-alu0101116204.git
... etc.
https://github.com/ULL-MFP-AET-2122/aprender-markdown-yeray_exposito_garcia_alu0100951844.git
```

When using the command:

```
✗ gh activity -rf REPOFILE2 -f json -c >  markdown-aet.json
```

it produces the following output. Commas are missed among repos reports:

```json
[
  {
    "username": "AdelaGM",
    "repository": "aprender-markdown-adela-gonzalez-maury-alu0101116204",
    "start_date": "07/27/2021",
    "end_date": "07/27/2022",
    "merges": 0,
    "commits": 15,
    "insertions": 80,
    "deletions": 29,
    "files": 12
  }
]
... etc.
```

