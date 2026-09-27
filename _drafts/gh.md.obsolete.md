---
title: Afirmaciones obsoletas o incorrectas en el capítulo de GitHub CLI
---

Revisión del capítulo [`pages/gh.md`](../pages/gh.md), contrastada con la documentación oficial consultada el 27 de septiembre de 2026. Se incluyen afirmaciones y ejemplos que no funcionan o que ya no describen el comportamiento documentado. Las salidas antiguas y los números de repositorios se consideran ejemplos históricos, no falsedades por sí mismos.

## Afirmaciones que hay que corregir

### Placeholders de `gh api`

El capítulo dice que los placeholders `:owner`, `:repo` y `:branch` se sustituyen por los valores del repositorio actual, y los usa en `repos/:owner/:repo/issues`.

La sintaxis documentada actualmente usa llaves: `{owner}`, `{repo}` y `{branch}`. Hay que actualizar los endpoints y los valores de ejemplo, por ejemplo:

```sh
gh api repos/{owner}/{repo}/issues
```

Fuente: [gh api](https://cli.github.com/manual/gh_api).

### Método HTTP y conversión de campos en `gh api`

El texto presenta `GET` como método por defecto sin indicar que añadir parámetros cambia el método automáticamente a `POST`. También usa `-f private=true` como si el valor se enviara como booleano.

Actualmente, `gh api` usa `GET` si no se añaden parámetros y cambia a `POST` al añadirlos, salvo que se indique otro método. `-f` (`--raw-field`) envía valores como cadenas; para que `true`, `false`, `null` y los enteros se conviertan a tipos JSON, se debe usar `-F` (`--field`). Por tanto, el ejemplo que crea un repositorio privado debe usar `-F private=true` (o enviar un cuerpo JSON apropiado), no `-f private=true`.

Fuente: [gh api: método y opciones de campos](https://cli.github.com/manual/gh_api).

### Uso de `--paginate` con GraphQL

Varios ejemplos ejecutan `gh api graphql --paginate` con consultas que no declaran `$endCursor` ni solicitan `pageInfo { hasNextPage endCursor }`. Esto incluye los ejemplos de contar repositorios, obtener los últimos repositorios, listar issues y añadir una reacción.

Para paginar una consulta GraphQL, `gh api` requiere que la consulta acepte `$endCursor: String` y que lea `pageInfo { hasNextPage endCursor }` de una conexión. Tal como están escritos, esos ejemplos no cumplen el contrato de paginación. En el ejemplo de contar repositorios, además, `totalCount` ya devuelve el total y no necesita `--paginate`. En el ejemplo de añadir una reacción, la operación es una mutación y no debe presentarse como una consulta paginada.

Fuente: [gh api: modo `--paginate`](https://cli.github.com/manual/gh_api).

### Comando para borrar un repositorio

El ejemplo usa `gh repo-delete OWNER/REPO` como si fuera un subcomando integrado. El comando actual de GitHub CLI es `gh repo delete OWNER/REPO`; `repo-delete` no aparece entre los subcomandos de `gh repo`.

Fuente: [gh repo](https://cli.github.com/manual/gh_repo) y [gh repo delete](https://cli.github.com/manual/gh_repo_delete).

### Alias `my-orgs-names`

El alias de ejemplo ejecuta `gh my-orgs`, pero antes se ha definido `org-members`, no `my-orgs`. Sin que exista otro alias o extensión local con ese nombre, el ejemplo falla. Además, `/orgs/{org}/members` devuelve usuarios miembros, no objetos de organización con un campo `organization.login`; esa ruta de `jq` no sirve para extraer nombres de organizaciones.

Fuente: [List organization members](https://docs.github.com/en/rest/orgs/members#list-organization-members).

### Explicación del flujo de autenticación web

El texto dice que el navegador pide la contraseña que aparece en la terminal. En el flujo de dispositivo, la terminal muestra un código de un solo uso y el usuario lo introduce en GitHub para autorizar la CLI; no es la contraseña.

Fuente: [gh auth login](https://cli.github.com/manual/gh_auth_login).

## Incidencia de seguridad relacionada

El ejemplo de `curl` para la API contiene una cadena con aspecto de token en el encabezado `Authorization`. No es una afirmación falsa, pero no debe publicarse un token real ni dejarse una credencial con aspecto real en material docente. Sustituirla por un marcador como `<TOKEN>` y, si la credencial llegó a ser válida, revocarla y generar otra.

## Afirmaciones antiguas que no son falsas por sí solas

La versión `gh 2.14.3`, las salidas de terminal, nombres de organizaciones y recuentos de repositorios son instantáneas históricas. Conviene actualizarlos si se busca que el capítulo sea una guía vigente, pero no se clasifican aquí como afirmaciones falsas.

## Referencias principales

* [GitHub CLI manual](https://cli.github.com/manual/)
* [gh api](https://cli.github.com/manual/gh_api)
* [gh auth login](https://cli.github.com/manual/gh_auth_login)
* [gh repo delete](https://cli.github.com/manual/gh_repo_delete)
* [REST API: List organization members](https://docs.github.com/en/rest/orgs/members#list-organization-members)