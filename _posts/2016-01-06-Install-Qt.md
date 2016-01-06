---                               
layout: post
title: "Qt 설치하기" 
author: <a href="mailto:westporch@gmail.com">Westporch</a>
---


# 1. Qt 다운로드

https://download.qt.io/official_releases/qt 에서 최신 Qt를 다운받습니다.

{% highlight sh %}
westporch@localhost:~/Downloads$ wget https://download.qt.io/official_releases/qt/5.5/5.5.1/qt-opensource-linux-x86-5.5.1.run
{% endhighlight %}


# 2. Qt 설치

Qt 설치는 root가 아닌 일반 사용자 권한으로 해야합니다.

아래와 같이 파일의 허가권을 변경합니다.

{% highlight sh %}
westporch@localhost:~/Downloads$ chmod u+x qt-opensource-linux-x86-5.5.1.bin
{% endhighlight %}

.bin 파일을 실행하면 설치가 진행됩니다.

{% highlight sh %}
westporch@localhost:~/Downloads$ ./qt-opensource-linux-x86-5.5.1.bin
{% endhighlight %}
