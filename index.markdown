---
layout: default
---

<div>
  <ul class="listing">
  {% for post in site.posts limit: 1 %}
  <article class="content">
    <section class="title">
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
    </section>
    <section class="meta">
    <span class="time">
      <time datetime="{{ post.date | date:"%Y-%m-%d" }}">{{ post.date | date:"%Y-%m-%d" }}</time>
    </span>
    {% if post.tags %}
    <span class="tags">
      {% for tag in post.tags %}
      <a href="/tags.html#{{ tag }}" title="{{ tag }}">#{{ tag }}</a>
      {% endfor %}
    </span>
    {% endif %}
    <!-- BEGIN this would not work on any other domain -->
    <div class="bdlikebutton"></div>
    <script id="bdlike_shell"></script>
<script>
var bdShare_config = {
"type":"small",
"color":"blue",
"uid":"8888888",
"share":"yes"
};
document.getElementById("bdlike_shell").src="http://bdimg.share.baidu.com/static/js/like_shell.js?t=" + Math.ceil(new Date()/3600000);
</script>
    <!-- END this would not work on any other domain -->
    </section>
    <section class="post">
    {{ post.content }}
    </section>
    </article>
  {% endfor %}
  </ul>
  <div class="divider"></div>
  <ul class="listing main-listing">
    <li class="listing-seperator">Happend earlier this year</i>
  {% capture year %}{{ site.time | date:"%Y"}}{% endcapture %}
  {% for post in site.posts offset:1 %}
    {% capture y %}{{ post.date | date:"%Y"}}{% endcapture %}
    {% if year != y %}
    {% break %}
    {% endif %}
    <li class="listing-item">
      <time datetime="{{ post.date | date:"%Y-%m-%d" }}">{{ post.date | date:"%Y-%m-%d" }}</time>
      <a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a>
    </li>
  {% endfor %}
    <li class="listing-seperator"><a href="/archive.html">Long long ago</a></li>
  </ul>
</div>
