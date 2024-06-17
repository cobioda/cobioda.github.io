---
layout: archive
title: "CoBiODA projects"
permalink: /projects/
author_profile: true
---


{% include base_path %}



Past and ongoing project list supported by CoBiODA engineers. Please contact us directly in case you are interested to know the bioinformatics setup for a project. CoBiODA is dedicated to the IPMC research teams bioinformatics support.


{% for post in site.projects reversed %}
  {% include archive-single.html %}
{% endfor %}
