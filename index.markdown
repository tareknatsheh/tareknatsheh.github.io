---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: wrapper
---


<ul class="post-list">
    {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
    {% for post in site.posts %}
        <li>
            <span class="post-meta">{{ post.date | date: date_format }}</span>
            <h3>
            <a class="post-link" href="{{ post.url }}">
                {{ post.title }}
            </a>
            </h3>
        </li>
    {% endfor %}
</ul>