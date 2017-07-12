---
title: "Research"
layout: gridlay
excerpt: "Research."
sitemap: false
permalink: /research/
---


# Research

## Highlights

(For a full list of publications see [below](#full-list) or go to [Google Scholar](https://scholar.google.com/citations?user=uZvvcgUAAAAJ&hl=en)
{% assign number_printed = 0 %}
{% for project in site.data.proj_list %}

{% assign even_odd = number_printed | modulo: 2 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-6 clearfix">
 <div class="well">
  <pubtit style="text-decoration: underline;">{{ project.title }}</pubtit>
  <img src="{{ site.url }}{{ site.baseurl }}/images/proj_pics/{{ project.image }}" class="img-responsive" width="33%" style="float: left" />
  <p><strong>{{ project.summary }}</strong></p>
  <p>{{ project.description }}</p>
  <!-- <p><em>{{ project.collaborators }}</em></p> --> 
  

  {% assign have_pubs = 0 %}      
  {% for pub in site.data.pub_list %}
  {% if pub.tag == project.tag and pub.highlight == 1 %}
	  {% assign have_pubs = 1 %}    
  {% endif %}  
  {% endfor %}

  {% if have_pubs == 1 %}
  <p><strong style="text-decoration: underline;">Selected Publications:</strong>.</p>
  {% endif %}  

  {% for pub in site.data.pub_list %}
  {% if pub.tag == project.tag and pub.highlight == 1 %}
  <p><strong><a href="{{ site.baseurl}}/{{ pub.link.url }}">{{ pub.title }}</a></strong> {{ pub.venue_code }}      </p> 
  {% endif %}  
  {% endfor %}
  
  <p class="text-danger"><strong> {{ publi.news1 }}</strong></p>
  <p> {{ project.news2 }}</p>
 </div>
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}
{% endfor %}

{% assign even_odd = number_printed | modulo: 2 %}
{% if even_odd == 1 %}
</div>
{% endif %}

<p> &nbsp; </p>


## Full List

#### <span style="text-decoration: underline;">Highly-Refereed Conference Publications</span>
{% assign print_workshop = 0 %}
{% for publi in site.data.pub_list %}

  {% if publi.code contains 'W'  and print_workshop == 0%}
#### <span style="text-decoration: underline;">Lightly-Refereed Publications</span>  
  {% assign print_workshop = 1 %}
  {% endif %}

  <strong >[{{ publi.code }}] </strong>
  <a href=" {{ site.baseurl }}/{{ publi.link.url }}">{{ publi.title }} </a> <br />
  {{ publi.authors }}
  <br />
  <em>{{ publi.venue }}</em>
  <br />
  <span style="color: red;">{{ publi.awards }}</span>

{% endfor %}

