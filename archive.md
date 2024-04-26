<ul id="recent-articles">
{% for page in site.pages %}
    <li>
    <a href="{{ page.url | relative_url }}">{{ page.title | escape }}</a>
    </li>
{% endfor %}
</ul>
