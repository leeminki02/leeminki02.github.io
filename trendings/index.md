## Trendings
새롭거나 흥미로운 Weekly 소식을 기록합니다.

{% for post in site.posts %}
{% if post.categories[0] == 'trendings' %}
- [{{ post.title }} {{ post.categories }}]("{{ post.url }}")
{% endif %}
{% endfor %}
