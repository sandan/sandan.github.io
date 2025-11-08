---
layout: archive
permalink: /
title: "Blog posts"
author_profile: true
---

{% include base_path %}
{% capture written_year %}'None'{% endcapture %}
{% if paginator %}
  {% assign posts_list = paginator.posts %}
{% else %}
  {% assign posts_list = site.posts %}
{% endif %}

{% for post in posts_list %}
  {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
  {% if year != written_year %}
    <h2 id="year-{{ year | slugify }}" class="archive__subtitle">{{ year }}</h2>
    {% capture written_year %}{{ year }}{% endcapture %}
  {% endif %}
  {% include archive-single.html %}
{% endfor %}

{% if paginator %}
  {% include paginator.html %}
{% endif %}
