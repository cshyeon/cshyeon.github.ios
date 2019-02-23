---
layout: post
title: "Jekyll로 만드는 블로그 - 튜토리얼"
categories: jekyll tutorial
---

블로그나 웹사이트를 만드는 방법이 여러가지 존재한다. 블로그 서비스를 이용하거나 직접 웹사이트를 만드는 방법 등이다. 최근에 jekyll을 사용해서 만들어진 사이트들을 많이 접하게 되면서 `지킬`에 대해서 궁금증이 생겼고 결국 jekyll을 사용하여 개발 관련 블로그를 만들어 운영해보기로 했다.

### 이 포스트는 Jekyll의 기본적인 사용법을 소개하고 있습니다.

Jekyll은 블로그 서비스 보단 좀더 자유로우면서 접근하기 까다롭고, 직접 웹사이트를 만드는 방법보다는 쉽다. 또한 github 페이지를 활용하여 쉽게 jekyll로 만든 페이지를 배포할수 있다.

*Jekyll 공식페이지 참조*
> Jekyll 은 GitHub Pages 의 내부 엔진이기 때문에, 당신의 프로젝트에 있는 Jekyll 페이지/블로그/웹사이트를 GitHub 서버에 무료로 호스팅 할 수 있습니다.

`지킬`을 사용하기 위해서 먼저 [ruby 사이트]{:target="_blank"}에서 자신의 운영체재에 맞는 `ruby`를 설치해야한다. 다운로드 페이지에서 `Ruby+Devkit`패키지를 다운받아 설치한다.

Ruby를 설치했다면 터미널 shell에서 루비가 제대로 설치됐는지 확인해 볼 수 있다.
```bash
ruby -v
# ruby 2.5.3p105 (2018-10-18 revision 65156) [x64-mingw32]
```

`gem`은 Ruby의 패키지 매니저다. gem을 사용하여 Jekyll과 bundler를 설치한다.
```bash
gem install jekyll bundler
```

jeykyll과 bundler가 제대로 설치됐는지 확인한다.
```bash
jeykyll -v
#jekyll 3.8.5
bundler -v
#Bundler version 2.0.1
```

jekyll을 사용하기 위한 준비가 끝났다. 이제 jekyll 프로젝트를 생성해보자
```bash
# jekyll-blog 디렉토리에 프로젝트를 생성한다.
jekyll new jekyll-blog
```

이제 default 웹사이트가 생성됐으므로 실행하여 확인해 보자.
```bash
cd jekyll-blog
bundle exec jekyll server
# ...
# Server address: http://127.0.0.1:4000
# ...
```

콘솔에 출력된 Server address로 접속하여 잘 나오는지 확인한다.

[ruby 사이트]: https://www.ruby-lang.org/ko/