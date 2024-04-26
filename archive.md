
    {% for page in site.pages limit:10 %}
        <p>
        <a href="{{ page.url | relative_url }}">{{ page.title | escape }}</a>
        </p>
    {% endfor %}
