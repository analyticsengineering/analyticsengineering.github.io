
{% for page in site.pages %}
    <p>
    <a href="{{ page.url | relative_url }}">{{ page.title | escape }}</a>
    </p>
{% endfor %}
