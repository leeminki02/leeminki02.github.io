## Experiences
새로운 경험을 정리합니다.

{% for post in site.posts %}
{% if post.categories[0] == 'experiences' %}
- [{{ post.title }} {{ post.categories }}](../{{ post.url }})
{% endif %}
{% endfor %}
