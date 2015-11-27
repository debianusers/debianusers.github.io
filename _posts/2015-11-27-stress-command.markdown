---                               
layout: post
title: "stress 명령어" 
author: <a href="mailto:westporch@gmail.com">Westporch</a>
---

stress 명령어를 통해 시스템에 과부하를 줄 수 있습니다. 이를 통해 안정성을 테스트해볼 수 있습니다.

1.stress 설치
--------------------------

{% highlight sh %}
root@localhost:/home/westporch# apt-get install stress
패키지 목록을 읽는 중입니다... 완료
의존성 트리를 만드는 중입니다       
상태 정보를 읽는 중입니다... 완료
다음 새 패키지를 설치할 것입니다:
  stress
0개 업그레이드, 1개 새로 설치, 0개 제거 및 84개 업그레이드 안 함.
20.4 k바이트 아카이브를 받아야 합니다.
이 작업 후 94.2 k바이트의 디스크 공간을 더 사용하게 됩니다.
받기:1 http://ftp.daum.net/debian/ jessie/main stress i386 1.0.1-1 [20.4 kB]
내려받기 20.4 k바이트, 소요시간 10초 (1,944 바이트/초)
Selecting previously unselected package stress.
(데이터베이스 읽는중 ...현재 133789개의 파일과 디렉터리가 설치되어 있습니다.)
Preparing to unpack .../stress_1.0.1-1_i386.deb ...
Unpacking stress (1.0.1-1) ...
Processing triggers for install-info (5.2.0.dfsg.1-6) ...
Processing triggers for man-db (2.7.0.2-5) ...
stress (1.0.1-1) 설정하는 중입니다 ...
root@localhost:/home/westporch#
{% endhighlight %}

2.메모리 stress
---------------

{% highlight ruby %}
root@localhost:/home/westporch# stress --vm 3 --vm-bytes 1024M
stress: info: [3415] dispatching hogs: 0 cpu, 0 io, 3 vm, 0 hdd

{% endhighlight %}

|옵션|설명|
|:--:|:--:|
|--vm '할당할 개수' (--vm과 -m은 같은 의미)|지정한 개수만큼 자식 프로세스를 생성합니다.|
|--vm-bytes '할당할 크기'|할당할 메모리 크기는 --vm-bytes 옵션으로 결정합니다. 이 옵션을 지정하지 않으면 기본값은 256MB입니다.|


2-(1).메모리 stress 작동 여부 확인
-----------------------------

**ps aux | grep stress**

_1050888_KB / 1024= 1026MB

PID 3416, 3417, 3418 (--vm 3)이 1026MB (--vm-bytes 1024M)만큼의 메모리를 사용하고 있습니다.

{% highlight ruby %}
root@localhost:/home/westporch# ps aux | grep stress
root      2873  0.0  0.0   9532  6896 pts/3    S+   09:32   0:02 vi 2015-11-27-stress-command.markdown
root      3415  0.0  0.0   2308   676 pts/4    S+   11:16   0:00 stress --vm 3 --vm-bytes 1024M
root      3416 98.5 11.0 1050888 882712 pts/4  R+   11:16   0:41 stress --vm 3 --vm-bytes 1024M
root      3417 98.5  5.9 1050888 475624 pts/4  R+   11:16   0:41 stress --vm 3 --vm-bytes 1024M
root      3418 98.5  0.2 1050888 22864 pts/4   R+   11:16   0:41 stress --vm 3 --vm-bytes 1024M
root      3423  0.0  0.0   4368  2148 pts/2    S+   11:17   0:00 grep stress
root@localhost:/home/westporch# 
{% endhighlight %}

**pstree -p**

**stress --vm 3 --vm-bytes 1024M** 명령으로 프로세스 3416, 3417, 3418이 생성되었음을 확인할 수 있습니다.

{% highlight sh %}
root@localhost:/home/westporch# pstree -p
systemd(1)─┬─ModemManager(618)─┬─{gdbus}(728)
           │                   └─{gmain}(640)
           ├─NetworkManager(624)─┬─{NetworkManager}(719)
           │                     ├─{gdbus}(741)
           │                     └─{gmain}(732)
             ..생략..
           │               ├─bash(2955)───su(3336)───bash(3337)───stress(3415)─┬─stress(3416)
           │               │                                                   ├─stress(3417)
           │               │                                                   └─stress(3418)
           │               ├─{QInotifyFileSys}(2094)
           │               └─{QProcessManager}(2096)
			..생략..
{% endhighlight %}

**free -hm**

약 3.0GB의 메모리를 사용하고 있습니다.
{% highlight ruby %}
root@localhost:/home/westporch# free -hm
             total       used       free     shared    buffers     cached
Mem:          7.6G       2.7G       4.9G       316M        44M       875M
-/+ buffers/cache:       1.8G       5.8G
Swap:         669M         0B       669M
root@localhost:/home/westporch#
{% endhighlight %}
