---
layout: post
comments: true
image: 
  feature: feature/noimg.png
title: testing prose.io
tags: 
  - tech
  - jekyll
modified: {}
published: true
---

<section id="table-of-contents" class="toc">
  <header>
    <h3>Übersicht</h3>
  </header>
<div id="drawer" markdown="1">
*  Auto generated table of contents
{:toc}
</div>
</section><!-- /#table-of-contents -->


## prose.io
Das ist ein Test um mal zu schauen wie das mit dem bloggen via [prose.io](http://prose.io/) so klappt...

#### my $0.02
Prinzipiell zwar nicht unbedingt notwendig da man auch schnell über das Github-Webinterface einen neuen Post anlegen könnte, aber komfortabel ist es schon ;) Vor allem wenn es darum geht, mal schnell ein, zwei Bilder anzuhängen. Das einzige was aus meiner Sicht noch fehlt ist die Möglichkeit, kleine Text-Snippets zu speichern – zum einen für die Metadaten und zum anderen dass man den HTML-Code für schöne Bilder nicht immer irgendwoher[^1] copypasten muss.

#### good to know
Empfehlenswert ist außerdem, ein paar Settings in der `_config.yml`[^2] zu setzen, so dass Bilder im richtigen Verzeichnis landen und die Metadaten je Post sinnvoll vorausgefüllt werden... die möglichen Optionen sind im [Wiki](https://github.com/prose/prose/wiki/Prose-Configuration) beschrieben.

#### Screenshot

<figure>
	<a href="{{ site.url }}/images/screen-prose.png"><img src="{{ site.url }}/images/screen-prose.png"></a>
	<figcaption>Screenshot von prose.io beim Schreiben dieses Beitrags.</figcaption>
</figure>


## liquid Templates
Was auch ganz cool ist ist die Template Engine dahinter. 

Ich will das mal an [diesem Blogeintrag]({% post_url 2012-09-29-shanghai-impressions %}) zeigen.

{% highlight html linenos %}
{% raw %}
---
layout: post
comments: true
image: 
  feature: feature/cnshanghaiskyline.jpg
title: "noch ein paar mehr Eindrücke aus Shanghai"
tags: [travel, photos, china]
published: false
---

#### (Fotopost)

<figure>
	<a href="{{ site.url }}/images/p/2012_china/moreshanghai/P9290893.jpg"><img src="{{ site.url }}/images/p/2012_china/moreshanghai/P9290893_tn.jpg"></a>
	<figcaption></figcaption>
</figure>
<figure>
	<a href="{{ site.url }}/images/p/2012_china/moreshanghai/P9290902.jpg"><img src="{{ site.url }}/images/p/2012_china/moreshanghai/P9290902_tn.jpg"></a>
	<figcaption></figcaption>
</figure>
<figure>
	<a href="{{ site.url }}/images/p/2012_china/moreshanghai/P9290915.jpg"><img src="{{ site.url }}/images/p/2012_china/moreshanghai/P9290915_tn.jpg"></a>
	<figcaption></figcaption>
</figure>
<figure>
	<a href="{{ site.url }}/images/p/2012_china/moreshanghai/P9290925.jpg"><img src="{{ site.url }}/images/p/2012_china/moreshanghai/P9290925_tn.jpg"></a>
	<figcaption></figcaption>
</figure>
<figure>
	<a href="{{ site.url }}/images/p/2012_china/moreshanghai/P9290948.jpg"><img src="{{ site.url }}/images/p/2012_china/moreshanghai/P9290948_tn.jpg"></a>
	<figcaption></figcaption>
</figure>
<figure>
	<a href="{{ site.url }}/images/p/2012_china/moreshanghai/P9290986.jpg"><img src="{{ site.url }}/images/p/2012_china/moreshanghai/P9290986_tn.jpg"></a>
	<figcaption></figcaption>
</figure>
{% endraw %}
{% endhighlight %}






[^1]: [Beispielpost](http://mmistakes.github.io/minimal-mistakes/sample-post-images/) und [zugehöriger Quellcode](https://raw.githubusercontent.com/mmistakes/minimal-mistakes/master/_posts/2013-05-22-sample-post-images.md)
[^2]: Die für dieses Blog kann man [hier](https://github.com/carstenboehm/carstenboehm.github.io/blob/master/_config.yml) einsehen.