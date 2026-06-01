---
layout: archive
title: "Teaching & Learning Hub"
permalink: /teaching/
author_profile: true
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /images/teaching-header.jpg
excerpt: "Interactive analytics teaching tools and practical tutorials for business analytics instructors."
---

{% include base_path %}

## 📊 Interactive Analytics Applets
*Interactive web applications designed for classroom demonstrations and student exploration.*

<div class="feature__wrapper">
  <div class="grid__wrapper">
    {% assign apps = site.teaching | where: "type", "app" %}
    {% for app in apps %}
      <div class="grid__item" style="border: 1px solid #f2f2f2; padding: 15px; border-radius: 8px; box-shadow: 0 2px 4px rgba(0,0,0,0.05);">
        {% if app.header.teaser %}
          <img src="{{ base_path }}/images/{{ app.header.teaser }}" alt="{{ app.title }}" style="border-radius: 4px; margin-bottom: 10px;">
        {% endif %}
        <h3 class="archive__item-title" style="margin-top: 0;">
          <a href="{{ app.url | prepend: base_path }}">{{ app.title }}</a>
        </h3>
        <p class="archive__item-excerpt" style="font-size: 0.85em;">{{ app.excerpt | truncate: 120 }}</p>
        <a href="{% if app.link %}{{ app.link }}{% else %}{{ app.url | prepend: base_path }}{% endif %}" class="btn btn--primary btn--small">Launch Live App</a>
      </div>
    {% endfor %}
  </div>
</div>

<hr style="margin: 40px 0;">

## 📝 Instructional Guides & Resources
*Practical tutorials and automated workflows designed to support instructors and streamline academic tasks.*

{% assign tutorials = site.teaching | where: "type", "tutorial" | sort: "date" | reverse %}
{% for post in tutorials %}
  <div class="list__item" style="margin-bottom: 30px;">
    <article class="archive__item" itemscope itemtype="http://schema.org/CreativeWork">
      <h3 class="archive__item-title" itemprop="headline">
        <a href="{{ post.url | prepend: base_path }}" rel="permalink">{{ post.title }}</a>
      </h3>
      <p class="page__meta" style="color: #888; font-size: 0.8em;">
        <i class="fa fa-fw fa-calendar" aria-hidden="true"></i> {{ post.date | date: '%B %d, %Y' }} &nbsp;
        <i class="fa fa-fw fa-clock-o" aria-hidden="true"></i> {% include read-time.html %}
      </p>
      <p class="archive__item-excerpt" itemprop="description">{{ post.excerpt | strip_html | truncate: 200 }}</p>
    </article>
  </div>
{% endfor %}
