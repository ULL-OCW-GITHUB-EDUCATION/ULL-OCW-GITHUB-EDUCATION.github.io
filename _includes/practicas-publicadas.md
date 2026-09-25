
<ol>
{%- for practica in site.tareas -%}
<li> 
  <a href="{{ site.baseurl}}{{ practica.url }}.html">{{ practica.title }}</a> 
</li>
{%- endfor -%}
</ol>


