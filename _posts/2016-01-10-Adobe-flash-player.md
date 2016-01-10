---                               
layout: post
title: "Chromium에서 Adobe flash player 설치하기" 
author: <a href="mailto:westporch@gmail.com">Westporch</a>
---


# 1. Flash plugin 다운

[ttp://ftp.uk.debian.org/debian/pool/contrib/p/pepperflashplugin-nonfree/](http://ftp.uk.debian.org/debian/pool/contrib/p/pepperflashplugin-nonfree/) 에서 pepperflashplugin-nonfree(deb 파일) 최신 버전을 다운 받습니다.

{% highlight sh %}
root@localhost:/home/westporch/Downloads# http://ftp.uk.debian.org/debian/pool/contrib/p/pepperflashplugin-nonfree/pepperflashplugin-nonfree_1.8.2_i386.deb
{% endhighlight %}

# 2. Flash pluin 설치

*dpkg -i pepperflashplugin-nonfree_1.8.2_i386.deb* 명령으로 플러그인을 설치합니다.

{% highlight sh %}
root@localhost:/home/westporch/Downloads# ls
flashplugin-nonfree_3.6.1_i386.deb
root@localhost:/home/westporch/Downloads# dpkg -i pepperflashplugin-nonfree_1.8.2_i386.deb 
Selecting previously unselected package pepperflashplugin-nonfree.
(데이터베이스 읽는중 ...현재 133858개의 파일과 디렉터리가 설치되어 있습니다.)
Preparing to unpack pepperflashplugin-nonfree_1.8.2_i386.deb ...
Unpacking pepperflashplugin-nonfree (1.8.2) ...
pepperflashplugin-nonfree (1.8.2) 설정하는 중입니다 ...
--2016-01-10 15:23:52--  http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_47.0.2526.106-1_i386.deb
Resolving dl.google.com (dl.google.com)... 216.58.221.14, 2404:6800:4004:814::200e
Connecting to dl.google.com (dl.google.com)|216.58.221.14|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 46749162 (45M) [application/x-debian-package]
Saving to: ‘/tmp/pepperflashplugin-nonfree.MjuKoVJfe5/google-chrome-stable_47.0.2526.106-1_i386.deb’

     0K .......... .......... .......... .......... ..........  0%  340K 2m14s
    50K .......... .......... .......... .......... ..........  0%  691K 1m40s
   100K .......... .......... .......... .......... ..........  0% 1.04M 81s
   150K .......... .......... .......... .......... ..........  0% 4.71M 63s
   200K .......... .......... .......... .......... ..........  0% 2.05M 55s
   250K .......... .......... .......... .......... ..........  0% 1.15M 52s
   300K .......... .......... .......... .......... ..........  0% 4.79M 46s
   350K .......... .......... .......... .......... ..........  0% 5.75M 41s
   400K .......... .......... .......... .......... ..........  0% 3.68M 38s
   450K .......... .......... .......... .......... ..........  1% 6.62M 35s
   500K .......... .......... .......... .......... ..........  1% 7.05M 32s
   550K .......... .......... .......... .......... ..........  1% 1.36M 32s
   600K .......... .......... .......... .......... ..........  1% 5.68M 30s
   650K .......... .......... .......... .......... ..........  1% 5.09M 28s
   700K .......... .......... .......... .......... ..........  1% 8.32M 27s
   750K .......... .......... .......... .......... ..........  1% 3.84M 26s
   800K .......... .......... .......... .......... ..........  1% 8.94M 25s
   850K .......... .......... .......... .......... ..........  1% 9.20M 24s
   900K .......... .......... .......... .......... ..........  2% 7.64M 23s
   950K .......... .......... .......... .......... ..........  2% 4.37M 22s
(...생략...)
2016-01-10 15:24:00 (5.44 MB/s) - ‘/tmp/pepperflashplugin-nonfree.MjuKoVJfe5/google-chrome-stable_449162]

root@localhost:/home/westporch/Downloads#
{% endhighlight %}

# 3. Flash plugin 설치 확인

실행 중인 Chromium을 모두 종료한 뒤에 Chromium을 재시작합니다.

주소 창에 [chrome://plugins](chrome://plugins)를 입력합니다.

plugins 항목에 *Adobe Flash Player*가 보이면 플러그인이 제대로 설치된 것입니다.
