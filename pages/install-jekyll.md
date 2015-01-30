---
layout: page
title: 운영체제별 지킬 설치와 사용
permalink: /install-jekyll/
menutitle: 설치
number: 3
---

사용 환경(운영체제)별 지킬 설치에 대해 알아보자. 우선 지킬 설치는 환경보다 지킬 버전에 따른 기준을 충족해야 한다. 새로운 지킬 버전이 있다면 공식 사이트에서 추가로 필요한 패키지가 무엇인지 확인하고 설치하면 된다는 것을 기억하자.

아래의 링크(영, 한)를 가끔 찾아보자.

 - [Installation](http://jekyllrb.com/docs/installation/)
 - [설치](http://jekyllrb-ko.github.io/docs/installation/)

## 리눅스에서 지킬 설치

이 글에서 안내하는 리눅스에서의 지킬 설치는 지킬 **1.x**, **2.x**, **3.x** 버전 모두에 똑같이 적용된다. 가장 큰 기준은 지킬이 요구하는 루비(Ruby) 소프트웨어를 각 배포판의 패키지 관리자(`apt-get` 같은)로 설치하지 않고 **RVM(Ruby Version Manager)**으로 설치한다는 것이다. 맥이나 이 글에서 안내하지 않는 다른 리눅스 배포판도 거의 같다.

배포판의 패키지 관리자로 설치하는 루비는 해당 배포판에 최적화되어 있다고 할 수 있다. 지킬의 새로운 버전이 배포판에 없는 루비 버전을 요구할 때 번거로운 과정을 진행해야 하는데 배경지식이 없을 때는 귀찮다. 복잡한 것은 아니지만 우리의 목적은 지킬을 사용하는 것이지 배포판의 특징이나 루비 소프트웨어를 학습하는 것이 아님을 잊지 말기 바란다. RVM을 통해 루비를 설치하면 지킬이 루비를 버리지 않는 한 버전업에 따른 환경 변경의 부담을 덜 수 있다.

또 여러 버전의 루비를 설치하면 여러 버전의 지킬을 사용할 수 있다. 그러나 특정 경우가 아니면 지킬 최신 버전과 그 버전이 요구하는 루비 버전을 사용하기 바란다.

### 기준

다음은 이 글에서 안내하는 리눅스에서의 지킬 설치의 기준이다.

 - 루비는 반드시 RVM으로 설치
 - 싱글 유저 RVM 설치
 - 우분투 데스크톱(12.04 부터 14.10 까지), 리눅스 민트 데스크톱(17) 기준
 - 배포판 설치 후 업데이트는 하지 않음
 - 이미 패키지 관리자로 루비를 설치하고 지킬 사용하는 경우도 동일
 - 지킬 버전 1, 2, 3 모두 동일

위에 없는 리눅스 배포판도 대부분 같다고 생각하면 된다. 바로 알아보자.

### 요약

먼저 이후에 안내하는 내용을 간단하게 요약하면 다음과 같다. 긴 설명이 싫다면 아래만 진행하면 된다.

아래 명령 라인을 하나씩 입력하여 실행 및 진행 후 터미널 설정만 아래에 나오는 내용을 참고하여 변경하면 된다. 4번째 명령 라인에서 `vjinn`은 자신의 정보로 변경하면 된다.

```bash
$ sudo apt-get install curl
$ gpg --keyserver hkp://keys.gnupg.net --recv-keys D39DC0E3
$ \curl -sSL https://get.rvm.io | bash -s stable
$ source /home/vjinn/.rvm/scripts/rvm
$ rvm install ruby-2.2.0
$ sudo apt-get install nodejs
$ gem install jekyll
```

다음의 링크는 우분투와 리눅스 민트 데스크탑에서 지킬 설치 영상이다. 한 번 참고하면 된다.

 - [How to Install Jekyll on Ubuntu and Linux Mint Desktop with RVM](http://youtu.be/lLLFAYoNHv4)

아래는 설명을 조금 더한 내용이다.

### 지킬이 요구하는 패키지 설치

터미널을 실행하고 아래의 명령을 그대로 입력하여 `curl`을 설치하자. RVM을 설치하기 위한 것이다. 설치 물음이 나오면 **Y**를 눌러 진행하면 된다. 이후의 과정도 같다.

```bash
$ sudo apt-get install curl
```

다음의 두 명령 라인의 내용은 [RVM](https://rvm.io/) 웹사이트에 접속하면 즉시 얻을 수 있다. 복사해서 사용하기 바란다. 이것만 하면 RVM 설치는 끝이다.

```bash
$ gpg --keyserver hkp://keys.gnupg.net --recv-keys D39DC0E3
$ \curl -sSL https://get.rvm.io | bash -s stable
```

다음 과정이 중요하다. 위의 명령으로 RVM 설치가 끝났다면 아래와 같은 메시지를 볼 수 있을 것이다.

```bash
Installing RVM to /home/vjinn/.rvm/
    Adding rvm PATH line to /home/vjinn/.profile /home/vjinn/.mkshrc /home/vjinn/.bashrc /home/vjinn/.zshrc.
    Adding rvm loading line to /home/vjinn/.profile /home/vjinn/.bash_profile /home/vjinn/.zlogin.
Installation of RVM in /home/vjinn/.rvm/ is almost complete:

  * To start using RVM you need to run `source /home/vjinn/.rvm/scripts/rvm`
    in all your open shell windows, in rare cases you need to reopen all shell windows.
```

위의 내용은 *'설치 잘 됐고요, 프로파일에 RVM 경로는 추가됐는데 RVM 사용하려면 터미널에 한 줄 명령을 넣어야 합니다.'* 라는 것이다. 그 한 줄 내용은 다음과 같다. 입력 및 실행해도 되지만 하지 말자.

```bash
$ source /home/vjinn/.rvm/scripts/rvm
```

위의 명령을 실행하면 터미널을 종료하기 전에는 루비 설치, 지킬 설치와 사용, 루비 버전 확인, 지킬 버전 확인 등 모든 것이 가능하지만, 터미널을 종료 후 재실행 하면 다시 입력해야 한다. 그렇지 않으면 아무것도 할 수가 없다.

RVM 설치 시 분명 경로가 추가됐다는 메시지가 있고, 확인하면 추가되어 있는데 재실행하면 추가한 경로의 파일을 읽지 않는다. 영구적인 방법은 터미널 설정을 변경하는 것이다. 이 글의 기준인 우분투와 리눅스 민트 데스크톱의 터미널 소프트웨어는 그놈 터미널(GNOME Terminal)이다. 이 소프트웨어의 설정을 변경해야 한다.

다음과 같이 터미널 설정을 변경하고 재실행하자. (설정에 따라 메뉴가 데스크톱 화면 상단에 나올 수 있다.)

 1. 터미널의 메뉴에서 `Edit - Profile Preferences - Title and Command 탭 - Run command as a login shell` 선택
 2. 터미널 종료 후 재실행

![그놈 터미널 설정]({{ site.il }}/gtset.gif)

설치 후 나오는 메시지를 실행하여 루비, 지킬을 설치하고 위의 터미널 설정을 변경해도 전혀 문제가 없다.

이제 루비를 설치하고 지킬을 설치하자. 루비는 글 작성일 기준 2.2.0 버전이 최신 안정 버전이며, 지킬 3.x 버전부터 루비 1.9.3 버전을 지원하지 않으며, 2.0과 2.2를 지원한다. 여기서는 2.2.0 버전을 설치한다.

다음의 명령을 실행하자.

```bash
$ rvm install ruby-2.2.0
```

설치 후 루비 버전을 확인하자.

```bash
$ ruby -v
ruby 2.2.0p0 (2014-12-25 revision 49005) [x86_64-linux]
```

다음으로 지킬 버전 2.x 부터 필요한 `nodejs`를 설치하자.

```bash
$ sudo apt-get install nodejs
```

### 지킬 설치 및 확인

바로 지킬을 설치하자. 지킬은 `gem` 패키지로 배포하는데 리눅스 배포판의 패키지 관리자로 루비를 설치하지 않았고, 싱글 모드로 RVM을 설치했으므로 `sudo`는 사용하지 않아도 된다.

```bash
$ gem install jekyll
```

*빠른 설치를 위해 아래와 같이 옵션을 주는 경우가 있다. 문서는 설치하지 않겠다는 것이다.*

```bash
$ gem install jekyll --no-rdoc --no-ri
```

설치가 끝나면 지킬 버전을 확인해 보자.

```bash
$ jekyll -v
```

### 사이트 생성, 변환 테스트 

아래의 명령으로 사이트를 생성하자.

```bash
$ jekyll new mysite
```

아래의 명령으로 생성한 사이트로 접근하고 사이트 변환하자. `jekyll serve` 명령 후 터미널에 나오는 **Server address: http://127.0.0.1:4000**에서 아이피 부분을 `Ctrl +` 클릭하여 웹브라우저에서 사이트를 확인하자. 문제가 없다면 리눅스에서 지킬 설치는 끝이다. 너무 간단하다.

```bash
$ cd mysite
$ jekyll serve
```

*localhost:4000과 127.0.0.1:4000에서 후자로 사이트를 확인하는 것이 유리할 때가 많다. 가령 코멘트 시스템 **Livefyre**를 사용하기 위해 코드를 삽입하고 웹브라우저에 확인할 때 나오지 않는 경우는 전자의 경우이다.*

리눅스 배포판의 패키지 관리자로 설치한 루비가 있다면 삭제하는 것이 좋다. 안해도 문제는 없다. 다음과 같이 하자.

```bash
$ sudo apt-get remove --purge ruby
```

지킬 버전 1.x에서 루비 2.x 버전을 사용하면 에러 메시지가 계속 나올 수 있다. 사용 시 발생하는 문제는 거의 없다. 거슬린다면 RVM으로 루비 1.9.3을 설치하고, 루비 사용 버전을 변경, 지킬 1.x 재설치*(설치라기 보다 변경한 루비 버전에 이 버전의 지킬을 사용하겠다는 정의로 생각하면 된다.)* 하면 된다. 하지만 1.x 버전의 지킬은 그만 쓰자.

반드시 RVM을 통한 루비와 지킬 설치로 지킬 버전업에 따라 변경되는 환경 구성의 부담을 덜기 바란다.  

### 지킬 특정 버전 설치, 삭제, 업데이트

지킬 **특정 버전을 사용**하고 싶다면 아래와 같은 옵션을 주면 된다. (예, 1.5.1)

```bash
$ gem install jekyll -v 1.5.1
```

**지킬 삭제**는 아래와 같다.

```bash
$ gem uninstall jekyll
```

**특정 버전 삭제**는 아래와 같다. (예, 1.5.1)

```bash
$ gem uninstall jekyll -v 1.5.1
```

다양한 지킬 버전이 설치되어 있을 때 **최신 버전 제외 모두 삭제**는 아래와 같다.

```bash
$ gem cleanup jekyll
```

**지킬 버전 업데이트**는 아래와 같다. `gem update`를 사용하는 것이 좋다.

```bash
$ gem update
or
$ gem update jekyll
```

**설치한 지킬 또는 `gem` 패키지 목록**은 다음의 명령으로 확인할 수 있다.

```bash
$ gem list
or
$ gem list jekyll
```

위의 내용들은 아래의 명령을 통해 도움을 얻을 수 있다.

```bash
$ gem help
```

지킬 버전을 한 눈에 보고 싶다면 아래 링크를 보자.

 - [All versions of jekyll](https://rubygems.org/gems/jekyll/versions)

---

## Mac OS X에 지킬 설치하기

맥에서 지킬을 사용하는 방법은 리눅스에서 구성하는 방법과 대부분 같다. **Command Line Tools**로 부르는 별도의 패키지 설치가 필요한 것뿐이다. 모든 설치는 터미널에서 끝난다. 지킬 사용만이 목적이라면 **Xcode** 설치는 필요 없다. 파일의 용량이 커서 지루한 시간을 맞이한다.

맥 사용자는 그 환경에 남달리 익숙하다는 기준에서 간단하게 안내해도 가볍게 구성할 것으로 생각한다. 아래는 **OS X Yosemite**에서 지킬 사용을 위한 설치의 과정이다. 터미널에서 다음의 명령 순서로 입력하고 실행하면 대부분 문제가 없다.

터미널 실행 후

```bash
$ xcode-select --install
$ \curl -sSL https://get.rvm.io | bash -s stable
$ source ~/.rvm/scripts/rvm
$ rvm install 2.2.0
$ gem install jekyll
```

위에서 2번째 라인은 [RVM](http://rvm.io) 웹사이트에서, 3번째 라인은 설치 과정에서 자신의 계정에 맞게 나오는 것을 복사하여 사용하면 된다.

다음의 동영상과 같이 보면 감 온다.

<div class="video">
<iframe width="420" height="315" src="https://www.youtube.com/embed/2j1Xt-azKss" frameborder="0" allowfullscreen></iframe>
</div>

위의 동영상은 테스트를 위해 전체 과정을 진행한 후에 리셋한 것이므로 나오지 않는데, 운영체제 처음 설치 후 RVM을 설치한다면 **경로 설정에 대한 물음**이 있을 수 있다. 주의하여 읽은 후 **'yes'** 입력 후 진행하면 된다. 또 **Homebrew** 관련한 내용도 설치 과정에서 나오는데, 지킬 사용이 목적이라면 세심하게 확인할 필요는 없다고 생각한다. RVM을 사용하면 된다.

OS X Yosemite에는 루비 2.0 버전이 이미 있지만, 지킬 3.x 버전은 루비 2.2 버전을 지원하므로 RVM으로 버전업 하는 것이 좋을 것이다.

맥이 주 운영체제라면 어느 환경 못지 않게 지킬 사용이 편할 것이다.

## 윈도즈에 지킬 설치와 사이트 생성

윈도즈에서 사용할 수 있는 지킬은 공식적으로 없다. 지킬 사용자가 윈도즈에서 사용할 수 있도록 만들어 놓은 것 (패키지) 또는 방법을 안내한 것만 있다. 아래의 지킬 공식 웹사이트와 번역 사이트 링크의 내용에 참조할 문서의 링크가 있다.  

 - [Jekyll on Windows](http://jekyllrb.com/docs/windows/#installation)
 - [윈도즈에서 지킬 사용하기 안내](http://jekyllrb-ko.github.io/docs/windows/#installation)

이 페이지에서는 @madhur의 **Portable Jekyll** 패키지를 사용하여 안내한다. 이 패키지를 사용한다면 만든 사람에게 감사의 표시(Star)도 하자.

### Portable Jekyll

한 번 더 이야기하면 윈도즈를 위한 지킬은 없으며, 특정 사용자가 패키지로 만든 것을 지금 설명하는 것임을 기억하자. 아래의 내용은 그 패키지 사용 설명이다.

 1. [다운로드](https://github.com/madhur/PortableJekyll) : 왼쪽 '다운로드'를 클릭하여 깃허브 페이지에 접속하면 오른쪽의 **Download ZIP** 버튼을 클릭하고, 운영체제와 다른 파티션에 이 파일을 저장(권장 사항)한 후 압축을 푼다. *(이것으로 설치는 끝이다.)*
 2. 윈도즈 커맨드(이하 CMD)를 실행한다.
 3. 압축해제 디렉터리에서 **setpath.cmd** 파일을 윈도즈 커맨더 화면으로 드래그 후 실행한다. *(기억하자. 윈도즈에서 지킬을 사용할 때 제일 먼저 할 일이 이것이다.)*
 4. CMD에 `jekyll -v`를 입력하여 버전을 확인해 보자.
 5. CMD 유틸을 종료하면 패키지를 종료하는 것과 같다. 그러므로 지킬도 안된다.
 6. 지킬을 다시 사용할 때는 2,3번 과정을 진행한다.

이 패키지에는 루비 2.x 버전이 포함되어 있어 **지킬 버전 3.x 사용이 가능**하며, 업데이트가 가능하다. 위의 2, 3번을 시행한 후 CMD에 `gem update`만 입력하면 된다.

```bash
> gem update
```

문제가 없다면 지킬과 의존 패키지들이 모두 업데이트되었을 것이다.

윈도즈에서 지킬을 사용할 때의 큰 이슈는 문서의 인코딩 문제이다. 그러나 1.x 버전에서 이 패키지를 사용했을 때는 문제가 있어 별도 정의를 하여 처리했으나, 글 작성일 기준으로 이 패키지 사용에 인코딩 문제는 없었다. 이유는 궁금해하지 말자. 문제가 발생하면 방법을 찾으면 된다. 어쨌든 즐거운 일이다.

윈도즈의 지킬이라고 하지만 지킬 사용의 기본 방식은 리눅스에서와 같다. `jekyll serve`, `jekyll new` 명령도 같다. 윈도즈 CMD 명령이 조금 다르지만 신경 쓸 일은 아니다. 윈도즈 시스템 사용이 어색한 사람은 없으므로 CMD에서 꼭 필요한 명령 외 사이트 디렉터리 생성, 포스팅, 설정, 편집 등은 GUI 환경에서 진행하면 된다. 윈도즈에서의 지킬 사용이 가장 친근할 수 있다.

다음의 동영상은 이 페이지 내용의 일부이다. 참고하기 바란다.

<div class="video">
<iframe src="//www.youtube.com/embed/T_ZhqkshtKk" frameborder="0" allowfullscreen></iframe>
</div>
