## Studies
공부한 내용을 정리합니다.

{% for post in site.posts %}
{% if post.categories[0] == 'studies' %}
- [{{ post.title }} {{ post.categories }}](../{{ post.url }})
{% endif %}
{% endfor %}
