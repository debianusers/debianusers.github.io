---                               
layout: post
title: "ssh - WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! 해결 방법" 
author: <a href="mailto:westporch@gmail.com">Westporch</a>
---

ssh 접속시 *WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!*가 발생할 때가 있습니다.

{% highlight sh %}
root@localhost:/home/westporch# ssh 10.0.11.244
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
ae:1a:ff:f7:a3:be:4c:70:dd:07:e3:48:a4:7f:c2:3c.
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /root/.ssh/known_hosts:3
  remove with: ssh-keygen -f "/root/.ssh/known_hosts" -R 10.0.11.244
RSA host key for 10.0.11.244 has changed and you have requested strict checking.
Host key verification failed.
root@localhost:/home/westporch#
{% endhighlight %}

1.해결 방법
------------
*ssh-keygen -R '접속할 주소'*를 입력합니다.

{% highlight sh %}
root@localhost:/home/westporch# ssh-keygen -R 10.0.11.244
# Host 10.0.11.244 found: line 3 type ECDSA
/root/.ssh/known_hosts updated.
Original contents retained as /root/.ssh/known_hosts.old
root@localhost:/home/westporch#
{% endhighlight %}

*ssh '접속할 주소'*를 입력해서 다시 ssh 접속을 시도합니다. 이때 yes를 입력합니다.

아래 화면과 같이 다시 접속이 가능해졌습니다.
{% highlight sh %}
root@localhost:/home/westporch# ssh 10.0.11.244
The authenticity of host '10.0.11.244 (10.0.11.244)' can't be established.
RSA key fingerprint is ae:1a:ff:f7:a3:be:4c:70:dd:07:e3:48:a4:7f:c2:3c.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '10.0.11.244' (RSA) to the list of known hosts.
root@10.0.11.244's password: 
Last login: Wed Nov 25 15:22:42 2015 from 10.0.11.185
[root@Hello ~]#
{% endhighlight %}
