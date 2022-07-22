  {%- assign previousMonth = "0" %}
  {%- for post in site.categories["leccion"] reversed %}
     {%- assign currentMonth = post.date | date: "%B" %}
      {%- if currentMonth != previousMonth %}
<!-- ### Classes during the month of {{ currentMonth }} -->
      {%- endif %}
1. [{{ post.title }}]({{site.baseurl}}{{ post.url }}) 
  {%- if post.video %} 
  * [Vídeo]({{post.video}}) 
  {%- endif %}
      {%- assign previousMonth = currentMonth %}
  {%- endfor %}
