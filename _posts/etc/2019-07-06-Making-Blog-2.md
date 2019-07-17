---
sidebar:
    nav: "category"
title: "깃허브(Github) 블로그 만들기 #2"
excerpt: "블로그 생성하고 테마 적용하기"
categories:
    - ETC
permalink: /categories/etc/making-blog-2
tags: [jekyll, github, blog]
toc: true
toc_sticky: true
comments: true
share: true
last_modified_at: 2019-07-06T18:00:00-10:00
---

<br>

[깃허브 블로그 만들기 #1](/categories/etc/making-blog-1)<br>
**[깃허브 블로그 만들기 #2](/categories/etc/making-blog-2)**<br>
[깃허브 블로그 만들기 #3](/categories/etc/making-blog-3)

<br>
깃허브 블로그 만들기 두 번째 포스팅입니다.

[지난 포스팅](/categories/etc/making-blog-1)에서 github 블로그 생성을 위한 사전 준비는 모두 마쳤습니다. 이제 설치된 jekyll을 이용해 블로그를 생성해야하는데 사실 생성 자체는 정말 별 거 없어요. 명령어 몇 줄이면 금방 생성이 됩니다. 그러나 이 포스팅을 보는 분들이라면 단지 블로그 생성만이 목적이 아니라 남들처럼 테마도 있고 애니메이션 효과도 있는 멋들어진 자신만의 블로그 생성이 목적이겠죠. 그래서 이번 포스팅에서는 블로그 생성 이후에 테마를 적용하는 과정까지 설명드리도록 하겠습니다.

## 1. 테마 다운로드
테마를 적용하는 방법에는 2가지 방법이 있습니다. 먼저, 적용하고 싶은 테마를 배포하고 있는 github에서 테마의 repository를 fork해서 내 github으로 옮겨온 후, 이름을 바꿔주는 방법이 있고, 적용하고 싶은 테마의 release 버전을 다운 받아 내 local repository에 옮긴 후, commit하는 방법이 있습니다. 저는 제가 사용한 두 번째 방법에 대해서 설명드리도록 하겠습니다.

[Minimal-mistakes release 페이지](https://https://github.com/mmistakes/minimal-mistakes/releases/tag/4.16.4)에서 Source code.zip을 받아줍시다.

![Source code](/assets/images/etc/sourcecode.png)

다운을 다 받으셨으면 압축을 풀어주시고 내부 피알들을 local 저장소로 옮겨주세요. local 저장소는 지난 포스팅에서 git clone으로 생성한 폴더입니다. 저 같은 경우는 G 드라이브 하위에 username.github.io로 저장 돼어 있겠죠?

![G drive](/assets/images/etc/gdrive.png)

다옮겨주셨으면 username.github.io의 폴더 내부는 다음과 같을거에요.

![test.io](/assets/images/etc/testio.png)

그럼 이제 여기서 필요 없는 파일들을 삭제해줍시다. 필요없는 파일들의 목록은 다음과 같습니다.

- .editorconfig
- .gitattributes
- .github
- /docs
- /test
- CHANGELOG.md
- README.md
- screenshot-layouts.png
- screenshot.png

docs 폴더 같은 경우네는 minimal-mistakes 깃허브 블로그의 샘플 페이지에 대한 정보가 저장이 돼있어요. 참고하실 분들은 지우지 않으셔도 되지만, 그대로 놔두실 경우 본인의 블로그에 샘플 페이지가 표시될 수도 있으니 알아두시면 좋을 것 같아요.

## 2. local 서버에 테마 적용하기
다운 받은 테마를 적용하는 방법은 명령어 몇 줄만으로도 가능합니다. 먼저 cmd 창을 열어주세요. 그리고 본인의 블로그 폴더가 저장돼있는 디렉토리로 이동해주세요.


    > g:
    > cd username.github.io


그리고 다음 명령어를 입력하면 테마가 적용이 돼요.

    > bundler exec jekyll serve

그런데 이 때 ruby와 jekyll을 처음 사용하신 분들은 대부분 에러 메시지가 뜨실거에요. 이 때 발생하는 에러는 위의 명령어를 실행하는 데에 필요한 페키지가 없다는 뜻입니다. 그러니 당황하지 마시고 찬찬히 읽어보시면서 필요하다고 하는 페키지들을 설치해줍시다. 저는 이미 다 설치가 돼 있어서 에러 메시지가 발생하지 않기 때문에 이미지 첨부는 힘들 것 같아요. 페키지를 설치하는 명령어는 다음과 같이 입력해주시면 됩니다.

    > gem install 페키지이름

모든 페키지가 설치됐다면 다시 한번 지킬 서브 명령어를 입력해주세요. 이 명령어는 실제 블로그가 아닌 local 서버에서 테마를 적용하겠다는 명령어입니다.

    > bundler exec jekyll serve

그리고 인터넷 브라우저를 키셔서 주소창에 **127.0.0.1:4000**을 입력하시면, 다음과같이 테마가 적용된 사이트를 보실 수 있습니다.

![test site](/assets/images/etc/testsite.png)

## 3. 실제 블로그에 테마 적용하기
local 서버에서 테마가 적용된 것까지 확인을 했습니다. 그럼 이제 실제 블로그에 적용을 해봐야겠죠?

실제 블로그에 테마를 적용하는 것은 본인의 github repository에 local에 있는 파일들을 업로드하는 것으로 가능합니다. 블로그 폴더에서 마우스 우클릭을 한 뒤 git bash창을 열어줍시다. 그리고 다음과 같은 명령어들을 입력해주세요

    $ git add .
    $ git commit -m "my first blog"
    $ git push origin master

깃 명령어들에 대한 의미는 생략하도록 하겠습니다. 궁금하신 분들은 구글링을 부탁드릴게요. 그리고 이 때, git push 명령어를 입력할 때 로그인 창이 뜨는데, 본인의 github 아이디로 로그인을 해주시면 됩니다.

그리고 push까지 완료되었다면, 브라우저에서 **username.github.io**의 주소로 이동하시면 실제 블로그에도 테마가 잘 적용된 것을 알 수 있습니다. 

![test remote](/assets/images/etc/testremote.png)

혹시라도 테마가 적용이 안되셨다면 조금만 기다리시면 돼요. github에서 파일을 읽고 테마를 적용하기 까지 어느 정도의 시간이 걸릴 수 있어요. 그럼에도 불구하고 테마가 계속 적용되지 않으시는 분들은 본인의 github repository에서 setting을 클릭하시고 아래로 내려보면 github pages라는 부분이 있어요. 거기서 github pages가 활성화 되었는지 확인을 해줍시다.

![pages](/assets/images/etc/pages.png)

위와같이 **Your site is published at**이라는 문구가 있어야 정상입니다.

이번 포스팅에서는 블로그를 생성하고 기본적인 테마를 적용해보았습니다. 다음 포스팅에서는 블로그를 자신의 입맛에 맞게 커스터마이징하는 방법에 대해 포스팅하도록 하겠습니다.