---
title: This will be used as the title-tag of the page head
---

<html dir="ltr" lang="en">
<head>
  <!-- Global site tag (gtag.js) - Google Analytics -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=UA-131795192-1"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());

    gtag('config', 'UA-131795192-1');
  </script>

  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>{{ site.title }}</title>
	<meta name="keywords" content="{{ site.keywords }}">
	<meta name="description" content="{{ site.description }}">
  <link rel="stylesheet" href="combo.css">
  <link href="https://fonts.googleapis.com/css?family=Open+Sans:300,300i,400,400i" rel="stylesheet">
  <link rel="stylesheet" href="//netdna.bootstrapcdn.com/font-awesome/4.2.0/css/font-awesome.min.css">
  {% if site.favicon %}<link rel="shortcut icon" href="{{ site.favicon }}" type="image/x-icon">{% endif %}
	{% if site.touch_icon %}<link rel="apple-touch-icon" href="{{ site.touch_icon }}">{% endif %}
	<style>
		#pro_bono_coaching {
			padding: 60px;
		}
	</style>
</head>
<body>
  <div id="main">

    <header id="masthead" class="site-header" role="banner" style="background-color: #000; color: #ffffff;">
    </header>

<!--
    <nav><ul>
      {% for node in site.posts reversed %}
        {% capture id %}{{ node.id | remove:'/' | downcase }}{% endcapture %}
        <li class="p-{{id}}"><a href="#{{id}}">{{node.title}}</a></li>
      {% endfor %}
    </ul></nav>
-->

    {% for page in site.posts reversed %}
		{% if page.title contains "Pro bono -coaching" %}
      {% capture id %}{{ page.id | remove:'/' | downcase }}{% endcapture %}
      <div id="{{id}}" class="section p-{{id}}">
        {% if page.icon %}
        <div class="subtlecircle sectiondivider imaged">
          <img src="{{page.icon}}" alt="section icon" />
          <h5 class="icon-title">{{ page.title }}</h5>
        </div>
        {% elsif page.fa-icon %}
        <div class="subtlecircle sectiondivider faicon">
          <span class="fa-stack">
            <i class="fa fa-circle fa-stack-2x"></i>
            <i class="fa fa-{{ page.fa-icon }} fa-stack-1x"></i>
          </span>
          <h5 class="icon-title">{{ page.title }}</h5>
        </div>
        {% endif %}
        <div class="container {{ page.style }}">
          {{ page.content }}
        </div>
      </div>
      {% if page.bottom-image %}
      <img src="{{ page.bottom-image }}" style="height: 100%; width: 100%; object-fit: contain;"/>
      {% endif %}
      {% if page.kuosi %}
      <div class="kuosi">
        <!--<embed src="img/HK_kuosi.svg"/>-->
      </div>
      {% endif %}
			{% endif %}
    {% endfor %}

  </div>

{% include analytics.html %}
</body>
<script src="//ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
<script src="site.js"></script>
</html>