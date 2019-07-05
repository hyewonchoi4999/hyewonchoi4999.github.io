---
sidebar:
    nav: "category"
title: "깃허브(Github) 블로그 생성과 테마 적용 #1"
excerpt: "#Git #Ruby #Jekyll #설치"
categories:
    - ETC
permalink: /categories/etc/making-blog-1
tags: [jekyll, github, blog]
toc: true
toc_sticky: true
comments: true
share: true
last_modified_at: 2019-07-04T19:10:00-10:00
---

첫 포스팅은 정말 간단한 포스팅일 줄 알았는데, 어찌하다 보니 깃허브 블로그를 개설하는 과정이 첫 포스팅이 되었네요. 블로그를 시작하려고 마음먹은 후 이런 저런 플랫폼을 사용해보았지만, 적당히 마음에 드는 것이 없어 결국 Github 블로그를 선택했습니다. 웹 프로그래밍에은 거의 처음이라 익숙하지 않아서 그런지, 구글링을 해가며 지금의 블로그 포멧을 완성하는 데에 순수하게 이틀은 걸린 것 같아요. 그래서 이 후에 다른 분들이 조금이라도 더 쉽게 블로그를 생성할 수 있도록 Github 블로그를 개설하는 과정에 대해 포스팅을 남기도록 하겠습니다. (Github pages라 하는 사람도 있고 Github 블로그라고 하는 사람도 있는데, 사실 차이점은 잘 모르겠네요.)

이번 포스팅은 Windows10과 제 블로에 적용된 minimal-mistakes 테마를 기준으로 작성했습니다. 또한, 블로그를 생성하고 테마를 적용하는 결과에 초점을 맞추고자 하기때문에, 블로그 생성에 사용되는 git이 무엇이고 ruby가 무엇인지에 대한 설명은 생략하도록 할게요.

# 사전 준비
Github 블로그를 개설하기 앞서 사전적으로 준비해야 할 것들이 몇 가지가 있습니다. 일단, 아무 것도 준비되지 않고, 모르는 상태에서 출발한다고 가정하겠습니다.

- github 계정 생성
- github repository 개설
- Ruby 설치
- Jekyll 설치

저도 완벽하게 이해한 것은 아니지만 짤막하게 각 단계의 목적을 설명드리자면, 블로그는 remote 저장소(github)의 파일을 기반으로 수정 사항들이 적용되는데, jekyll을 이용하면 수정 사항들을 실제 블로그에 적용하기 전에 local 서버에서 확인할 수가 있어요. 이렇게 확인을 거친 후 git을 이용하여 local 저장소(내 컴퓨터)의 수정 사항들을 remote 저장소에 반영하고, 그 이후에 실제 블로그도 수정이 되는 것이죠.

