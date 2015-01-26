---
layout: post
title: 지킬 사용을 위한 최소한의 우분투 설정
category: environment
---

지킬 사용을 위해 우분투를 설치했다면 최소한의 설정만 해보자. 이 페이지의 내용은 [VMware Player에 Ubuntu 설치하기]({% post_url 2015-01-03-How-to-Install-Ubuntu-64-on-VMware-Player %}) 포스트를 따라 했을 때 나오는 결과를 기준으로 한 것이다. 하지만 자신이 원하는 환경과 방향으로 우분투를 설치한 경우도 적용 가능하다는 것과 이 페이지에서 지킬 사용을 위해 설정하는 우분투 내 소프트웨어 또한 선택사항임을 기억하자.

한글 사용을 위한 설정만 텍스트로 안내하며, 나머지 부가 설정은 사용자의 취향이므로 동영상에 포함하여 안내한다. 부가적인 설정도 배경지식이 없는 사용자라면 지킬 사용을 위해 따라 하는 것을 권장한다. 이 페이지의 내용이 마음에 들지 않는다면 **우분투 설치 후의 설정**에 대해 검색하여 적용해도 무방하다.

멋진 우분투 데스크톱 환경을 구성하는 일은 즐겁고, 관련 내용이 넘쳐나지만, 우분투 환경의 지킬에서 글쓰기보다 재미있는 일은 별로 없으니 나중에 그것도 적당히 구성하기 바란다.

----

## 지킬 사용을 위한 우분투 14.04 데스크톱 최소한의 설정

다음의 내용을 실제로 해보면 3분 정도 걸리는 작업이다. 텍스트로 늘어 놓아 많은 일처럼 보인다. 부담없이 진행하자.

### 키보드 입력 시스템 IBus를 사용하는 한/영 전환 설정

1. VMware Player 실행 및 우분투 부팅
2. 키보드 `Super` (윈도우 키) 누른 후 **System Settings** 입력 후 선택
3. **Language Support** 클릭
4. 팝업에서 **Install** 클릭 및 사용자 암호 입력 순으로 진행
5. 설치 완료 후 **Install/Remove Languages** 클릭
6. **Korean** 선택, Apply Changes 클릭
7. 로그아웃, 로그인
8. 키보드 `Super` (윈도우 키) 누른 후 **System Settings** 입력 후 선택
9. **Text Entry** 클릭
10. Input sources to use 아래 **+** 버튼 클릭
11. **Korean (Hangul)** 선택 후 Add 버튼으로 추가
12. Input sources to use 항목 Korean (Hangul)의 선택
13. 오른쪽 Switch to next source using 필드에 마우스 포커싱 (클릭)
14. 키보드 `Shift + Space` 누르기로 지정
15. Input sources to use 아래 **+** 버튼 클릭
16. **English (US)** 선택 후 Add 버튼으로 추가
17. 키보드 `Alt + F2` 누른 후 키보드 `Shift + Space`로 영어 입력 상태로 전환
18. **ibus-setup** 입력 후 실행
19. General 탭의 **Show property panel**에서 **Do not show** 선택
20. 키보드 `Super` (윈도우 키) 누른 후 입력란에 'gedit' (또는 'text editor') 입력 후 선택 실행
21. 임의의 텍스트 입력과 키보드 `Shift + Space` 사용으로 한/영 전환 확인
22. 활성화한 모든 창 종료 및 로그아웃, 로그인

위의 내용은 우분투에서 한글을 사용하고, 한/영 전환을 키보드 `Shift + Space`를 사용한다는 설정이다. 윈도즈에 설치한 VMware Player에 우분투를 설치하여 사용할 때 한/영 전환을 보통의 키로 설정하는 방법은 직접 검색하기 바란다.

랩톱(노트북) 또는 데스크톱 사용에 따라 다를 수 있으며, 하드디스크의 파티션을 구분하여 우분투를 설치한 경우 등에 따라서도 다를 가능성이 있다.

### 지킬 사용을 위한 기본 환경 설정

다음의 동영상은 이 페이지의 전체 설정 내용이다. 위의 키보드 입력 시스템 설정과 지킬 사용에 필요한 아주 기초적인 설정을 안내하고 있다. 한 번 더 말하면 '지킬 사용을 위한 최소한의 설정'을 전제한다.

<div class="video">
<iframe src="//www.youtube.com/embed/iDzgdx18MCk" frameborder="0" allowfullscreen></iframe>
</div>

*우분투 14.10 까지 'gedit' + 한글 입력기 'nabi' 조합에서 귀찮은 버그가 있다. 한글 입력 모드가 되면 흔히 '버벅거림', '멈춤' 현상이 지속해서 발생한다는 것을 참고하기 바란다. 만약 발생하지 않는다면 해결됐다고 생각하면 된다. 열반의 경지에 이르지 못한 사용자라면 피하기 바란다.*

우분투 설치 후의 설정에 관한 참고 링크를 몇 가지 남긴다.

 - [Ubuntu 14.04 LTS 내게 맞게 설정하기](http://bagjunggyu.blogspot.kr/2014/04/ubuntu-1404-lts.html)
 - [우분투 14.04, 한영 키로 한영 전환](http://egloos.zum.com/nemonein/v/5227053)
 - [우분투 14.04 LTS 설치 후 다듬기](http://egloos.zum.com/opensea/v/5814426)
 - [Ubuntu 12.04 LTS - 한/영, 한자 키 설정](http://morningt.tistory.com/12)
