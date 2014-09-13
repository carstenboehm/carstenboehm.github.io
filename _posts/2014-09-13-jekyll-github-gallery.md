---
layout: post
comments: true
image: 
  feature: feature/noimg.png
title: "hässlicher Code (GitHub-kompatible Gallery mit Jekyll)"
tags: 
  - tech
  - jekyll
published: false
---


{% highlight html linenos %}
{% raw %}
{% if page.bilderordner %}
{% for bild in site.static_files %}
{% assign bildpfadarr = bild.path | split: '/' %}
{% assign bildfilename = bildpfadarr | last %}
{% assign bildpfad = bild.path | remove: bildfilename %}
{% assign filenametemp = bildfilename | remove: page.bilderordner.thumbext %}
{% if bildpfad == page.bilderordner.filepath and bildfilename == filenametemp %}
  {% assign thumbpfad = bild.path | remove: page.bilderordner.fileext | append: page.bilderordner.thumbext %}
  {% assign hasthumb = site.static_files | where: "path", thumbpfad | size%}
  <figure>
  {% if hasthumb == 1 %}
    <a href="{{ site.url }}{{ bild.path }}"><img src="{{ site.url }}{{ thumbpfad }}"></a>
  {% else %}
    <a href="{{ site.url }}{{ bild.path }}"><img src="{{ site.url }}{{ bild.path }}"></a>
  {% endif %}
  </figure>
{% endif %}
{% endfor %}
{% endif %}
{% endraw %}
{% endhighlight %}


{% highlight html linenos %}
{% raw %}
---
layout: post
comments: true
tags: [travel, photos, china]
bilderordner:
  filepath: "/images/p/2012_china/1eindruck/"
  fileext: ".jpg"
  thumbext: "_tn.jpg"
---
{% endraw %}
{% endhighlight %}
