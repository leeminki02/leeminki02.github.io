## Technical Writings
연구나 개발 등에 대한 기술적 글을 기록합니다.

{% for post in site.posts %}
{% if post.categories[0] == 'writings' %}
- [{{ post.title }} {{ post.categories }}]("{{ post.url }}")
{% endif %}
{% endfor %}
