---
layout: post
title: VMware Player에 Ubuntu 설치하기
category: environment
---

윈도즈에 설치한 VMware Player에 우분투를 설치해 보자. 설치의 목적은 지킬 사용을 위한 환경 구성이지만, 우분투를 경험하고 싶을 때도 같은 방법으로 설치하면 된다. 또 리눅스 배포판에 대부분 공통된 설치와 설정이다.

설치 흐름을 아래 텍스트로 간단히 나열해 본다. 동영상과 함께 참고하면 어려운 것은 하나도 없다. 이 글에서는 우분투 14.04 데스크톱 64비트 버전을 설치한다. 배경지식이 있다면 이 페이지를 빨리 떠나는 것이 좋다.

## 윈도즈의 VMware Player에 우분투 설치하기

1. [우부투 배포판 다운로드](http://www.ubuntu.com/download/desktop) 및 저장 위치 확인
2. VMware Player 실행
3. Create New Virtual Machine 선택
4. Installer disc Image file (iso) 항목에 다운로드한 배포판 파일 추가
5. Personalize Linux
 - Full Name : 이름 입력
 - **User Name : 아이디 입력 (사용자 계정, 로그인 ID)**
 - Password : 암호 입력
6. Virtual Machine Name : 영문으로 구분하기 쉬운 이름 입력 (예, Ubuntu 64Bit Desktop)
7. **Location : 생성할 가상 운영체제 파일 저장 위치 선택**
8. Specify Disk Capacity
 - Maximum disk size : 기본 값 (원하는 크기 지정 가능)
 - Store virtual diks as a single file, Split virtual disk into multiple files : 하드디스크 파일 시스템이 NTFS일 경우 전자(Single), FAT32일 경우 후자(Multiple)를 선택한다고 일반적으로 알려져 있으나 어떤 것을 선택해도 무관
9. 설치 시작 및 완료
10. Restart 또는 Shutdown

7번의 가상 파일 저장 위치를 호스트 운영체제*(여기서는 윈도즈)*가 설치된 파티션이 아닌 별도의 파티션에 디렉터리(6번의 가상 머신 이름으로)를 만들어 저장하는 것을 권장한다. 생성한 가상 파일만 있으면 호스트 운영체제를 새롭게 설치해도 그대로 다시 사용할 수 있으며 데이터도 그대로 유지된다.

위의 내용과 동영상은 지킬 사용의 목적이 우선이므로 다른 설정을 안내하지 않았으나 설치가 끝난 후나 가상 머신을 사용하면서도 추가 설정이 가능하며 재시작 시 적용된다. 가상 머신에 적용할 CPU (코어 수), 메모리 크기는 직접 설정하기 바라며 아래의 동영상도 확인하면 도움이 된다.

<div class="video">
<iframe src="//www.youtube.com/embed/wKezpLoGFh4" frameborder="0" allowfullscreen></iframe>
</div>
