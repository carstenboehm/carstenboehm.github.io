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
Von daher wäre es eigentlich ganz komfortabel, in der Front Matter einfach das Verzeichnis anzugeben und Jekyll den Rest machen zu lassen. Es gibt auch bereits einige Plugins dazu, die aber bei GitHub deaktiviert sind. Von daher musste eine eigene Lösung her (ich weiß, der Code ist mehr als hässlich, aber ich bin hier durch Liquid Template Sprache beschränkt). In der [Doku](http://jekyllrb.com/docs/variables/) habe ich die Variable `site.static_files` gefunden, welche in einem Array die Dateinamen (einschl. Pfad) aller statischen Dateien der Webseite, also auch der Bilder, enthält. Damit sollte sich was anfangen lassen :grinning:

In meinem Fall gibt es je Fotostrecke ein eigenes Verzeichnis, in dem jeweils das Bild in *Fullsize*- und *Thumbnail*- Auflösung[^1] liegen, wobei die Thumbnails durch das Postfix `_tn` gekennzeichnet sind. Diese drei Variablen werden in der *Front Matter* hinterlegt:
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

In der `_layouts/post.html` sorgt nun folgender Code für die Weiterverarbeitung:
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
**Achtung:** Beim CopyPasten am besten alle Zeilenumbrüche entfernen. Die äußere Schleife iteriet über *alle* statischen Dateien der Webseite und erzeugt somit ggf. eine ganze Menge Zeilenumbrüche im fertigen HTML-Quelltext.
 {: .notice}

Im Prinzip wird also jede einzelne Datei aus `site.static_files` erstmal darauf überprüft, ob sie im angegeben Verzeichnis liegt, die passende Dateiendung aufweist und kein Thumbnail ist. Da in Jekyll aus irgend einem Grund der [split](http://docs.shopify.com/themes/liquid-documentation/filters/string-filters#split)-Filter nicht zu funktionieren scheint, geschieht dies indem versucht wird das Thumbnail-Postfix aus dem Dateinamen zu entfernen und danach die Dateiamen verglichen werden (Übereinstimmung --> kein Thumbnail). Anschließend wird der Thumbnail-Dateinamen synthetisiert und es wird überprüft ob eine entsprechende Datei in der `site.static_files` enthalten ist. Falls ja wird das Thumbnail eingebunden und das Fullsize-Bild verlinkt, andernfalls wird das Fullsize-Bild direkt in den `<img>`-Tag geschrieben. Funktioniert soweit :wink:

[^1]: Zur Erstellung der Thumbnails bietet sich auf dem Mac das Tool "[ThumbsUp](http://www.devontechnologies.com/products/freeware.html)" an.
