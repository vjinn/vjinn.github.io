---
layout: post
title: 깃허브 페이지에 지킬 사이트 호스팅
category: tip
---

![GitHub Pages]({{ site.il }}/github_pages.png)

<div class="message">
이 포스트는 깃허브에 지킬 사이트를 호스팅하는 내용이지만, 깃허브 관점이 아니라 지킬 소프트웨어 중심이다. 깃허브의 저장소, 브랜치에 대한 깊은 이해는 필요없다. 도메인 사용, 지킬 사이트 수 등의 호스팅 계획에 따른 선택의 문제라고 생각하면 된다. 또 배경지식이 없는 사용자 대상이므로 반대라면 꼭 볼 필요는 없다.
</div>

깃허브에 지킬 사이트를 호스팅하려면 먼저 **저장소(Repository)**를 생성해야 한다. 저장소를 만들면 `master`라는 브랜치가 생성된다. (브랜치는 **저장소 내 하나의 구분자**라고 단순하게 생각하자) 저장소의 `master` 브랜치에 지킬 사이트를 호스팅 하는 것을 **사용자(조직) 페이지**에 호스팅한다고 정의하자. 또 저장소 하나를 생성하고 터미널에서 `gh-pages`라는 브랜치를 만들어 지킬 사이트를 푸쉬하는 것을 **프로젝트 페이지**에 호스팅한다고 하자. 이 페이지에서 안내하는 내용은 이 두 가지이다.

## username.github.io

깃허브에 저장소 하나를 만들고 그 저장소의 `master` 브랜치에 지킬 사이트를 호스팅(게시, 푸쉬)하는 방법에 대해 알아보자. 이 방법만 알면 지킬 사이트 하나를 호스팅하는 것은 문제없다. 우선 웹브라우저에서 깃허브에 접속하여 다음의 순서로 해보자. **로컬 PC에 지킬 사이트 소스가 있다는 전제**의 내용이며, `username.github.io` 이름의 저장소가 없다는 기준에서 시작한다.

하나 더 기억할 것은 저장소 이름을 `username.github.io` 형식으로 정했을 때 지킬 사이트 (또는 일반 정적 사이트) 호스팅은 반드시 `master` 브랜치를 사용해야 한다.

1. 깃허브 로그인
1. 위쪽 **+** 아이콘 클릭 후 **New repository** 클릭
1. Repository name에 반드시 **username.github.io** 형식으로 입력 (username은 자신의 깃허브 아이디, `io` 대신에 `com` 사용 가능)
1. Create repository 버튼 클릭

