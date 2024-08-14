---
title: "[Elastic Search] Basics"
layout: archive
permalink: /es-basics
author_profile: true
sidebar:
    nav: "sidebar-category"
---

{% assign posts = site.categories.es-basics %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}