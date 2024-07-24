---
title: "[Python] 자료형"
layout: archive
permalink: /python-datatypes
author_profile: true
sidebar:
    nav: "sidebar-category"
---


{% assign posts = site.categories.python-datatypes %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}