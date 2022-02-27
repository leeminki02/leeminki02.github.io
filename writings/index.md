{% for post in site.posts %}
    - [{{ post.title }} {{ post.categories }}]("{{ post.url }}")
{% endfor %}

====
{% for post in site.posts %}
    {% if post.categories[0] == 'writings' %}
        - [{{ post.title }} {{ post.categories }}]("{{ post.url }}")
    {% endif %}
{% endfor %}
