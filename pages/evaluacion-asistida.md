---
toc: true
title: Automatizando las labores de Evaluación con **gh**
---

# {{ page.title }}

Las siguientes secciones muestran *scripts* que facilitan las labores de retroalimentación y
evaluación  usando `gh`. Se asume un lector familiarizado con el uso de la terminal.


## Alias cd

The `gh` environment variable `GH_REPO` specifies the GitHub repository in the `[HOST/]OWNER/REPO` format for commands that otherwise operate on a local repository. It can be used also to get the default `OWNER`and consequently the default organization. However this solution is not persistent enough for the daily work of a github education teacher and it is better to have it stored permanently. 

Currently I use this alias to save the default organization:

```
➜  ocw git:(main) ✗ gh alias list | grep cd
cd:	!gh config set current-org "$1" 2>/dev/null
```

## Alias pwd 

Currently I use this alias to recover the default organization:

```
➜  ocw git:(main) ✗ gh alias list | grep pwd
pwd:	!gh config get current-org
```

Ejemplo:

```
➜  ocw git:(main) ✗ gh pwd
ULL-MFP-AET-2122
```

all the gh extensions I have wrote are consistent with these alias. 

## `gh org-browse`: Comprobando la asistencia y participación de los alumnos via los commits

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

La siguiente imagen muestra una ventana con tantas pestañas como prácticas entregadas. Cada pestaña está  abierta en el diagrama de actividad del alumno:

![]({{ site.baseurl }}/assets/images/gh-org-browse-students-activity.png)

## `gh submodule-add`: Creando un super-repo con todos los repos de la práctica:
 

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

Si hacemos un dry-run con `-n` con una búsqueda por repos (`-s`) cuyos nombres casen con la palabra `markdown` 
simplemente nos muestra las urls de dichos repos:

```
➜  practicas-alumnos gh submodule-add -n -s markdown
ULL-MFP-AET-2122/latex-markdown-alejandro-gonzalez-sarasola
...
ULL-MFP-AET-2122/latex-markdown-chloe-boistel-perez-alu0100788020
```

Pero si omitimos la `-n` nos descargaremos los repos creando un repo cuyos submódulos son los repos de los alumnos para esa asignación. 

La extensión `gh submodule-add` requiere que cuando se ejecute se esté en la raíz de un repositorio. Por ello, primero creamos una carpeta e iniciamos un repo:

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

## Determinando que alumno tiene el informe con mayor número de líneas

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

```sh
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

```sh
✗ git submodule foreach 'wc README.md ' | xargs -n 6 | sort -gk 3

Entrando aprender-markdown-ivan-gonzalez-aguiar-alu0100551266 27 82 918 README.md
Entrando aprender-markdown-alejandro-gonzalez-gonzalez-alu0100879902 45 112 1157 README.md
Entrando aprender-markdown-alejandro-gonzalez-sarasola-alu0100260076 49 142 1323 README.md
Entrando aprender-markdown-adela-gonzalez-maury-alu0101116204 57 130 1587 README.md
Entrando aprender-markdown-nestor-gonzalez-lopez-alu0100108859 61 142 1419 README.md
```

## Abriendo pestañas en cada uno de los proyectos de los alumnos.

Estando en el super-repo, abrimos primero una nueva ventana en el navegador por defecto y ...

```
git submodule foreach 'gh browse'
```

esto nos abrirá tantas pestañas como repos de alumnos haya en el super-repo. 
¡Tenga cuidado si tiene 200 alumnos!

## Generando retroalimentación

Usamos un programa que haga un diagnóstico de la calidad del trabajo. 
En este  ejemplo se trata de mirar la calidad del markdown que ha escrito el alumno.

Instalamos una herramienta adecuada:

```
npm install -g markdownlint-cli
```

Generamos los informes:

```
$ git submodule foreach 'markdownlint README.md -o issues.txt || :'
```

y creamos  incidencias para cada uno de los alumnos enviando el informe generado:

```
$ git submodule foreach 'gh issue create -F issues.txt'
```

## gh org-members

```
➜  markdown git:(master) ✗ gh org-members -h
Usage: gh org-members [options] [organization]

Options:
  -V, --version             output the version number
  -f, --fullname            show name of the user (if available)
  -j, --json                returns the full json object
  -r, --regexp <regexp>     filter <query> results using <regexp>
  -u, --url                 show github user url
  -l, --login               show github user login
  -w, --orgurl              show github user url as a member of the org
  -s, --site                show url of the members github pages web sites
  -c, --csv [field...]      shows the values of the fields of the organization csv
  -p, --pathcsv <csv file>  path to the csv file
  -o --org <org>            default organization
     --default              Set selected "org" as default organization for future uses
  -h, --help                display help for command

  - If the organization is not explicitly specified or there is a default org,
    the selection will be done interactively among the list of your organizations using 'fzf'
  - You can set the default organization through the "--default" option for future uses of this program
  - When in 'fzf', use CTRL-A to select all, tab to select/deselect
  - You can merge the results of the GitHub API info with info from info in a '.csv' file using the "-c" and "-p" options. For instance: "gh org-members -jr sara -c -p ./ULL-MFP-AET-2122.csv"
  - If the option '-c' is used but the '.csv' file is not specified via the '-p' option, it will use the most recent '*.csv' file in your 'Downloads' folder mathching the regular expression pattern '/<org>.*.csv/' where 'org' refers to the specified or default organization
  - When using '-c' it can be followed by any list of field names in the '.csv' file.
  - The '.csv' file has to have a column named 'login' having the Github login of the members
