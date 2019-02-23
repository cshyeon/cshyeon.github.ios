---
layout: post
title: "자주쓰는 git 명령어"
slug: "using-git-command-frequently"
date: 2019-02-22 14:26:28 +0900
categories: jekyll update
---

git에서 자주 사용하는 명령어들을 정리해 보았다.

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
