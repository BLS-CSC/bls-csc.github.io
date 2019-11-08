---
layout: default
---

# Python Tutorials

{% for tut in site.data.python-tutorials %}
 - [{{tut.name}}]({{tut.url}})
{% endfor %}

