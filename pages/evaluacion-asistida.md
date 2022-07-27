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

### `gh org-browse`: Comprobando la asistencia y participación de los alumnos via los commits

```
gh org-browse-repo -h             
Usage: gh org-browse-repo [options]

Open tabs in your browser for all the matching repos inside the org

Options:
  -V, --version             output the version number
  -C, --commit              open the commit activity pages
  -S, --search <query>      search <query> using GitHub Search API. A dot '.' refers to all the repos
  -d, --dryrun              shows the repos that will be open
  -P, --pause <number>      pause <number> of open tabs (default: 20)
  -r, --regexp <regexp>     filter <query> results using <regexp>
  -v, --dontmatch <regexp>  filter <query> results not matching <regexp>
  -o --org <org>            set default organization or user
  -h, --help                display help for command

  - You can set the default organization through the GITHUB_ORG environment variable
  - If the org is not specified and you issue the command inside a repo the org of that repo will be used 
  - Additional options will be passed to "gh browse":
      -b, --branch string            Select another branch by passing in the branch name
      -c, --commit                   Open the last commit
      -n, --no-browser               Print destination URL instead of opening the browser
      -p, --projects                 Open repository projects
      -s, --settings                 Open repository settings
      -w, --wiki                     Open repository wiki
```

Dada una organización por defecto:

```
 gh pwd
ULL-MFP-AET-2122
```

Para abrir pestañas de 25 en 25 en el navegador en las ventanas que nos informan de los commits de los alumnos para  la asignación de las tareas que llevan en su nombre la palabra `static`:
 
1. Abrimos  una nueva ventana en el navegador
2. `gh org-browse-repo -CS static -P 25`

![]({{ site.baseurl }}/assets/images/gh-org-browse-students-activity.png)

### `gh submodule-add`: Creando un super-repo con todos los repos de la práctica:
 

```
➜  practicas-alumnos gh submodule-add -h
Usage: gh submodule-add [options] [organization] -- [git submodule options]

Options:
  -V, --version                              output the version number
  -s, --search <query>                       search <query> using GitHub Search API
  -r, --regexp <regexp>                      filter <query> results using <regexp>
  -c, --csr <comma separated list of repos>  the list of repos is specified as a comma separated list
  -f, --file <file>                          file with the list of repos, one per line
  -n --dryrun                                just show what repos will be added as submodules
  -C --clone                                 clone only. Skip submodule adds and aborbgitdirs steps
  -o --org <org>                             organization or user
     --default                               Implies "-o <org>". Set "org" as default organization for future uses
  -D --depth <depth>                         Create a shallow clone with a history truncated to <depth> number of commits
  -d, --debug                                output extra debugging
  -p --parallel <int>                        number of concurrent  processes during the cloning stage (default: 2)
  -h, --help                                 display help for command

  - If the organization is not explicitly specified,
    the selection will be done interactively among the list of your organizations
  - You can set the default organization through the "--default" option for future uses of this program
  - If no repos are specified the selection of repos will be done interactively among the repos in the org
  - Option '-s' assumes all the repos belong to the same org
  - When called with option  '-s .', the dot '.' refers to all the repos.  fzf will be open to select the repos
  - The current folder must be the root of a git repo unless options '-n' or '-C' are used
  - When in fzf, use CTRL-A to select all, tab to select/deselect
  ```

```
✗ gh pwd
ULL-MFP-AET-2122
```

Si hacemos un dry-run con una búsqueda por repos cuyos nombres e casen con la palabra `markdown` 
simplemente nos muestra las urls de dichos repos:

```
➜  practicas-alumnos gh submodule-add -n -s markdown
ULL-MFP-AET-2122/latex-markdown-alejandro-gonzalez-sarasola
...
ULL-MFP-AET-2122/latex-markdown-chloe-boistel-perez-alu0100788020
```

Pero si omitimos la `-n` nos descargaremos los repos creando un repo cuyos submódulos son los repos de los alumnos para esa asignación. 

