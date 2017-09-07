---
layout: page
title: 지킬 사이트
permalink: /jekyll-site/
menutitle: 사이트
number: 5
---

지킬 사이트를 운영중이라면 아래의 지킬 공식 깃허브 저장소 위키에 추가하면 된다. 깃허브 계정만 있다면 누구나 편집이 가능하다.

 - [공식 깃허브 지킬 저장소의 사이트 위키]({{ site.gl }}/jekyll/jekyll/wiki/Sites)

우리나라 지킬 사용자 사이트만 보려면 아래의 경로를 보면 된다. 역시 누구나 편집이 가능하므로 자신의 사이트를 등록해도 된다.

 - [우리나라 지킬 사용자 사이트 위키]({{ site.repo }}/wiki/지킬-사이트)

---
 
아래는 개인적으로 사이트 내에 게재하는 우리나라 지킬 사이트 목록이다. 위의 우리나라 사이트 위키 정보와 다르지 않다. 정렬 기준은 없고, 소스를 공개하는 사이트 중심이다. 사이트 소유자의 사전 동의는 얻지 않지만 불편하다면 즉시 알려주기 바란다.

{% for jsite in site.data.jsites %}
- <a href="{{ jsite.link }}">{{ jsite.name }}</a> (<a href="{{ site.gl }}/{{ jsite.source }}">Source</a>) - {{ jsite.desc }}
{% endfor %}
