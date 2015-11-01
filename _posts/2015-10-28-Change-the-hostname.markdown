---
layout: post
title: "systemd에서 호스트네임(hostname) 변경"
author: Westporch
---

1.systemd 버전 확인
-----------------
systemd에서 hostname을 변경하기 위해서 hostnamectl 명령어를 사용합니다.

hostnamectl은 systemd에 포함된 명령어입니다.
{% highlight ruby %}
root@localhost:/home/westporch# hostnamectl --version
systemd 215
+PAM +AUDIT +SELINUX +IMA +SYSVINIT +LIBCRYPTSETUP +GCRYPT +ACL +XZ -SECCOMP -APPARMOR
root@localhost:/home/westporch#
{% endhighlight %}

hostnamectl 명령어를 통해 현재 호스트네임을 확인할 수 있습니다.

***Static hostname: localhost***
{% highlight sh %}
root@localhost:/home/westporch# hostnamectl 
   Static hostname: localhost
         Icon name: computer-laptop
           Chassis: laptop
        Machine ID: 53291f6d86714db2862f4df466fe4e17
           Boot ID: 008872f2272441c78b13c8054fff0e7a
  Operating System: Debian GNU/Linux 8 (jessie)
            Kernel: Linux 3.16.0-4-686-pae
      Architecture: x86
root@localhost:/home/westporch# 
{% endhighlight %}

2.hostname 변경
--------------
***hostnamectl set-hostname --static '변경할_호스트네임'***으로 hostname을 변경합니다.
{% highlight ruby %}
root@localhost:/home/westporch# hostnamectl set-hostname --static HelloWorld
root@localhost:/home/westporch#
{% endhighlight %}

3.변경된 hostname 확인
---------------------
***hostnamectl*** 명령을 통해 hostname이 변경되었는지 확인합니다.

hostname이 HelloWorld로 변경되었습니다.
{% highlight ruby %}
root@localhost:/home/westporch# hostnamectl
   Static hostname: HelloWorld
         Icon name: computer-laptop
           Chassis: laptop
        Machine ID: 53291f6d86714db2862f4df466fe4e17
           Boot ID: 008872f2272441c78b13c8054fff0e7a
  Operating System: Debian GNU/Linux 8 (jessie)
            Kernel: Linux 3.16.0-4-686-pae
      Architecture: x86
root@localhost:/home/westporch# 
{% endhighlight %}

재부팅을 하면 로그인 프롬프트에도 hostname이 HelloWorld로 출력됩니다.
{% highlight ruby %}
root@localhost:/home/westporch# reboot
{% endhighlight %}

리부팅 후 프롬프트에서도 hostname이 HelloWorld로 변경되었습니다.
{% highlight ruby %}
root@HelloWorld:/home/westporch# 
{% endhighlight %}
