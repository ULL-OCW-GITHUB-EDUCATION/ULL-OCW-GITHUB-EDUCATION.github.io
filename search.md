---
layout: default
permalink: /search/
title: Búsqueda
---

{% capture initSearch %}

<h1>{{page.title}}</h1>

<form id="search-form" action="">
  <label class="label" for="search">Frase a buscar (puede usar una expresión regular en el texto de la búsqueda):</label>
  <br/>
  <input class="input" id="search" type="text" name="search" autofocus placeholder="" autocomplete="off">
  
  <ul class="list  list--results" id="list">
  </ul>
</form>

<script type="text/javascript" src="{{site.baseurl}}/assets/src/fetch.js"></script>
<script type="text/javascript" src="{{site.baseurl}}/assets/src/search.js"></script>

<script type="text/javascript">

  const search = new JekyllSearch(
    '{{site.baseurl}}/assets/src/search.json',
    '#search',
    '#list',
    '{{site.baseurl}}'
  );
  search.init(); 
  
</script>

<noscript>Please enable JavaScript to use the search form.</noscript>

{% endcapture %}

{{ initSearch | lstrip }}

# Glosario

* [Glosario]({{site.baseurl}}/glossary.html)

<!--

# Tópicos

* [Tópicos]({{site.baseurl}}/topics)

-->