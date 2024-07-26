---
title: "[Python] 제어문"
layout: archive
permalink: /python-cs
author_profile: true
sidebar:
    nav: "sidebar-category"
---

{% assign posts = site.categories.python-cs %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}