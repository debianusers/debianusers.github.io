---                               
layout: post
title: "debianusers.github.io에 글 쓰는 방법" 
author: <a href="mailto:westporch@gmail.com">Westporch</a>
---

# 1. git

## 1-(1). git 설치

{% highlight sh %}
root@localhost:/home/westporch# apt-get install git
{% endhighlight %}

 ![alt text](https://lh3.googleusercontent.com/-76XQQsw34nQ/Vs0PHrJkHFI/AAAAAAAACdg/FDnybSEE5Os/s512-Ic42/1.%252520git%252520%2525EC%252584%2525A4%2525EC%2525B9%252598_2016_02_23_09_16_42_751.png "git을 설치하는 모습")  

## 1-(2). git 설정

 ![alt text](https://lh3.googleusercontent.com/-XQ_Aj7k8Uz8/Vs0PHOQV_lI/AAAAAAAACdc/BafNfQVCWhE/s512-Ic42/2.%252520git%252520%2525EC%252584%2525A4%2525EC%2525A0%252595_2016_02_23_10_41_44_242.png "git을 설정하는 모습")  

### 1). 사용자 정보 설정

{% highlight sh %}
root@localhost:/home/westporch# git config --global user.name "Westporch"
root@localhost:/home/westporch# git config --global user.email westporch@gmail.com
{% endhighlight %}

### 2). 기본 편집기 설정

{% highlight sh %}
root@localhost:/home/westporch# git config --global core.eidtor vim
{% endhighlight %}

### 3). git 설정 확인

{% highlight sh %}
root@localhost:/home/westporch# git config --list
user.name=Westporch
user.email=westporch@gmail.com
core.editor=vim
push.default=matching
root@localhost:/home/westporch# 
{% endhighlight %}


## 1-(3). git clone

![alt text](https://lh3.googleusercontent.com/-2Ta9SgYmKp4/Vs0PHFmy0hI/AAAAAAAACeA/4malpHI5nrA/s512-Ic42/3.%252520git%252520clone_2016_02_23_10_18_25_247.png "git clone을 하는 모습")

[git clone](http://gitref.org/creating/#clone) 명령어를 이용해서 [repository](https://github.com/debianusers/debianusers.github.io.git)를 로컬에 받아옵니다.

{% highlight sh %}
iroot@localhost:/home/westporch# git clone https://github.com/debianusers/debianusers.github.io.git
{% endhighlight %}


# 2. [마크다운](https://guides.github.com/features/mastering-markdown/) 문서 

마크다운 문법은 [stackedit.io](https://stackedit.io/)에서 연습할 수 있습니다.

## 2-(1). 마크다운 문서 생성

파일 이름은 **YYYY-MM-DD-Your-file-name.markdown** 형식을 유지해야 합니다.

마크다운 문서의 확장자는 markdown, md 둘 다 사용할 수 있습니다.

![alt text](https://lh3.googleusercontent.com/-fi2IKiTjaXk/Vs0PIBrKQfI/AAAAAAAACeA/AWrS-F-u3js/s512-Ic42/4-%2525281%252529.%252520%2525EB%2525AC%2525B8%2525EC%252584%25259C%252520%2525EC%252583%25259D%2525EC%252584%2525B1_2016_02_24_10_02_26_14.png "마크다운 문서를 생성하는 모습")

매번 마크다운 문서를 작성하기가 번거로워서 [문서 양식](https://raw.githubusercontent.com/debianusers/debianusers.github.io/master/_posts/2015-01-01-welcome-to-debianusers.markdown)을 만들었습니다. 파일 이름은 원하는 이름으로 바꾸면 됩니다.

{% highlight sh %}
root@localhost:/home/westporch/Git/debianusers.github.io/_posts# cp 2015-01-01-welcome-to-debianusers.markdown YYYY-MM-DD-Your-file-name.markdown
{% endhighlight %}

## 2-(2). 마크다운 문서 편집

![alt text](https://lh3.googleusercontent.com/-t86hm6mXutw/Vs0PJKDdkOI/AAAAAAAACeA/AYpt0jjU4Wc/s512-Ic42/4-%2525282%252529.%252520%2525EB%2525AC%2525B8%2525EC%252584%25259C%252520%2525EC%252597%252585%2525EB%2525A1%25259C%2525EB%252593%25259C_2016_02_24_10_03_40_61.png "마크다운 문서를 편집하는 모습")

[문서 양식](https://raw.githubusercontent.com/debianusers/debianusers.github.io/master/_posts/2015-01-01-welcome-to-debianusers.markdown)을 바탕으로 작업할 때 **title, author, 내용**을 바꾸면 됩니다.

마크다운 문서 작성이 끝나면 작성한 파일을 [repository](https://github.com/debianusers/debianusers.github.io.git)에 반영해야 합니다. 그러기 위해서 git add, git status, git commit 명령어를 사용합니다.

> **git add 파일명**

> **git status**

> **git commit -m "설명"**

> **git push**

[git 간편 안내서](https://rogerdudler.github.io/git-guide/index.ko.html)를 참고하시면 도움이 될 것입니다.


# 3. 작성한 문서 확인하기

![alt text](https://lh3.googleusercontent.com/--1bokIylpwY/Vs0PJPxtnNI/AAAAAAAACeA/09hW5n-R-mA/s512-Ic42/5.%252520%2525EC%252597%252585%2525EB%2525A1%25259C%2525EB%252593%25259C%2525EB%252590%25259C%252520%2525EB%2525AC%2525B8%2525EC%252584%25259C%252520%2525ED%252599%252595%2525EC%25259D%2525B8_2016_02_24_10_07_19_911.png "작성한 문서를 웹 브라우저에서 확인하는 모습")

브라우저를 새로 고침하면 작성한 문서를 확인할 수 있습니다.

변경 사항이 반영되는데 시간이 걸릴 때가 있습니다. 이럴 땐 잠시 후 다시 새로 고침을 하면 변경된 내용을 확인할 수 있습니다.