위의 내용을 그대로 따라했다면 **Quick setup** 페이지가 나올 것이다. 페이지에 나오는 내용을 그대로 사용해도 되지만 로컬에 존재하는 사이트 파일이 있으므로 처음 경험하는 사용자라면 어려울 수 있다. 그대로 두고 터미널을 실행하여 [**지킬 사이트 소스 디렉터리**](/jekyll-basic/#사이트-생성,-사이트-변환-(소스-파일,-변환-파일))로 경로를 맞추자. 터미널에서 원하는 경로에 접근하는 방법을 모른다면 검색이나 질문을 통해 해결하기 바란다.

먼저 `git`이 설치되지 않았다면 다음을 참고하여 설치하자. 리눅스(우분투, 민트) 기준이며, 설치 확인은 필요는 없다. 아래 명령을 그냥 실행하면 된다. [윈도즈용 지킬 패키지](/install-jekyll/#portable-jekyll)에는 포함되어 있다.

```bash
$ sudo apt-get install git
```

다음으로 터미널에서 아래의 순서로 명령을 입력하자. `username` 부분만 자신의 것으로 입력하면 된다. 그전에 터미널 접속 위치가 지킬 사이트 소스 디렉토리가 맞는지 한 번 더 확인하자. 직접 입력이 어렵다면 웹브라우저에 있는 Quick setup 페이지에서 복사해서 사용해도 된다. 아래 내용은 리눅스, 윈도즈, 맥 등 모든 환경에서 똑같다.

```bash
$ git init
$ git remote add origin https://github.com/username/username.github.io.git
$ git add .
$ git commit -m "first commit"
$ git push origin master
```

다음으로 깃허브 아이디와 암호를 단계에 따라 입력하면 된다.

위의 명령은 현재 위치에서 `Git`을 사용하겠다는 선언, 원격 저장소의 위치(정보) 등록, 현재 위치에 있는 파일 전부(또는 변경 사항이 있는 파일)를 원격 저장소의 `master` 브랜치에 게시(푸쉬) 하겠다는 내용이다. 이것이 끝이다.

Quick setup 페이지가 있는 웹브라우저를 '새로고침' 해보자. 지킬 사이트 소스가 나타날 것이다. 그리고 웹브라우저에서 `http://username.github.io` (username에 자신의 아이디를 입력) 입력으로 지킬 사이트를 확인해 보자.

새로운 포스트 작성, 기존 파일 수정 등 이후부터는 세 번째 명령부터 진행하면 된다. 네 번째 명령라인 큰따옴표 안의 내용은 파일 변동사항에 대한 간략 메시지를 입력하는 것으로 필수 항목이며, 한글도 된다. 또 [이모티콘]({% post_url 2015-01-28-jekyll-plugins-and-github-pages %}#jemoji) 입력도 가능하다.

`Git`을 처음 사용한다면 위의 명령을 입력하고 실행하는 과정에서 일종의 전역 설정에 대한 메시지를 볼 수 있다. `git config --global`이 포함된 메시지가 나온다면 아래를 참고하여 한글 부분만 자신의 정보를 입력하자.

```bash
$ git config --global user.name "깃허브 아이디"
$ git config --global user.email 메일주소
```

## username.github.io/projectname

한 사람이 프로젝트 페이지를 생성하여 지킬 사이트를 호스팅할 이유는 두 가지 밖에 없다.

 - 그냥 프로젝트 페이지에 게시하고 싶어서 (저장소 이름을 간단하게 하고 싶거나)
 - 하나의 깃허브 계정에 여러 사이트를 호스팅하고 싶어서

프로젝트 페이지를 생성하는 방법은 아래의 링크에서 찾을 수 있다.

 - [Creating Project Pages manually](https://help.github.com/articles/creating-project-pages-manually/)

위의 링크에 나와 있는 내용을 바탕으로 프로젝트 페이지를 생성하고 지킬 사이트를 호스팅하는 방법을 알아보자. 

우선 위에서 잠깐 이야기 했지만 한 번 더 말하면, `master` 브랜치를 사용하는 사용자 페이지에서는 저장소를 생성할 때 반드시 `username.github.io` 형식으로 저장소 이름을 정해야 한다고 했다. 다시 말하면 프로젝트 페이지를 사용하여 지킬 사이트를 호스팅할 때 저장소 이름에 `username.github.io` 형식은 안된다와 똑같다.

깃허브 계정에 생성한 저장소가 하나도 없다는 기준, 이 프로젝트 페이지에 게시할 지킬 사이트 소스 디렉터리는 아직 없다는 가정이다. 아래의 순서로 진행해 보자.

1. 깃허브 로그인
1. 위쪽 **+** 아이콘 클릭 후 **New repository** 클릭
1. Repository name에 **원하는저장소이름** 입력 (영문으로 입력, 설명을 위해 이후부터 저장소 이름을 **jekyllsite**라 가정)
1. **Initialize this repository with a README** 항목을 반드시 선택
1. Create repository 버튼 클릭

위의 과정을 완료했다면 마스터 브랜치 화면으로 전환된 상태일 것이다. 4번을 진행한 이유는 저장소를 활성화 하기 위한 것이다.

이제 터미널을 실행하고 지킬 사이트를 생성할 위치에 경로를 맞추고 다음의 명령을 실행하자.

```bash
$ git clone https://github.com/username/jekyllsite.git
$ cd jekyllsite
$ git checkout --orphan gh-pages
$ git rm -rf *
```

위의 내용은 깃허브 아이디가 `username`인 사용자의 이미 존재하는 저장소 `jekyllsite`를 그대로 가져와서 `gh-pages` 브랜치로 전환하겠다는 내용이다. 존재하는 저장소를 복제함으로써 저장소 이름의 디렉터리 `jekyllsite`도 생성하고, 그 디렉터리 안의 위치에서 `git`을 사용하겠다는 `git init`도 함께 실행한 것과 같다.

세 번째 명령에서 `gh-pages` 브랜치 이름은 원하는 것을 입력해도 된다. 그러면 저장소에 그 이름으로 브랜치가 생성되며, 이후 파일을 푸쉬할 때도 그 브랜치 이름을 사용하여 푸쉬하면 된다.
 
복제한 파일에 디렉터리가 없다면 세 번째와 네 번째의 순서를 바꿔서 실행하면 `-rf` 옵션은 사용하지 않아도 된다. 만약 숨겨진 파일이나 디렉터리가 있다면 위의 네 번째 명령으로 지워지지 않으므로 별도로 지정해서 지워야 한다. 지금 과정에서는 가져온 파일이 하나라는 것을 알고 있지만, 아닐 경우 `.git` **디렉터리만 빼고 모두 지우는 것**이 좋다.

위의 과정만으로는 저장소에 `gh-pages` 브랜치가 나타나지 않는다. 아직 푸쉬한 파일이 없기 때문이다. 하지만 위의 과정만으로 프로젝트 페이지에 지킬 사이트를 호스팅할 준비는 끝이다. 지킬 사이트 소스를 로컬 PC의 `jekyllsiste` 디렉터리에 만든 후 푸쉬만 하면 된다.

우선 테스트를 위해 `index.html` 파일을 만들어 푸쉬하여 확인해 보자. 터미널 경로는 현재 `jekyllsite` 디렉터리 안에 맞춰져 있을 것이다. 다음의 내용을 실행하자.

```bash
$ echo "index" > index.html
$ git add .
$ git commit -m "first test"
$ git push origin gh-pages
```

파일 `index.html`을 만들어 `gh-pages`라는 브랜치에 푸쉬한다는 내용이다. 만일 Checkout 과정에서 입력한 브랜치 이름이 `site`였다면 푸쉬할 때 다음과 같이 입력해야 한다.

```bash
$ git push origin site
```

깃허브 저장소에서 `master` 대신 `gh-pages` 브랜치를 선택하면 `index.html` 파일이 나타날 것이다. 확인을 위해 웹브라우저에 `username.github.io/jekyllsite` URL을 입력하자. `username`에는 자신의 깃허브 아이디를 입력하는 것을 잊지 말자. 저장소 이름도 `jekyllsite`가 아니라면 자신이 정한 저장소 이름을 입력하자. 웹브라우저에 'index'라는 텍스트가 있는 페이지가 나오면 성공이다. 프로젝트 페이지에 지킬 사이트를 호스팅하면 URL은 `username.github.io/저장소이름` 형태로 구성된다.

이제는 지킬 사이트를 게시해 보자. 우선 방금 만든 `index.html` 파일을 지운다.

```bash
$ git rm index.html
```

현재 터미널 접속 경로가 `jekyllsite` 디렉터리 안에 있을 것이다. 이 상태에서 `jekyll new` 명령으로 현재 위치에 기본 사이트 템플릿을 생성하자. `.git` 디렉터리 외 다른 파일이나 디렉터리는 없어야 한다. 지금까지 과정을 그대로 진행했다면 없을 것이다.

```bash
$ jekyll new .
```

깃허브 저장소 `gh-pages` 브랜치에 푸쉬하자.

```bash
$ git add .
$ git commit -m "second test"
$ git push origin gh-pages
```

웹브라우저에서 사이트를 확인해 보자. 사이트가 나오지만 형태가 어긋나 있을 것이며, 링크의 경로가 맞지 않을 것이다. 사이트 소스의 `_config.yml` 파일을 열어 경로를 조정해야 한다. 글쓰는 시점의 지킬 버전 2.5.3의 기본 템플릿의 `_config.yml` 파일을 열어 아래의 두 곳만 참고하여 자신에게 맞게 수정한 후 저장하자.

```yaml
baseurl: "/jekyllsite"
url: "http://username.github.io/jekyllsite/"
```

다시 저장소의 해당 브랜치에 푸쉬하자.

```bash
$ git add .
$ git commit -m "second test2"
$ git push origin gh-pages
```

웹브라우저에서 사이트를 확인하면 제대로 표현되는 것을 확인할 수 있다.

사용 또는 선택한 테마에 따라 다를 수 있으므로 `_config.yml` 파일 수정만으로 올바른 표현이 나오지 않을 때는 레이아웃 템플릿 파일을 열어 경로 정의를 어떻게 설정했는지 확인해야 한다.

깃허브 계정에 생성한 저장소가 하나도 없다는 가정을 둔 것은 `master` 브랜치의 username.github.io 저장소가 없어도 프로젝트 페이지에 지킬 사이트 호스팅이 가능함을 확인하기 위해서이다.

프로젝트 페이지의 사이트 URL을 신경쓰지 않는 방법은 사용자 도메인(자신의 도메인, 커스텀 도메인)을 사용하는 것이다.

## CNAME

사용자(조직) 또는 프로젝트 페이지에 지킬 사이트를 호스팅할 때 자신의 도메인을 사용하려면 원하는 도메인 주소가 들어간 `CNAME` 파일을 만들어 함께 푸쉬하면 간단하게 해결된다. 프로젝트 페이지의 URL 때문에 테마의 설정을 변경하지 않아도 된다. *(일부 테마는 배포 시 서브 경로를 지정하여 배포하는 경우가 있으므로 확인해야 한다.)* 

TLD(Top Level Domain), 서브도메인 무엇이든 상관없다. 도메인이 있다는 것과 DNS 정보를 변경할 수 있다는 조건만 있으면 된다.

다음과 같이 깃허브의 계정 아이디가 **veteran**일 때 사용자 페이지(`master`), 프로젝트 페이지(`gh-pages`)의 깃허브 제공 도메인과 새롭게 적용할 자신의 도메인이 다음과 같다고 가정하자. 

|    저장소 이름     |  브랜치 이름 | 깃허브 제공 URL           | **사용자 도메인** |
| ------------------| ----------- | ------------------------ | ----------------|
| veteran.github.io | master      | veteran.github.io        | **aaa.com**     |
| mysite            | gh-pages    | veteran.github.io/mysite | **bbb.com**     |

위의 조건으로 사용하려면 제일 먼저 도메인의 DNS 정보를 변경하는 것이다. 도메인을 구입한 사이트에서 **DNS 레코드 관리**와 비슷한 메뉴를 찾아서 **A 레코드** 또는 **CNAME 레코드** 추가 항목에 정보를 등록하면 된다. 위의 예를 기준으로 하면 다다음과 같이 할 수 있다.

| A 레코드 | IP 정보 |
| ------- | -------------- |
| aaa.com | 192.30.252.153 |
| aaa.com | 192.30.252.154 |
| bbb.com | 192.30.252.153 |
| bbb.com | 192.30.252.154 |

위의 IP는 깃허브에서 안내하는 정보이며, TLD의 경우 IP를 안내하고 있지만 꼭 IP를 사용하지 않아도 된다. 다음과 같이 CNAME에 정보를 입력할 수 있다.

| CNAME   | 연결 정보 |
| ------- | -------------- |
| aaa.com | veteran.github.io |
| bbb.com | veteran.github.io |

서브도메인도 마찬가지이다. CNAME 입력란에 원하는 내용을 입력하면 된다. 예를 들면 다음과 같다.

| CNAME   | 연결 정보 |
| ------- | -------------- |
| 123.aaa.com | veteran.github.io |
| 456.bbb.com | veteran.github.io |

도메인을 구입한 곳에서 DNS 레코드 관리 서비스를 제공하지 않는다면 [DNSZI](https://dnszi.com/)나 [dnsever](https://kr.dnsever.com/)와 같은 서비스를 이용하면 된다. 'dnsever'의 경우는 유료 서비스다.

DNS 레코드 정보를 등록했다면 `CNAME` 파일을 만들면 된다. 이 파일은 확장자가 없는 대문자 파일명, 내용에는 `http(s)://` 없이 도메인만 입력해야 한다. 터미널의 CUI 환경이나 데스크톱의 GUI 환경을 이용하여 각각의 지킬 사이트 소스 디렉터리에 이 파일을 만들자.

| 도메인 | 파일명 | 내용 |
| ------- | ----- | ------- |
| aaa.com | CNAME | aaa.com |
| bbb.com | CNAME | bbb.com |

파일을 만든 후 각각 깃허브에 푸쉬하자. 사용자 페이지(`master`)에 등록할 경우는 다음과 같을 것이다.

```bash
$ git add . (또는 git add CNAME)
$ git commit -m "add aaa.com"
$ git push origin master
```

프로젝트 페이지(`gh-pages`) 경우는 아래와 같을 것이다.

```bash
$ git add . (또는 git add CNAME)
$ git commit -m "add bbb.com"
$ git push origin gh-pages
```

웹브라우저에서 각 도메인을 입력하여 지킬 사이트를 확인하면 된다.

도메인을 막 구입했다면 해당 도메인으로 지킬 사이트 확인은 보통 1분이면 가능하다. 지킬 사이트에 사용하기 위해 네임서버를 막 변경했다면 시간이 걸릴 수 있다. 만약 테스트 하고 싶다면 새로운 서브도메인을 생성하여 적용하면 빨리 확인할 수 있을 것이다.

깃허브에 100개든 1,000개든 사이트를 호스팅하는 것은 DNS 레코드 설정, CNAME 파일 및 내용추가, 사이트마다의 저장소 추가, 각 브랜치 생성이면 된다. `master` 브랜치를 사용하여 지킬 사이트를 호스팅하기 위해서는 `username.github.io` 형식의 이름으로 저장소를 만들어야 한다는 것과 하나의 계정에 1개만 가능하다는 것만 기억하자.

브랜치 `master`에 TLD를 사용하는 것은 하나의 깃허브 계정에 주어지는 `username.github.io`를 변경할 수 있으므로 이후에 생성하는 `gh-pages` 브랜치의 사이트 URL을 별도의 도메인으로 사용하지 않고 디렉터리 구조로 사용한다면 DNS 레코드 설정이나 CNAME 파일 추가를 하지 않아도 되므로 유리하다.

도메인 사용 계획에 따라 효율적인 방법을 선택하는 것이 좋다.

## 참고

### 브랜치 삭제

이 페이지의 내용은 지킬 사이트를 호스팅하는 것이 목적이지 깃허브 시스템을 이해하여 프로젝트를 진행하는 것이 아니다. 따라서 프로젝트 페이지를 사용하여 `gh-pages` 브랜치에 지킬 사이트를 호스팅한다면 브랜치 `master`는 사용하지 않으므로 지우면 좋다. 우선 웹브라우저 깃허브에서 해당 저장소의 설정 페이지로 이동하자. 설정 페이지 URL은 `https://github.com/username/저장소이름/settings` 형태이다.

**Default branch** 항목에서 `gh-pages`를 선택하자.

![Default branch]({{ site.il }}/dfghpages.gif)

터미널에 다음과 같이 입력하고 실행하자. 터미널 경로가 해당 지킬 사이트 디렉터리인지 항상 염두에 두어야 한다.

```bash
$ git push origin :master
```

다시 웹브라우저에서 해당 저장소를 확인해 보면 `master` 브랜치가 보이지 않을 것이다.

### git rm

`git` 정보가 있는 사이트 디렉터리에서 만약 특정 파일을 삭제할 때 다음과 같이 실행했다 가정하자.

```bash
$ rm aaaa.md
```

그리고 다시 깃허브에 게시하기 위해 다음의 명령을 실행했다고 하자.

```bash
$ git add .
```

아마 친절한 안내 메시지가 나올 것이다. 이 메시지는 `git` 명령을 통한 파일 삭제가 아니었기 때문에 나오는 것으로 이럴 경우는 다음과 같이 입력하고 실행하면 된다.

```bash
$ git add -A
```

위와 같은 메시지가 나오지 않게 할려면 파일 삭제 시 다음과 같이 실행하면 된다.

```bash
$ git rm aaaa.md
```

## 참고

이 페이지의 내용은 아래의 링크에서 얻을 수 있는 정보를 포함하고 있다. 처음 경험하는 사용자나 배경지식이 없을 경우 아래의 정보를 통해서 원하는 결과를 금방 얻기가 쉽지 않을 것이다. 배경지식이 있다면 사용자 도메인 적용은 IP 정보와 같은 일부만 획득하여 직접 적용하는 것이 더 효율적일 수 있다.

 - [GitHub Pages](https://pages.github.com/)
 - [Using Jekyll with Pages](https://help.github.com/articles/using-jekyll-with-pages/)
 - [the GitHub Pages Gem]({{ site.gl }}/github/pages-gem)
 - [Dependency versions](https://pages.github.com/versions/)
 - [Deploying Jekyll to GitHub Pages](http://jekyllrb.com/docs/github-pages/)
 - [Custom Domain](https://help.github.com/search/?utf8=%E2%9C%93&q=custom+domain)
