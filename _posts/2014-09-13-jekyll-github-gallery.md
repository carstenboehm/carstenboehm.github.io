---
layout: post
comments: true
image: 
  feature: feature/noimg.png
title: "GitHub-kompatible Bildergallerie mit Jekyll"
tags: 
  - tech
  - jekyll
---

Wie ich [schon geschrieben habe]({% post_url 2014-09-01-bloggen-mit-jekyll %}), nutze ich für dieses Blog Jekyll in Verbindung mit GitHub Pages. Nun gibt es hier ja so einige Posts, die hauptsächlich bis vollständig aus Fotos bestehen, und diese Fotostrecken liegen der Übersichtlichkeit halber auch bereits in eigenen Verzeichnissen.
Von daher wäre es eigentlich ganz komfortabel, in der Front Matter einfach das Verzeichnis anzugeben und Jekyll den Rest machen zu lassen. Es gibt auch bereits einige Plugins dazu, die aber bei GitHub deaktiviert sind. Von daher musste eine eigene Lösung her (ich weiß, der Code ist mehr als hässlich, aber ich bin hier durch Liquid Template Sprache beschränkt.

In meinem Fall gibt es je Fotostrecke ein eigenes Verzeichnis, in dem jeweils das Bild in *Fullsize*- und *Thumbnail*- Auflösung liegen, wobei die Thumbnails durch das Postfix `_tn` gekennzeichnet sind. Diese drei Variablen werden in der *Front Matter* hinterlegt:
{% highlight text linenos %}
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



{% highlight text linenos %}
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


{% highlight text linenos %}
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
