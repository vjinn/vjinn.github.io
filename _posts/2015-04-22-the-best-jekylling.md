---
layout: post
title: 더 간편하고 가벼우며 홀가분한 지킬링은 무엇인가
category: tip
---

데이터베이스 없이 정적 파일(html)로 마크다운을 사용하여 글쓰기에 집중하는 환경을 만들어 주는 지킬 이지만, 글쓰기에 들어가는 과정 및 글쓰기, 호스팅(Push) 방법, 보관(백업)을 좀 더 간편하게 하기 위한 **조합의 구상**은 끝이 없어 보인다. 지킬 설치 없는 지킬링을 기준으로 가능한 몇 가지를 생각해 보자.

## terminal

깃허브 호스팅을 사용한다는 가정에서 Git 패키지만 설치한다면 지킬을 설치하지 않아도 지킬링이 가능하다. 리눅스 또는 맥과 같은 터미널 환경이 있어야 한다.  Git을 지원하는 웹호스팅을 사용해도 된다.

적당한 템플릿(테마)을 클론하고, `nano`, `vim`, `vi` 등 터미널에서 사용할 수 있는 에디터를 이용하여 설정 및 포스팅하여 깃허브에 푸시하면 그만이다. 지킬을 설치하지 않고, 터미널 환경이므로 프리뷰만 포기하면 된다. 하지만 이미지나 다른 콘텐츠 소스 삽입 등이 필요할 때 번거롭다. 

누구 말처럼 [해커처럼 블로깅](http://tom.preston-werner.com/2008/11/17/blogging-like-a-hacker.html)(지킬링) 하고 싶다면 좋은 방법이다. 지킬 태생의 근간이 되는 방법으로 볼 수 있다.

## sublime-jekyll

지킬을 위한 [Sublime Text](http://www.sublimetext.com/) 에디터 패키지의 하나이다. 관련 내용은 아래의 링크에서 볼 수 있다. 2개의 링크에서 나오는 정보는 같다고 보면 된다.

 - [A Sublime Text package for Jekyll static sites](http://23maverick23.github.io/sublime-jekyll/)
 - [Package Control - sublime-jekyll](https://packagecontrol.io/packages/Jekyll)
 
윈도즈 운영체제를 기준으로 볼 때 Sublime Text 에디터는 PC 애플리케이션이다. 애플리케이션과 이 패키지를 설치해야 한다. 그런데 패키지 설치와 설정 안내를 보고 있으면 가슴이 막힌다. 블로깅보다는 개발을 위한 목적에 중심을 둔 것으로 보인다.

지킬을 설치하지 않아도 되고, PC 환경에서 에디터를 통한 지킬링이라는 점은 당연히 이점이다. 그래도 환경 구성의 과정과 실사용이 효율적일지는 물음표다.
 
## Markdown-Writer for Atom

[![Atom]({{ site.il }}/atom.png)]({{ site.il }}/atom.png)

깃허브의 텍스트 에디터 [Atom](https://atom.io/)에 추가하여 사용하는 지킬을 위한 패키지이다. 패키지를 떠나 Atom 에디터의 슬로건을 보면 감동이 잠깐 온다.

 > **_A hackable text editor for the 21st Century_**

Atom 실행 후 `File > Settings > Install > Search : markdown-writer > Install` 순으로 진행하면 `Packages > Markdown Writer` 메뉴를 볼 수 있으며 간단한 설정으로 에디터와 뷰 화면으로 구분하여 포스팅이 가능하다. 프론트 메터 정보도 깃허브처럼 뷰 화면에서 보여준다.

[![Atom package for Jekyll]({{ site.il }}/atom_markdown.png)]({{ site.il }}/atom_markdown.png)

몇 가지 설정이 필요한지 임의의 포스트 작성 후 퍼블리싱 과정에서 계속 오류가 발생했다. 어쨌든 PC 환경의 에디터에서 지킬링이 가능하며, 깃허브의 에디터라는 점에서 좀 더 이점이 있을 것으로 생각한다. 관련 내용은 아래의 링크를 참고하면 된다.

[Markdown-Writer for Atom](https://atom.io/packages/markdown-writer)

이 역시 지킬을 설치할 필요가 없지만 `sublime-jekyll`와 마찬가지로 뭔가 홀가분한 느낌이 없다.

## stackedit

[![Stackedit]({{ site.il }}/stackedit.png)](https://stackedit.io/)

벌써 널리 알려졌으며, 좋은 평가를 받고 있는 마크다운 에디터 크롬 앱이다. 실제로 아주 유용하며 효율적이다. 웹으로 깃허브에 접속하여 지킬 사이트를 운영하는 것을 제외하고 이 포스트의 제목에 가장 걸맞은 방법으로 생각한다.

 - 드롭박스, 구글 드라이브 파일과 연동, 싱크
 - 깃허브, 워드프레스, 텀블러, 블로거, FTP(SSH Server) 등에 퍼블리싱
 - 로컬, 웹 파일 임포트
 - 마크다운 비주얼 에디터 버튼 제공
 - 라이브 뷰 화면
 - 간편한 이미지 삽입 흐름
 - 폴더 분류 관리
 - GFM(GitHub Flavored Markdown)
 - `Ctrl + C` 조합으로 실시간 저장 (클라우드 싱크)
 - 아주 간편한 수정 및 업데이트

나열한 내용 외에 다른 기능들이 있지만 필요할 때 확인하면 된다. 지킬에 한정하여 볼 때 너무 과분한 기능들이다. 이미 많은 사람이 사용하고 있으므로 세부 내용은 검색하면 얻을 수 있을 것이다.

[![Stackedit Markdown]({{ site.il }}/stackedit_markdown.png)]({{ site.il }}/stackedit_markdown.png)

에디터를  설치하고 플러그인(패키지) 형식을 추가하여 지킬링 하는 방법과 비교할 때 (크롬에 제한적이지만) 웹브라우저와 인터넷만 가능하다면 어디서든 마크다운으로 포스팅, 깃허브 퍼블리싱(푸시), 클라우드 보관(싱크)이 가능하다는 점은 지킬링에 가장 최적화되어 있다고 생각한다.

## Github

웹에서 깃허브에 저장소를 만들고 맘에 드는 템플릿을 포킹하고 수정한 후 포스팅을 하면 된다. 지킬링 방법 중 이보다 더 간단한 방법은 없다. 탭으로 나뉜 프리뷰 화면도 있어 커밋 전 확인도 가능하다. 인터넷만 되면 된다.

---

위의 내용은 모두 **글쓰기**가 지킬 사용의 핵심 목적일 때를 기준으로 생각한 것이다.