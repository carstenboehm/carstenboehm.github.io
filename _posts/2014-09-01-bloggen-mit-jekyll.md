---
layout: post
comments: true
image: 
  feature: feature/noimg.png
title: bloggen mit Jekyll
modified: 2014-09-09
---

## prose.io
Das ist ein Test um mal zu schauen wie das mit dem bloggen via [prose.io](http://prose.io/) so klappt...

### my $0.02
Prinzipiell zwar nicht unbedingt notwendig da man auch schnell über das Github-Webinterface einen neuen Post anlegen könnte, aber komfortabel ist es schon ;) Vor allem wenn es darum geht, mal schnell ein, zwei Bilder anzuhängen. Das einzige was aus meiner Sicht noch fehlt ist die Möglichkeit, kleine Text-Snippets zu speichern – zum einen für die Metadaten und zum anderen dass man den HTML-Code für schöne Bilder nicht immer irgendwoher[^1] copypasten muss.

### good to know
Empfehlenswert ist außerdem, ein paar Settings in der `_config.yml`[^2] zu setzen, so dass Bilder im richtigen Verzeichnis landen und die Metadaten je Post sinnvoll vorausgefüllt werden... die möglichen Optionen sind im [Wiki](https://github.com/prose/prose/wiki/Prose-Configuration) beschrieben.

### Screenshot

<figure>
	<a href="{{ site.url }}/images/screen-prose.png"><img src="{{ site.url }}/images/screen-prose.png"></a>
	<figcaption>Screenshot von prose.io beim Schreiben dieses Beitrags.</figcaption>
</figure>


## liquid Templates
Was auch ganz cool ist ist die [Liquid](http://wiki.shopify.com/Liquid) Template Engine dahinter, die es recht einfach erlaubt *mal schnell was selber zu basteln* ohne sich tief einarbeiten zu müssen. 

Was damit möglich ist lässt sich an [diesem Blogeintrag]({% post_url 2012-09-29-shanghai-impressions %}) gut zeigen. Der zugrundeliegende Markdown-"Quelltext" sah anfangs so aus:




[^1]: [Beispielpost](http://mmistakes.github.io/minimal-mistakes/sample-post-images/) und [zugehöriger Quellcode](https://raw.githubusercontent.com/mmistakes/minimal-mistakes/master/_posts/2013-05-22-sample-post-images.md)
[^2]: Die für dieses Blog kann man [hier](https://github.com/carstenboehm/carstenboehm.github.io/blob/master/_config.yml) einsehen.