```

Por ejemplo, para obtener  las urls de los alumnos en github podemos hacer:

```
✗ gh org-members -u | egrep -v 'crguezl|casiano'
"https://github.com/amarrerod"
... etc.
"https://github.com/alu0100879902"
```

Puede fusionar los resultados de la información de la API de GitHub con la información de la información en un archivo `.csv` usando las opciones `-c` y `-p`. Por ejemplo: 


```json
✗ gh org-members -jr Pere -c -p ./ULL-MFP-AET-2122.csv
[
  {
    "login": "Cami100260076",
    "name": "Camilo Glez. Peresola",
    "url": "https://github.com/Cami100260076",
    "role": "member",
    "site": "https://Cami100260076.github.io",
    "orgurl": "https://github.com/orgs/ULL-MFP-AET-2122/people/Cami100260076",
    "fullname": "Camilo Glez. Peresola",
    "id": "alu0100260076",
    "orden": "8",
    "Marca temporal": "26/10/2021 18:16:30",
    "Nombre 1": "Camilo",
    "Apellidos": "González Peresola",
    "Nombre": "Camilo",
    "Primer Apellido": "González",
    "Segundo Apellido": "Peresola",
    "Grado desde el que accede": "Ingeniería industrial",
    "Experiencia previa en la Enseñanza": "2",
    "markdown": "APTO",
    "profile": "APTO",
    "web site": "APTO",
    "pandoc": "APTO+",
    "TFP DCP": "APTO",
    "Calculada": "8,8",
    "Calificador Propuesta": "9",
    "Calificador propuesta": ""
  }
]
```

- Si se usa la opción `-c` pero el archivo `.csv` no se especifica a través de la opción `-p`, se usará el archivo `*.csv` más reciente en la carpeta `Downloads` de su O.S. que coincida con la expresión regular patrón `/<org>.*.csv/` donde `org` se refiere a la organización especificada o predeterminada
- Cuando se usa `-c`, puede ir seguido de cualquier lista de nombres de campo que ocurra en el archivo `.csv`.
- El archivo `.csv` debe tener una columna llamada `login` con el nombre de inicio de sesión en Github de los miembros de la organización

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

## Repository sizes in a GH Classroom organization 

See the Global Campus Teachers Discussion [97](https://github.com/community/Global-Campus-Teachers/discussions/97): 

> I have a GitHub Classroom organization that has exceeded the LFS quota. Is there any way to see which repository has caused this or an overview of how large each repository in the organization is? I know I can see repo sizes under https://github.com/settings/repositories, but this is just for the ones I have created. The GH classroom repos do not show up. Also, the organization's settings do not seem to have an overview of the sizes.
> 
> Anything that helps me to avoid cloning all the repos to determine their sizes is appreciated.

**Solution**:

The command `gh repo list`has the options:

```
      --json fields         Output JSON with the specified fields
  -L, --limit int           Maximum number of repositories to list (default 30)
```

Así un comando como:

```
✗ gh repo list ULL-MFP-AET-2122 --limit 999 --json name,diskUsage
```

Muestra el nombre del repo y su tamaño:

```
[
  {
    "diskUsage": 3,
    "name": ".github"
  },
  {
    "diskUsage": 6485,
    "name": "latex-markdown-chloe-boistel-perez-alu0100788020"
  },
  ... etc.
]
```

Si uno es un experto en [jq](https://stedolan.github.io/jq/) puede obtener el mayor elemento:

```
✗ gh repo list ULL-MFP-AET-2122 --limit 999 --json name,diskUsage  --jq 'max_by(.diskUsage)'
{"diskUsage":45756,"name":"static-generator-juan-alberto-cabrera-garcia-alu0100360912-"}
```

o bien ordenarlos:

```
➜  markdown git:(master) ✗ gh repo list ULL-MFP-AET-2122 --limit 999 --json name,diskUsage  --jq 'sort_by(.diskUsage) | reverse[0:2]'
[{"diskUsage":45756,"name":"static-generator-juan-alberto-cabrera-garcia-alu0100360912-"},{"diskUsage":45240,"name":"static-generator-noelia-rodriguez-hernandez-alu0100595420"}]
```

## Referencias

{% include references-gh.md %}
