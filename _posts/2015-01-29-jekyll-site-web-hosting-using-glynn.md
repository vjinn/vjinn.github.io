---
layout: post
title: Glynn으로 일반 웹호스팅에 지킬 사이트 업로드 하기
category: tip
---

일반 웹호스팅 서비스에 지킬 사이트를 게시할 때는 `_site` 디렉터리의 파일을 FTP 방식으로 업로드하면 된다. 물론 깃허브 페이지에 호스팅을 원한다면 사이트 소스 푸쉬만으로도 가능하며, 특정 플러그인 사용에 의해 반려 된다면 `_site` 디렉터리의 파일만 푸쉬하면 호스팅이 가능하다.

지킬 사이트를 호스팅하는 방법에 대한 내용은 다음의 링크에 잘 나와 있다.

 - [Deployment methods]({{ site.jl }}/docs/deployment-methods/)
 - [지킬 사이트 게시 방법]({{ site.jkl }}/docs/deployment-methods/)

그 중에 터미널에서 FTP 방식의 업로드를 통한 지킬 사이트 게시 방법에 대해 간단히 알아보자.

## Glynn

[Glynn]({{ site.gl }}/dmathieu/glynn), 지킬 사이트 게시를 위한 프로젝트라고 알려져 있다. 설치는 다음과 같다.

```bash
$ gem install glynn --source http://gemcutter.org
```

다음과 같은 정보가 있다고 가정하자.

 - ftp host : glynn.jekyllis.com
 - ftp dir(절대경로) : /home/glynn/www
 - ftp Passive : false
 - port : 21
 - ftp Username : glynn
 - ftp Password : 1234

위의 가상 정보로 Glynn을 사용한다면 `_config.yml` 파일에 다음의 내용을 추가하면 된다.

```yaml
ftp_host: 'glynn.jekyllis.com'
ftp_dir: '/home/glynn/www'
ftp_passive: false
ftp_port: 21        
ftp_username: 'glynn' 
ftp_password: '1234'
```
Port, Username, Password 정보는 설정에 추가하지 않아도 된다. 기본 포트를 사용하지 않는다면 추가하면 되고, Username, Password는 설정 파일에 없으면 실행 시 묻는다. 그 때 입력하면 된다.

실행은 터미널에서 간단하게 다음과 같다.

```bash
$ glynn
```

Glynn은 사이트 변환 명령(`jekyll build`)을 포함하며, 설정이 없다면 `_site` 디렉터리를 생성하고 파일을 업로드한다. 만약 생성 디렉터리를 `_www`로 `_config.yml` 파일에 정의했다면 그 설정에 따라 `_www` 디렉터리를 생성한다.
