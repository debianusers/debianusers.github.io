---                               
layout: post
title: "ssh - timed out waiting for input: auto-logout 문제 해결하기" 
author: <a href="mailto:westporch@gmail.com">Westporch</a>
---


# 1. TMOUT 쉘 변수 확인

TMOUT 쉘 변수에 자동 로그아웃 시간이 설정되어 있습니다.

프롬프트에 _echo $TMOUT_ 명령으로 언제 로그아웃이 되는지 확인합니다.

{% highlight ruby %}
[root@localhost ssh]# echo $TMOUT
300
[root@localhost ssh]# 
{% endhighlight %}

300은 5분(300 초)을 의미합니다. 

{% highlight ruby %}

{% endhighlight %}

# 2. TMOUT 비활성화

~/.bash_profile에 **TMOUT=**을 기록한 뒤 **source ~/.bashrc** 명령을 입력합니다.

_echo $TMOUT_ 명령으로 _$TMOUT_의 값을 확인하면 값이 지정되지 않았습니다.

이제 자동으로 로그아웃되지 않고 접속을 유지할 수 있습니다.

{% highlight ruby %}
[root@SNIPER ssh]# echo $TMOUT

[root@SNIPER ssh]# 
{% endhighlight %}
