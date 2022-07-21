
<ol>
{%- for practica in site.tareas -%}
<li> 
  <a href="{{ practica.url }}">La Práctica {{ practica.title }}</a>
</li>
{%- endfor -%}
</ol>


