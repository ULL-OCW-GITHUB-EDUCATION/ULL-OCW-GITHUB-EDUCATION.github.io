
<ol>
{%- for practica in site.tareas -%}
<li> 
  <a href="{{ site.baseurl}}{{ practica.url }}.html">{{ practica.title }}</a> 
  {% if practica.classroom %}
  <ul><li><a href="{{ practica.classroom }}" target="_blank">Acepta la asignación de la tarea</a></li></ul>
  {% endif %}
</li>
{%- endfor -%}
</ol>


