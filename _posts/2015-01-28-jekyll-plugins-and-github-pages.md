---
layout: post
title: 지킬 플러그인과 깃허브 페이지 플러그인
category: tip
---

간단하며 기본적인 지킬 플러그인이 몇가지 있는데 다음과 같다.

 - [Jemoji]({{ site.gl }}/jekyll/jemoji) : 지킬 사이트 변환 시 그래픽 이모티콘 표현
 - [Jekyll-mentions]({{ site.gl }}/jekyll/jekyll-mentions) : `@`+`username` 사용만으로 깃허브 계정 링크로 자동 변환
 - [Jekyll-redirect-from]({{ site.gl }}/jekyll/jekyll-redirect-from) : 포스트나 페이지 접근 시 특정 URL로 리디렉트
 - [Jekyll-sitemap]({{ site.gl }}/jekyll/jekyll-sitemap) : 지킬 사이트의 사이트맵 생성 (로컬에서는 사이트 변환 시)

위의 4가지 플러그인은 로컬에서 다음과 같이 설치할 수 있다.

```bash
$ gem install jemoji
$ gem install jekyll-mentions
$ gem install jekyll-redirect-from
$ gem install jekyll-sitemap
```

설치 후 4가지 플러그인 모두 `_config.yml` 파일에 다음과 같이 추가만 하면 된다. 물론 사용을 원하는 플러그인만 입력한다.

```yaml
gems:
 - jekyll-mentions
 - jemoji
 - jekyll-redirect-from
 - jekyll-sitemap
```

## Jemoji

설치와 설정 파일 추가 후 글쓰기에 원하는 이미티콘 텍스트를 입력하면 되고, 이모티콘 시트는 아래의 2개의 링크에서 참고 하자.

 - [Emoji searcher](http://emoji.muan.co/)
 - [Emoji cheat sheet](http://www.emoji-cheat-sheet.com/)

아래 예제에서 진한 부분의 텍스트처럼 입력하면 된다.

 - 지킬 플러그인 `jemoji`는 정말 최고입니다. **:+1:**
 - 오늘은 지킬 씨의 100번 째 **:100:** 생일입니다.

별개로 [Gemoji]({{ site.gl }}/github/gemoji)라는 것도 있는데, 깃허브 시스템(사이트)에서 사용할 수 있으며, 터미널에서 깃허브로 사이트를 푸쉬할 때 커밋 메시지에 넣을 수도 있다.

```bash
$ git commit -m "아침엔 :apple:"
```

## Jekyll-mentions

글쓰기에 깃허브 사용자의 소스를 참고하여, 글 내용에 해당 사용자의 깃허브 페이지를 링크할 때 아주 유용하다. 트위터 맨션처럼 생각하면 된다. 하지만 맨션에 대한 알림은 안된다. 다음과 같이 단순하게 입력하면 된다.

 - 이 사이트는 @jekyll로 구성했다. (o)
 - 지킬 저장소는 @jekyll/jekyll이다. (x)

기본 값이 깃허브 URL이지만 원하는 정보로 변경할 수 있다. `_config.yml`에 정의하면 된다. 아래의 `base_url`의 값을 원하는 값으로 입력하면 된다.

```yaml
jekyll-mentions:
  base_url: https://twitter.com
```

## Jekyll-sitemap

로컬에서 사이트를 변환하면 `_site`에 `sitemap.xml` 파일을 생성한다. 설치와 설정만 하는 것으로 끝이다. 처음 설치했다면 `_site` 디렉터리를 확인하여 사이트맵 파일이 생성되는지 한 번만 확인하자.

## Jekyll-redirect-from

예를 들어, 이전에 작성한 `aaa.md` 포스트가 있고 실제 포스트 주소를 `/aaa/`라고 하자. `bbb.md` 포스트를 작성하면서 프런트 메터(front-matter)에 다음과 같은 옵션을 추가했다고 가정하자.

```yaml
redirect_from:
  - /aaa/
```

사이트 변환 후 실제 웹사이트에서 /aaa/ 포스트로 접근하면 /bbb/ 포스트로 리디렉트한다. `_site` 디렉터리에서 `/aaa/index.html` 파일을 열면 다음과 같은 내용으로 변경되어 있을 것이다. 사이트 소스 디렉터리의 `aaa.md` 파일의 내용은 변하지 않으므로 걱정하지 않아도 된다.

```html
<!DOCTYPE html>
<meta charset=utf-8>
<title>Redirecting...</title>
<link rel=canonical href="/bbb/">
<meta http-equiv=refresh content="0; url=/bbb/">
<h1>Redirecting...</h1>
<a href="/bbb/">Click here if you are not redirected.</a>
<script>location='/bbb/'</script>
```

여러 포스트를 리디렉트할 수 있다. 위의 설정 예에서 /aaa/ 밑으로 원하는 포스트 URL을 입력하면 된다.

```yaml
redirect_from:
  - /aaa/
  - /ccc/
  - /ddd/
```

주의할 것은 **'/'**와 **사이트 변환 시 생성되는 포스트 URL**을 입력해야 한다는 것이다. 직접 테스트하면 금방 알 수 있다.

## Github Pages

위의 4가지 플러그인은 깃허브에 호스팅을 한다면 로컬에 설치하지 않아도 된다. 설정 파일에 추가하는 것만 진행 후 깃허브에 푸쉬하면 된다. **깃허브 페이지**가 이 플러그인을 지원하기 때문이다. 패키지 버전이 다를 수 있지만, 위의 플러그인들은 문제가 거의 없을 것이다.

 - [Using Jekyll Plugins with GitHub Pages](https://help.github.com/articles/using-jekyll-plugins-with-github-pages/)

플러그인을 설치하지 않고 설정에만 추가했는데 사이트 변환 명령을 실행하면 에러 메시지가 나올 것이다. 설정은 있는데 플러그인이 설치되지 않아서 나오는 메시지이므로 걱정할 것 없다. 하지만 사용하는 플러그인이라면 로컬에서도 설치하는 것이 좋다.

깃허브가 아니라면 플러그인을 설치, 설정하여 사이트 변환 후 `_site`의 파일을 내보내면 된다.
