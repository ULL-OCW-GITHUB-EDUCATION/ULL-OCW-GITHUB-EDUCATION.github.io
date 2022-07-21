
<ol>
{%- for practica in site.tareas -%}
<li> 
  <a href="{{ practica.url }}">{{ practica.title }}</a>
</li>
{%- endfor -%}
</ol>