Primero creamos una carpeta e iniciamos el repo:

```
➜  practicas-alumnos mkdir markdown
➜  practicas-alumnos cd markdown
➜  markdown git init .
```

Vamos a crear un repo con submódulos 
los repos de la asignación `aprender-markdown` en cuyo nombre aparece la palabra `gonzalez`:

```
➜  markdown git:(master) gh submodule-add ULL-MFP-AET-2122 -s aprender-markdown -r gonzalez
cloning with 2 concurrent processes ...
...
➜  markdown git:(master) ✗ ls
aprender-markdown-adela-gonzalez-maury-alu0101116204        aprender-markdown-ivan-gonzalez-aguiar-alu0100551266
aprender-markdown-alejandro-gonzalez-gonzalez-alu0100879902 aprender-markdown-nestor-gonzalez-lopez-alu0100108859
aprender-markdown-alejandro-gonzalez-sarasola-alu0100260076
```

### Determinando que alumno tiene el informe con mayor número de líneas

Ahora podemos usar el comando `foreach` de `git submodule` usand `wc` (word count) 
para averiguar que alumno tiene  el fichero `README.md` mas grande:
```
➜  markdown git:(master) ✗ git submodule foreach 'wc README.md'

Entrando 'aprender-markdown-adela-gonzalez-maury-alu0101116204'
      57     130    1587 README.md
Entrando 'aprender-markdown-alejandro-gonzalez-gonzalez-alu0100879902'
      45     112    1157 README.md
Entrando 'aprender-markdown-alejandro-gonzalez-sarasola-alu0100260076'
      49     142    1323 README.md
Entrando 'aprender-markdown-ivan-gonzalez-aguiar-alu0100551266'
      27      82     918 README.md
Entrando 'aprender-markdown-nestor-gonzalez-lopez-alu0100108859'
      61     142    1419 README.md
```

Vemos que la salida tiene 6 campos separados por blancos. El tercero de los cuales es el número de líneas en el fichero. 

La utilidad [xargs](https://man7.org/linux/man-pages/man1/xargs.1.html) lee cadenas delimitadas por espacio, tabulación, nueva línea y final de archivo de la entrada estándar. 

Cuando es usada con la opción `-n número` se establece el número máximo de argumentos tomados de la entrada estándar y llama a `echo` con ese `número` de argumentos. Por ejemplo:

```
✗ git submodule foreach 'wc README.md ' | xargs -n 6
```
produce líneas cada una conteniendo 6 campos:
```
Entrando aprender-markdown-adela-gonzalez-maury-alu0101116204 57 130 1587 README.md
Entrando aprender-markdown-alejandro-gonzalez-gonzalez-alu0100879902 45 112 1157 README.md
Entrando aprender-markdown-alejandro-gonzalez-sarasola-alu0100260076 49 142 1323 README.md
Entrando aprender-markdown-ivan-gonzalez-aguiar-alu0100551266 27 82 918 README.md
Entrando aprender-markdown-nestor-gonzalez-lopez-alu0100108859 61 142 1419 README.md
```

Que si lo alimentamos a un pipe/canal  con [sort](https://man7.org/linux/man-pages/man1/sort.1.html) ordenando por el tercer campo `-k 3`,
nos produce una lista ordenada por líneas:

```
➜  markdown git:(master) ✗ git submodule foreach 'wc README.md ' | xargs -n 6 | sort -gk 3

Entrando aprender-markdown-ivan-gonzalez-aguiar-alu0100551266 27 82 918 README.md
Entrando aprender-markdown-alejandro-gonzalez-gonzalez-alu0100879902 45 112 1157 README.md
Entrando aprender-markdown-alejandro-gonzalez-sarasola-alu0100260076 49 142 1323 README.md
Entrando aprender-markdown-adela-gonzalez-maury-alu0101116204 57 130 1587 README.md
Entrando aprender-markdown-nestor-gonzalez-lopez-alu0100108859 61 142 1419 README.md
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

