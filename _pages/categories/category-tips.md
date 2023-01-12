---
title: "왜 에러일까 싶으면 보는 Tips"
layout: archive
permalink: categories/tips
author_profile: true
sidebar_main: true
---


{% assign posts = site.categories.tips %}
{% for post in posts %} {% include archive-single.html type=page.entries_layout %} {% endfor %}