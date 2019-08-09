---
layout: page
title: Wiki
description: 人越学越觉得自己无知
keywords: 维基, Wiki
comments: false
menu: Wiki
permalink: wiki/
---

> 以下wiki非本人编辑， 只是觉得不错， 保留下来。后续可能会更新自己的wiki并注明。如有侵权，请联系本人删除，谢谢。

<ul class="listing">
{% for wiki in site.wiki %}
{% if wiki.title != "Wiki Template" %}
<li class="listing-item"><a href="{{ site.url }}{{ wiki.url }}">{{ wiki.title }}</a></li>
{% endif %}
{% endfor %}
</ul>
