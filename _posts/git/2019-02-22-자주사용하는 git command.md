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

#### 브랜치

- 모든 저장소의 브랜치 보기
{% highlight bash %}
git branch -a
{% endhighlight %}

- 원격 저장소의 브랜치만 보기
{% highlight bash %}
git branch -r
{% endhighlight %}

- 로컬 저장소 브랜치 삭제하기
{% highlight bash %}
git branch -d <branchname>
{% endhighlight %}

- 로컬 저장소 브랜치 삭제후 원격 저장소 브랜치 삭제 반영하기
{% highlight bash %}
git push origin :<로컬에서 삭제한 branchname>
{% endhighlight %}

- 원격 저장소의 브랜치 로컬에 가져와 적용하기
{% highlight bash %}
git checkout -t origin/<branchname>
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
