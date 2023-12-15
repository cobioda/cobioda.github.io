---
layout: archive
title: "Active projects"
permalink: /projects/
author_profile: true
---


{% include base_path %}



Listing of past and active projects supported by CoBiODA engineers. Please contact us directly in case you are interested to know the bioinformatics setup for a project. CoBiODA is dedicated to the IPMC research teams bioinformatics support.



{% for post in site.projects reversed %}
  {% include archive-single.html %}
{% endfor %}
