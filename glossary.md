---
toc: false
---
 
<!-- Example data like: https://gist.github.com/ThoMo/fb3cb24dc8d14a53af97 -->

# Glossary


{% assign gs = site.data.glossary | sort %}
{% for kv in gs %}
### {{ kv[0] }} 

{{ kv[1] | markdownify }} 

{% endfor %}

## GitHub Glossary 

For git and GitHub related terms go here:

* [GitHub Glossary](https://docs.github.com/en/free-pro-team@latest/github/getting-started-with-github/github-glossary)

## GitHub Classroom Glossary

For GitHub Classroom Glossary terms go here:

* [GitHub Classroom Glossary](https://docs.github.com/en/education/manage-coursework-with-github-classroom/get-started-with-github-classroom/glossary)
