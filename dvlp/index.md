## Development
개발과 관련된 글을 정리합니다.

{% for post in site.posts %}
{% if post.categories[0] == 'dvlp' %}
- [{{ post.title }} {{ post.categories }}](../{{ post.url }})
{% endif %}
{% endfor %}
