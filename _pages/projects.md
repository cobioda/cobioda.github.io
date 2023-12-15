---
layout: archive
title: "Active projects"
permalink: /projects/
author_profile: true
---


{% include base_path %}


Listing of projects supported by CoBiODA engineers


{% for post in site.projects reversed %}
  {% include archive-single.html %}
{% endfor %}
