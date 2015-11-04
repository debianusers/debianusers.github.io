--- 
layout: post
title: tree 명령어
author: Westporch
email: westporch@gmail.com
---

1.설치
-------

***tree***를 프롬프트에 입력해서 ***tree*** 명령어가 존재하는지 확인합니다.

***tree*** 명령어가 존재하지 않으니 ***tree***를 설치해야합니다.
{% highlight bash %}
root@localhost:/home/westporch# tree
bash: tree: command not found
root@localhost:/home/westporch#
{% endhighlight %}

***apt-get install tree*** 명령어로 설치합니다. 
{% highlight bash %}
root@localhost:/home/westporch# apt-get install tree
패키지 목록을 읽는 중입니다... 완료
의존성 트리를 만드는 중입니다       
상태 정보를 읽는 중입니다... 완료
다음 새 패키지를 설치할 것입니다:
  tree
0개 업그레이드, 1개 새로 설치, 0개 제거 및 84개 업그레이드 안 함.
47.9 k바이트 아카이브를 받아야 합니다.
이 작업 후 137 k바이트의 디스크 공간을 더 사용하게 됩니다.
받기:1 http://ftp.daum.net/debian/ jessie/main tree i386 1.7.0-3 [47.9 kB]
내려받기 47.9 k바이트, 소요시간 10초 (4,547 바이트/초)
Selecting previously unselected package tree.
(데이터베이스 읽는중 ...현재 133486개의 파일과 디렉터리가 설치되어 있습니다.)
Preparing to unpack .../archives/tree_1.7.0-3_i386.deb ...
Unpacking tree (1.7.0-3) ...
Processing triggers for man-db (2.7.0.2-5) ...
tree (1.7.0-3) 설정하는 중입니다 ...
root@localhost:/home/westporch# 
{% endhighlight %}

2.tree 명령어 사용
------------------

***tree*** 명령어만 입력하면 현재 디렉토리의 tree를 확인합니다.
{% highlight bash %}
root@localhost:/home/westporch/R# tree
.
├── graph.R
├── sample
│   ├── Rplots.pdf
│   ├── graph.R
│   ├── plot.png
│   ├── scan.txt
│   ├── test.R
│   ├── test.png
│   └── test2.R
└── values.txt

1 directory, 9 files
root@localhost:/home/westporch/R#
{% endhighlight %}

***tree '조회할 디렉토리 경로'***를 입력하면 특정 디렉토리의 tree를 조회합니다.
{% highlight bash %}
root@localhost:/home/westporch# tree /tmp
/tmp
├── akonadi-westporch.E1i1Yk
│   ├── akonadiserver.socket
│   └── mysql.socket
├── kde-westporch
├── ksocket-westporch
│   ├── KSMserver__0
│   ├── kdeinit4__0
│   └── klauncherMT1010.slave-socket
├── pulse-PKdhtXMmr18n
├── ssh-QbYOKm4jXa73
│   └── agent.849
└── systemd-private-714c213b6f494bcbbd9daec6af73423b-rtkit-daemon.service-YKMYkF
    └── tmp

7 directories, 6 files
root@localhost:/home/westporch#
{% endhighlight %}
