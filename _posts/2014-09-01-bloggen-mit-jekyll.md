---
layout: post
comments: true
image: 
  feature: feature/noimg.png
title: bloggen mit Jekyll (und GitHub Pages)
tags: 
  - tech
  - jekyll
modified: 2014-09-13
---

## Ausgangssituation
Nachdem ich in 2012 (anlässlich einer Reise – seitdem hat sich hier auch inhaltlich nicht mehr viel getan) bei Tumblr ein Blog erstellt habe, passt zwei Jahre später das Konzept nicht mehr für mich. Konkret: Die Texte, Bilder usw... einfach an irgend eine Webplattform zu verfüttern, ohne Exportmöglichkeit und mit der Gefahr dass was kostenlos war plätzlich *premium* oder vom Mutterkonzern[^1] dichtgemacht wird.

<figure>
	<a href="{{ site.url }}/images/holycrepeold.png"><img src="{{ site.url }}/images/holycrepeold.png"></a>
	<figcaption>Das alte tumblr-Blog</figcaption>
</figure>


## getting startet with Jekyll
Also musste eine Alternative her. Auf [Apps N Coffee](http://www.appsncoffee.de/) wurde vor kurzem ein Tutorial (Teil [1](http://www.appsncoffee.de/2014/07/01/Tutorial-Teil1-Jekyll-GitHubPages/) [2](http://www.appsncoffee.de/2014/07/09/Tutorial-Teil2-Jekyll-GitHubPages/) [3](http://www.appsncoffee.de/2014/07/15/Tutorial-Teil3-Jekyll-GitHubPages/)) zu [Jekyll](http://jekyllrb.com/) veröffentlicht, was dann auch der Anstoß für mich war mich näher damit zu beschäftigen. Kurz gesagt: Theme suchen (z.B. [hier](http://jekyllthemes.org/)), Repository auf GitHub forken und umbenennen, `_config.yml` und Design nach eigenen Wünschen anpassen, loslegen :smile:

Jekyll ist ein *Static Site Generator*, d.h. nach jeder Änderung gibt es einen *Build*-Prozess in dem die Quelldateien (HTML-Templates, Layouts, Posts, ...) zu statischen HTML-Seiten zusammengesetzt werden. Die kann man dann einfach via FTP auf jedenbeliebigen Webspace schieben. Oder man benutzt [GitHub Pages](https://pages.github.com/); wenn man auf GitHub ein Repository mit den Quelldateien pflegt läuft der Build-Prozess direkt dort ab und die Seiten sind anschließend unter `deinnutzername.github.io` (oder optional einer eigenen Domain) zugänglich. Der eigentliche Inhalt wird dabei in Markdown geschrieben (und in `*.md`-Dateien gespeichert), denen man ein (Front Matter)[http://jekyllrb.com/docs/frontmatter/] mit Metadaten voranstellen sollte.

Das waren dann auch die Punkte die mich überzeugt haben Jekyll mal auszuprobieren:

* Keine Wordpress-Installation, die man irgendwo pflegen muss
* Sehr komfortables Hosting via GitHub Pages (und die Exit-Strategie ist schon eingebaut: gibt es GitHub Pages irgendwann nicht mehr kann ich jederzeit lokal die Seite bauen und auf jeden beliebigen Webspace schieben)
* Anpassungen sind über die [Liquid](http://docs.shopify.com/themes/liquid-documentation/basics) Template Engine recht einfach möglich (siehe unten)

## nächste Schritte 

### mobiles Bloggen
Wer mobil bloggen will kann einfach online im GitHub-Repository eine neue Datei unterhalb von `_posts` anlegen und in Markdown-Syntax losschreiben. Das selbe gilt für das Ändern bestehender Inhalte. Bei jedem neuen *Commit* baut GitHub die Webseite automatisch neu.

#### prose.io
Komfortabler geht es mit [prose.io](http://prose.io/), einer Webapp die es ermöglicht Posts in gewohnter WYSIWYG-Manier zu verfassen und vor allem auch mal mobil (vom iPad oder einem Rechner ohne GitHub-Client) ein Bild hochzuladen. Im Prinzip also eine komfortable Spielerei. Das einzige was aus meiner Sicht noch fehlt ist die Möglichkeit, kleine Text-Snippets zu speichern – zum einen für die Metadaten und zum anderen dass man den HTML-Code für schöne Bilder nicht immer irgendwoher[^2] copypasten muss.

Empfehlenswert ist es, ein paar Settings in der `_config.yml`[^3] zu setzen, so dass Bilder im richtigen Verzeichnis landen und die Metadaten je Post sinnvoll vorausgefüllt werden... die möglichen Optionen sind im [Wiki](https://github.com/prose/prose/wiki/Prose-Configuration) beschrieben.

<figure>
	<a href="{{ site.url }}/images/screen-prose.png"><img src="{{ site.url }}/images/screen-prose.png"></a>
	<figcaption>Screenshot von prose.io beim Schreiben dieses Beitrags.</figcaption>
</figure>

#### Octopage
Für iOS-Geräte gibt es außerdem die App [Octopage](https://itunes.apple.com/us/app/octopage-blogging-jekyll-markdown/id649843345?mt=8), die sich zwar auch auf die Basisfunktionen beschränkt aber für 89 Cent macht man wenig falsch. Wer professionell schreibt wird sich wohl ohnehin mit [Editorial](http://omz-software.com/editorial/) seinen eigenen Workflow zurechtgebastelt haben.


### Eigene Anpassungen
Wie oben schon geschrieben nutzt Jekyll die [Liquid](http://wiki.shopify.com/Liquid) Template Engine, die es recht einfach erlaubt mal schnell was selber zu basteln ohne sich tief einarbeiten zu müssen. 

Was damit möglich ist lässt sich an [diesem Blogeintrag]({% post_url 2012-09-28-shanghai-impressions %}) gut zeigen. Der zugrundeliegende Markdown-"Quelltext" sah anfangs so aus:

{% highlight html linenos %}
{% raw %}
---
layout: post
comments: true
image: 
  feature: feature/cnshanghaiskyline.jpg
title: "noch ein paar mehr Eindrücke aus Shanghai"
tags: [travel, photos, china]
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

Nicht wirklich schön. Man kann dem Post aber auch einfach eine Liste der Bilder, die man zeigen möchte, in den Metadaten (heißt hier *Front Matter*) mitgeben:

{% highlight html linenos %}
{% raw %}
---
layout: post
comments: true
image: 
  feature: feature/cnshanghaiskyline.jpg
title: "noch ein paar mehr Eindrücke aus Shanghai"
tags: [travel, photos, china]
fotos:
  filepath: "images/p/2012_china/moreshanghai/"
  images:
    - filefs: "P9290893.jpg"
      filetn: "P9290893_tn.jpg"
    - filefs: "P9290902.jpg"
      filetn: "P9290902_tn.jpg"
    - filefs: "P9290915.jpg"
      filetn: "P9290915_tn.jpg"
    - filefs: "P9290925.jpg"
      filetn: "P9290925_tn.jpg"
    - filefs: "P9290948.jpg"
      filetn: "P9290948_tn.jpg"
    - filefs: "P9290986.jpg"
      filetn: "P9290986_tn.jpg"
---

#### (Fotopost)
{% endraw %}
{% endhighlight %}

Schon deutlich übersichtlicher. Das funktioniert, weil Jekyll alle Felder aus der Front Matter, die nicht [global vordefiniert](http://jekyllrb.com/docs/frontmatter/#predefined-global-variables) sind, an die Template-Engine durchreicht. Jetzt muss man nur noch in der `layouts/post.html` eben diese Felder auswerten. Der Platzhalter für den (HTML-formatierten) Text des Beitrags heißt `{% raw %}{{ content }}{% endraw %}`. Dahinter kann man nun folgendes ergänzen:

{% highlight html linenos %}
{% raw %}
{% if page.fotos %}
{% for foto in page.fotos.images %}
<figure>
  {% if foto.filetn %}
    <a href="{{ site.url }}/{{ page.fotos.filepath }}{{ foto.filefs }}"><img src="{{ site.url }}/{{ page.fotos.filepath }}{{ foto.filetn }}"></a>
  {% else %}
    <a href="{{ site.url }}/{{ page.fotos.filepath }}{{ foto.filefs }}"><img src="{{ site.url }}/{{ page.fotos.filepath }}{{ foto.filefs }}"></a>
{% endif %}
<figcaption>{{ foto.caption }}</figcaption>
</figure>
{% endfor %}
{% endif %} 
{% endraw %}
{% endhighlight %}

Hier gibt `filefs` den Dateinamen des Originalbildes an (*fullsize*), `filetn` den des Thumbnails. Außerdem kann mit `caption` noch ein Bildtitel angegeben werden. Außer `filefs` sind alle Parameter optional.

Der resultierende HTML-Code dürfte annähernd der gleiche sein, aber man spart sich Tipparbeit und Fehlersuche. Und wenn man mal später das ganze schöner gestalten will ändert man nur noch bequem die Layout-Datei ab.

Im wesentlichen kann Liquid die Basics wie Schleifen, Verzweigungen, und bringt nen Haufen an Formatierungsoptionen mit. Da man aber auch Datenstrukturen aus externen Dateien nutzen kann (auf die Daten aus `_data/foo.yml` lässt sich beispielsweise über `site.data.foo` zugreifen) kann man damit schon etwas Ordnung schaffen.

**Update:** Mittlerweile habe ich auch einen Weg gefunden, einfach ein Bilderverzeichnis an einen Post anzuhängen (auch wenn man ab und an liest, GitHub Pages ließe keinen Zugriff auf das Dateisystem zu). **[Hier weiterlesen]({% post_url 2014-09-13-jekyll-github-gallery %})**.
{: .notice}


### lokales Jekyll
Vor allem zur Fehlersuche und Entwicklung ist es sinnvoll, Jekyll auch mal lokal laufen zu lassen. Ich hab dazu (unter MacOS) einfach eine neue virtuelle Linux-Maschine aufgesetzt – muss man nicht machen, erspart aber das Gefrickel mit HomeBrew und Co.

Der Grund ist, dass die Fehlermeldungen die GitHub verschickt nicht immer aussagekräftig sind. Ich hatte via `{% raw %}{% post_url 2014-02-29-beispielpost %}{% endraw %}` einen internen Link gesetzt und irgendwann später den verlinkten Artikel umbenannt. Die E-Mail-Benachrichtigung über den fehlgeschlagenen Build-Versuch sah dann folgendermaßen aus:
{% highlight html %}
The page build failed with the following error:

Page build failed. For more information, see https://help.github.com/articles/using-jekyll-with-pages#troubleshooting.
{% endhighlight %}
Da kann man, vor allem wenn man nicht jede kleine Änderung gleich Committet, schon mal einige Stunden den Fehler suchen :angry:

[^1]: Tumblr gehört seit Mitte 2013 zu Yahoo.
[^2]: [Beispielpost](http://mmistakes.github.io/minimal-mistakes/sample-post-images/) und [zugehöriger Quellcode](https://raw.githubusercontent.com/mmistakes/minimal-mistakes/master/_posts/2013-05-22-sample-post-images.md)
[^3]: Die für dieses Blog kann man [hier](https://github.com/carstenboehm/carstenboehm.github.io/blob/master/_config.yml) einsehen.
