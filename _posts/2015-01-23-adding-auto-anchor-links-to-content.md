---
layout: post
title: 마크다운 엔진과 상관없이 문서에 자동으로 앵커 태그 링크 표현
category: tip
---

지킬 공식 웹사이트는 문단 제목에 마우스를 올리면 링크 아이콘이 나타나며, 그 아이콘에 마우스를 올리면 문단 제목의 주소가 나타난다.

![jekeyllrb.com]({{ site.il }}/anchor_jekyllrb.png)

## Kramdown

지킬 공식 웹사이트는 현재 마크다운 엔진으로 `kramdown`을 사용 중인 것으로 보인다. 이 엔진을 사용하여 문서를 작성 후 사이트를 변환하면 자동으로 `id=문단 제목` 형식으로 소스가 생성된다. 예를 들어, 문단 제목이 **Jekyll is Awesome**, 문서 작성 시 `## Jekyll is Awesome`으로 입력했다면 사이트 변환 후 `html` 소스는 다음과 같이 생성된다.

{% highlight html %}
<h2 id="jekyll-is-awesome">
{% endhighlight %}

마크다운 엔진으로 `kramdown`만 사용해도 `#, ##, ...`와 같은 문단 계층 구분으로 문서 작성 시 자동으로 문단의 `id`가 부여되므로 하나의 페이지 내에 존재하는 고유주소가 된다. 사이트 내부 또는 외부에서 문서 참조로 활용할 수 있다. 하지만 역시 문제가 있다.

 - 한글과 같은 2byte 문자의 경우에 `id=section-N` 형태로 표시
 - 영어와 한글을 혼용해서 사용할 경우에 알고 싶지 않은 규칙의 다양한 형태로 나온다는 것
 - `kramdown` 엔진을 사용해야 한다는 것

*(권유하고 싶지 않지만)* 어쨌거나 `kramdown` 엔진을 사용하면서 지킬 공식 사이트와 같이 제목에 마우스를 올렸을 때 링크 아이콘 노출과 아이콘 클릭으로 문단 주소를 웹브라우저의 주소란에서 쉽게 얻으려면 아래의 문서나 지킬 공식 웹사이트의 [저장소]({{ site.gl }}/jekyll/jekyll/tree/master/site)에서 소스를 참고하면 된다. **괜한 고생을 할 수도 있다.**

 - @parkr's [Header Anchor Links in Vanilla JavaScript for GitHub Pages and Jekyll](http://blog.parkermoore.de/2014/08/01/header-anchor-links-in-vanilla-javascript-for-github-pages-and-jekyll/)

## 마크다운 엔진과 상관없이 적용하기

마크다운 엔진을 `kramdown`만 사용해야 한다면 재미없다. 그리고 위의 방법은 귀찮은 방법이며 적용한 사이트 소스를 그대로 가져오지 않는 한 단번에 적용하기 어렵다. *(귀찮아서 그만뒀다)* 이제 마크다운 엔진과 무관하게, 한글 차별없는 방법을 알아보자. 정말 간단하다.

우선 아래의 @bryanbraun **anchorjs** 깃허브 저장소로 가자.

 - [A tiny javscript utility for adding anchor links to existing page content]({{ site.gl }}/bryanbraun/anchorjs)

필요한 것은 2개의 파일 `anchor.min.js`, `anchor.css` 그리고 `index.html` 소스 맨 아래의 일부 코드이다.

{% highlight js %}
    var selector = 'h2';
    addAnchors(selector);
{% endhighlight %}

텍스트 설명은 하지 않는다. 아래의 영상으로 대신한다.

<div class="video">
<iframe width="560" height="315" src="//www.youtube.com/embed/Bo4tkLZAY8U" frameborder="0" allowfullscreen></iframe>
</div>

영상과 같이 스크립트 삽입 시 `_includes` 디렉터리에 `anchor.html` 파일로 만들어 템플릿에는 인클루드 태그를 사용하는 것이 좋다.

이 사이트는 `kramdown` 엔진으로 이 페이지의 내용을 적용했으므로 이 사이트의 저장소 [소스]({{ site.repo }})를 참고하면 도움 되지 않을까 생각한다.
