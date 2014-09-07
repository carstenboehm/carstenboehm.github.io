---
layout: post
comments: true
image: 
  feature: feature/cndragon.jpg
title: Shanghai: Erste Eindrücke
fotostrecke:
  - image:
      imgurl: images/p/2012_china/P9200299.jpg
      tnurl: images/p/2012_china/P9200299_tn.jpg
  - image:
      imgurl: images/p/2012_china/P9200309.jpg
      tnurl: images/p/2012_china/P9200309_tn.jpg
  - image:
      imgurl: images/p/2012_china/P9200315.jpg
      tnurl: images/p/2012_china/P9200315_tn.jpg
  - image:
      imgurl: images/p/2012_china/P9200320.jpg
      tnurl: images/p/2012_china/P9200320_tn.jpg
  - image:
      imgurl: images/p/2012_china/P9200342.jpg
      tnurl: images/p/2012_china/P9200342_tn.jpg
  - image:
      imgurl: images/p/2012_china/P9200394.jpg
      tnurl: images/p/2012_china/P9200394_tn.jpg
  - image:
      imgurl: images/p/2012_china/P9200413.jpg
      tnurl: images/p/2012_china/P9200299_tn.jpg
  - image:
      imgurl: images/p/2012_china/P9200426.jpg
      tnurl: images/p/2012_china/P9200426_tn.jpg
---

#### Bilder

{% for image in page.fotostrecke %}
<figure>
	<a href="{{ site.url }}/{{ image.imgurl }}"><img src="{{ site.url }}/{{ image.tnurl }}"></a>
	<figcaption>{{ image.text }}</figcaption>
</figure>
{% endfor %}