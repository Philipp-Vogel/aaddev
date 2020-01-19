# Blog Posts

{% for post in site.posts %}
<div>
    <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
</div>
{% endfor %}



