---
title: Ports
nav_order: 3
has_children: true
permalink: /ports/
---

# Ports

{% include todo.html text="One paragraph: what a port is here, what the states mean. See also Compare and Failed ports." %}

<div class="cards" markdown="0">
{%- for p in site.data.ports %}
  <a class="card" href="{{ p.url | relative_url }}">
    <div class="photo-frame"><span>PHOTO</span></div>
    <p class="card-title">{{ p.name }} {% include badge.html state=p.state %}</p>
    <p>{{ p.blurb }}</p>
  </a>
{%- endfor %}
</div>
