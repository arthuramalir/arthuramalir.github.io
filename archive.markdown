---
layout: default
title: Blog Archive
permalink: /archive/
---

<div style="font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, 'Liberation Mono', 'Courier New', monospace; font-size: 0.9rem; line-height: 1.7; color: #e0e0e0; letter-spacing: -0.01em;">

<span style="color: #6a737d;">// blog posts</span>

<div style="margin: 2rem 0;">
  {% for post in site.posts %}
    <div style="margin: 1.5rem 0; padding-left: 1rem; border-left: 2px solid #4fc1ff;">
      <p style="margin: 0.3rem 0; color: #fff;">
        <a href="{{ post.url }}" style="text-decoration: none; color: #4fc1ff;">{{ post.title }}</a>
      </p>
      <p style="margin: 0.3rem 0; color: #6a737d; font-size: 0.85rem;">
        {{ post.date | date: "%B %d, %Y" }}
      </p>
    </div>
  {% endfor %}
</div>

{% if site.posts.size == 0 %}
<p style="color: #aacaf6;">No posts yet. Check back soon!</p>
{% endif %}

</div>