## 1. Github repository 개설
저같은 경우는 github 계정은 이미 생성되어 있어서 github repository만 따로 개설을 했습니다.
Github 계정 생성은 [여기](https://github.com/)로 가셔서

![github_signup](/assets/images/etc/github_signup_1.png)

Username, Email 그리고 Password를 입력하시고 sign up버튼을 눌러주시면 됩니다.

계정생성이 완료된 후 로그인을 하시면 다음과 같은 화면이 뜨는데 start a project 버튼을 눌러줍시다.

![github_repos_1](/assets/images/etc/github_repos_1.png)

그리고 다음 화면에서 Repository name을 적어주셔야 하는데 **본인계정이름.github.io**로 생성을 하는게 좋아요(이유는 모름. 아마 중복 방지 때문이 아닐까...). 저는 이미 생성이 된 상태라 빨갛게 뜨지만 중복이 아닌 이상 별일 없이 완료될 거에요.

![github_repos_2](/assets/images/etc/github_repos_2.png)

Repostory 목적을 적고싶으신 분은 description란에 간단히 적어주셔도 되구, initialize this repository with a README는 **체크하지 마시길** 권장드립니다. 그리고 나서 Create repository 클릭하면 repository가 생성되었어요.

## 2. Git 설치와 repository clone
Github repository만 개설했다고 해서, local 저장소와 바로 연동이 되는 것은 아니에요. 생성된 repository를 local과 연동하기 위해서는 git을 설치해야 합니다. Git 설치는 [여기](https://git-scm.com/downloads)에서 할 수 있으며, 본인의 운영체제에 따라 선택을 해줍시다.

![git_install](/assets/images/etc/git_install.png)

설치 과정에서 어려운 점은 없으니 설치 가이드를 읽응시면서 따라하시면 될 것 같아요.

그럼 이제 Github의 remote 저장소와 내 컴퓨터의 저장소를 연동을 해주어야 합니다. 먼저, 블로그 내용을 저장하고 싶은 위치에 폴더를 만들어주세요. 저는 G드라이브 하위에 바로 저장을 했습니다.

그리고 폴더를 만드셨다면 그 폴더로 들어가서 우클릭 해보시면 Git bash here이라는 표시(?)가 있을거에요. 클릭해줍니다.

![git_bash_here](/assets/images/etc/git_bash_here.png)

git을 사용할 수 있는 bash가 생겼습니다..

![git_bash](/assets/images/etc/git_bash.png)

저는 g 드라이브 하위에 바로 저장할거라 했으니 bash 경로가 /g라고 되어있고, 다른 곳에 저장하려 하시는 분들은 경로가 다를 수도 있어요.

이제 여기에 이제 remote 저장소를 연동시켜야 하는데, **git clone repository_주소**라고 입력하셔야 해요. repository 주소는 본인 github repository로 가시면, 이렇게

![git_repos_address](/assets/images/etc/git_repos_address.png)

주소를 복사할 수가 있어요. 저는 이미 파일들이 있는 상태라 화면이 저렇게 뜨지만, 아무 것도 없으신 분들은 조금 다르게 뜨실건데 repository로 가시면 제일 상단부분에 저렇게 주소를 복사하실 수 있도록 되어있습니다.

그리고 복사한 주소를 bash에 붙여넣기 하시면 됩니다.

![git_clone_1](/assets/images/etc/git_clone_1.png)

![git_clone_2](/assets/images/etc/git_clone_2.png)

그러면 이제 local에 저장하는 파일들을 git으로 push하면 github 저장소에도 수정사항이 반영됩니다. Push라는 것은 google drive처럼 drive와 내 폴더를 동기화 시키는 건데, push라는 커멘드를 입력할 때에 모든 동기화가 일어난다고 생각하시면 됩니다.

## 2. Ruby 설치
Jekyll을 사용하기 앞서 ruby를 설치해주어야 합니다. [여기](https://rubyinstaller.org/downloads/)에서 인스톨러를 설치하시면 되는데, 오른쪽에 보시면 추천해주는 버전이 있어요. 저는 2.5.x with devkit 버전을 추천해주어서 그대로 다운받아 설치를 했습니다.

![ruby_install](/assets/images/etc/ruby_install.png)

다운받으신 후 인스톨러를 실행시키시면 설치가 진행되는데, 이 때 MSYS2를 같이 설치할거냐고 물어봅니다. 체크를 해줍니다. MSYS2를 같이 설치하면 MinGW 등 ruby를 구동하는 데에 필요한 toolchain이 같이 설치가 됩니다.

![ruby_install_2](/assets/images/etc/ruby_install_2.png)

설치가 완료되면 ruby cmd가 뜨고 ruby 설치 옵션이 뜰거에요. 

![ruby_install_3](/assets/images/etc/ruby_install_3.png)

1, 2, 3을 선택하라고 하는데 잘 모르시겠으면 그냥 엔터를 눌러줍시다. (저도 그냥 엔터 눌렀어요.)

![ruby_comp](/assets/images/etc/ruby_comp.png)

이렇게 뜨면 설치가 된거에요. (명령어는 ruby --version 입니다.)

## 3. Jekyll 설치
ruby 설치가 완료되었으면 이제 jekyll을 설치해야 되는데요, Jekyll은 일종의 페키지라고 생각하시면 될 것 같아요.

먼저 CMD를 켜주시는데 ruby cmd든 그냥 cmd든 상관없어요. 그리고 나서 cmd 창에 **gem install jekyll bundler** 라고 쳐주고 엔터를 눌러줍니다. 이 명령어는 jekyll과 bundler를 설치하라는 명령어이고 gem은 ruby라는 언어를 사용하겠다는 의미인 것 같습니다. 파이썬의 pip3 install tensorflow 이런 명령어와 비슷한 느낌이겠죠?

bundler는 jekyll이라는 페키지를 사용하기위해 가상환경을 생성해주는 또 다른 페키지(?)인 것 같은데 이 부분은 저도 아직 자세하게는 모르겠네요.

![jekyll_install](/assets/images/etc/jekyll_install.png)

여기까지 설치가 완료되었다면 사전 준비는 끝났습니다.

그럼 다음 포스팅에서 실제 블로그를 생성하고, 테마를 적용하는 법을 알아보도록 하겠습니다.