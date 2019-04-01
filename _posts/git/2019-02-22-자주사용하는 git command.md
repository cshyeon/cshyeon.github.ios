---
layout: post
title: "자주쓰는 git 명령어"
slug: "using-git-command-frequently"
date: 2019-02-22 14:26:28 +0900
categories: git
---

git에서 자주 사용하는 명령어들을 정리해 보았다.

### 작업 명령어

- 원격 저장소의 내용 가져오기
{% highlight bash %}
git fetch
{% endhighlight %}

- 원격 저장소의 브랜치만 보기
{% highlight bash %}
git branch -r
{% endhighlight %}

- 모든 저장소의 브랜치 보기
{% highlight bash %}
git branch -a
{% endhighlight %}

- 원격 저장소에서 삭제된 브랜치 로컬에서 삭제
{% highlight bash %}
git fetch origin --prune
{% endhighlight %}

### 관리 명령어

- git config 확인하기
{% highlight bash %}
git config --list
{% endhighlight %}

- 단축 명령어(alias) 사용하기
{% highlight bash %}
git config --global alias.co checkout
# git co anotherBranch 

git config --global alias.br branch
{% endhighlight %}
