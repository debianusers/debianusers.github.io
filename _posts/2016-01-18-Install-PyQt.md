---                               
layout: post
title: "PyQt 설치하기" 
author: <a href="mailto:westporch@gmail.com">Westporch</a>
---

# 1. SIP 설치

[PyQt](https://riverbankcomputing.com/software/pyqt/intro)를 설치하기 전에 [SIP](https://riverbankcomputing.com/software/sip/download)를 먼저 설치해야합니다.

저는 [sip-4.17.tar.gz](http://sourceforge.net/projects/pyqt/files/sip/sip-4.17/sip-4.17.tar.gz)로 설치했습니다.

## 1-(1). python configure.py

**python configure.py**를 입력합니다.

{% highlight sh %}
root@localhost:/home/westporch/Downloads/sip-4.17# chmod 655 configure.py; python configure.py
This is SIP 4.17 for Python 2.7.9 on linux2.
The SIP code generator will be installed in /usr/bin.
The sip module will be installed in /usr/lib/python2.7/dist-packages.
The sip.h header file will be installed in /usr/include/python2.7.
The default directory to install .sip files in is /usr/share/sip.
Creating siplib/sip.h...
Creating siplib/siplib.c...
Creating siplib/siplib.sbf...
Creating sipconfig.py...
Creating top level Makefile...
Creating sip code generator Makefile...
Creating sip module Makefile...
{% endhighlight %}


## 1-(2). make

**make**를 실행합니다.

{% highlight sh %}
root@localhost:/home/westporch/Downloads/sip-4.17# make
make[1]: Entering directory '/home/westporch/Downloads/sip-4.17/sipgen'
gcc -c -pipe -O2 -w -DNDEBUG -I. -o main.o main.c
gcc -c -pipe -O2 -w -DNDEBUG -I. -o transform.o transform.c
gcc -c -pipe -O2 -w -DNDEBUG -I. -o gencode.o gencode.c
gcc -c -pipe -O2 -w -DNDEBUG -I. -o extracts.o extracts.c
gcc -c -pipe -O2 -w -DNDEBUG -I. -o export.o export.c
gcc -c -pipe -O2 -w -DNDEBUG -I. -o heap.o heap.c
gcc -c -pipe -O2 -w -DNDEBUG -I. -o parser.o parser.c
gcc -c -pipe -O2 -w -DNDEBUG -I. -o lexer.o lexer.c
g++  -o sip main.o transform.o gencode.o extracts.o export.o heap.o parser.o lexer.o 
make[1]: Leaving directory '/home/westporch/Downloads/sip-4.17/sipgen'
make[1]: Entering directory '/home/westporch/Downloads/sip-4.17/siplib'
gcc -c -pipe -fPIC -O2 -w -DNDEBUG -I. -I/usr/include/python2.7 -o siplib.o siplib.c
siplib.c:20:20: fatal error: Python.h: 그런 파일이나 디렉터리가 없습니다
 #include <Python.h>
            ^
compilation terminated.
Makefile:29: recipe for target 'siplib.o' failed
make[1]:  [siplib.o] Error 1
make[1]: Leaving directory '/home/westporch/Downloads/sip-4.17/siplib'
Makefile:3: recipe for target 'all' failed
make:  [all] Error 2
root@localhost:/home/westporch/Downloads/sip-4.17# 
{% endhighlight %}

만약 위와같은 메시지가 발생하면 *python-dev*를 설치합니다. (**apt-get install python-dev**)

{% highlight sh %}
root@localhost:/home/westporch/Downloads/sip-4.17# apt-get install python-dev
패키지 목록을 읽는 중입니다... 완료
의존성 트리를 만드는 중입니다       
상태 정보를 읽는 중입니다... 완료
다음 패키지를 더 설치할 것입니다:
  libexpat1-dev libpython-dev libpython2.7-dev python2.7-dev
다음 새 패키지를 설치할 것입니다:
  libexpat1-dev libpython-dev libpython2.7-dev python-dev python2.7-dev
0개 업그레이드, 5개 새로 설치, 0개 제거 및 0개 업그레이드 안 함.
2개를 완전히 설치하지 못했거나 지움.
18.8 M바이트 아카이브를 받아야 합니다.
이 작업 후 28.2 M바이트의 디스크 공간을 더 사용하게 됩니다.
계속 하시겠습니까? [Y/n] y
받기:1 http://ftp.daum.net/debian/ jessie/main libexpat1-dev i386 2.1.0-6+deb8u1 [126 kB]
받기:2 http://ftp.daum.net/debian/ jessie/main libpython2.7-dev i386 2.7.9-2 [18.4 MB]
받기:3 http://ftp.daum.net/debian/ jessie/main libpython-dev i386 2.7.9-1 [19.6 kB]
받기:4 http://ftp.daum.net/debian/ jessie/main python2.7-dev i386 2.7.9-2 [278 kB]
받기:5 http://ftp.daum.net/debian/ jessie/main python-dev i386 2.7.9-1 [1,178 B]
내려받기 18.8 M바이트, 소요시간 5초 (3,417 k바이트/초)
Selecting previously unselected package libexpat1-dev:i386.
(데이터베이스 읽는중 ...현재 140709개의 파일과 디렉터리가 설치되어 있습니다.)
Preparing to unpack .../libexpat1-dev_2.1.0-6+deb8u1_i386.deb ...
Unpacking libexpat1-dev:i386 (2.1.0-6+deb8u1) ...
Selecting previously unselected package libpython2.7-dev:i386.
Preparing to unpack .../libpython2.7-dev_2.7.9-2_i386.deb ...
(..이하 생략..)
{% endhighlight %}

python-dev 설치가 끝나면 다시 **make**를 실행합니다.

{% highlight sh %}
root@localhost:/home/westporch/Downloads/sip-4.17# make
make[1]: Entering directory '/home/westporch/Downloads/sip-4.17/sipgen'
make[1]: Nothing to be done for 'all'.
make[1]: Leaving directory '/home/westporch/Downloads/sip-4.17/sipgen'
make[1]: Entering directory '/home/westporch/Downloads/sip-4.17/siplib'
gcc -c -pipe -fPIC -O2 -w -DNDEBUG -I. -I/usr/include/python2.7 -o siplib.o siplib.c
gcc -c -pipe -fPIC -O2 -w -DNDEBUG -I. -I/usr/include/python2.7 -o apiversions.o apiversions.c
gcc -c -pipe -fPIC -O2 -w -DNDEBUG -I. -I/usr/include/python2.7 -o descriptors.o descriptors.c
gcc -c -pipe -fPIC -O2 -w -DNDEBUG -I. -I/usr/include/python2.7 -o qtlib.o qtlib.c
gcc -c -pipe -fPIC -O2 -w -DNDEBUG -I. -I/usr/include/python2.7 -o threads.o threads.c
gcc -c -pipe -fPIC -O2 -w -DNDEBUG -I. -I/usr/include/python2.7 -o objmap.o objmap.c
gcc -c -pipe -fPIC -O2 -w -DNDEBUG -I. -I/usr/include/python2.7 -o voidptr.o voidptr.c
gcc -c -pipe -fPIC -O2 -w -DNDEBUG -I. -I/usr/include/python2.7 -o array.o array.c
g++ -c -pipe -fPIC -O2 -w -DNDEBUG -I. -I/usr/include/python2.7 -o bool.o bool.cpp
g++ -shared -Wl,--version-script=sip.exp -o sip.so siplib.o apiversions.o descriptors.o qtlib.o threads.o objmap.o voidptr.o array.o bool.o 
make[1]: Leaving directory '/home/westporch/Downloads/sip-4.17/siplib'
root@localhost:/home/westporch/Downloads/sip-4.17#
{% endhighlight %}

## 1-(3). make install

**make install**을 실행합니다.

{% highlight sh %}
root@localhost:/home/westporch/Downloads/sip-4.17# make install
make[1]: Entering directory '/home/westporch/Downloads/sip-4.17/sipgen'
Gcp -f sip /usr/bin/sip
make[1]: Leaving directory '/home/westporch/Downloads/sip-4.17/sipgen'
make[1]: Entering directory '/home/westporch/Downloads/sip-4.17/siplib'
cp -f sip.so /usr/lib/python2.7/dist-packages/sip.so
strip /usr/lib/python2.7/dist-packages/sip.so
cp -f /home/westporch/Downloads/sip-4.17/siplib/sip.h /usr/include/python2.7/sip.h
make[1]: Leaving directory '/home/westporch/Downloads/sip-4.17/siplib'
cp -f sipconfig.py /usr/lib/python2.7/dist-packages/sipconfig.py
cp -f /home/westporch/Downloads/sip-4.17/sipdistutils.py /usr/lib/python2.7/dist-packages/sipdistutils.py
root@localhost:/home/westporch/Downloads/sip-4.17# 
{% endhighlight %}


# 2. PyQt 설치

[PyQt4](https://www.riverbankcomputing.com/software/pyqt/download)를 다운 받습니다.

저는 [PyQt-x11-gpl-4.11.4.tar.gz](http://sourceforge.net/projects/pyqt/files/PyQt4/PyQt-4.11.4/PyQt-x11-gpl-4.11.4.tar.gz) 버전으로 설치하겠습니다.

## 2-(1). python configure.py

**python configure.py**을 실행하고 *yes*를 입력합니다.

{% highlight sh %}
root@localhost:/home/westporch/Downloads/PyQt-x11-gpl-4.11.4# python configure.py
Determining the layout of your Qt installation...
This is the GPL version of PyQt 4.11.4 (licensed under the GNU General Public
License) for Python 2.7.9 on linux2.

Type 'L' to view the license.
Type 'yes' to accept the terms of the license.
Type 'no' to decline the terms of the license.

Do you accept the terms of the license? yes
Found the license file pyqt-gpl.sip.
Checking to see if the QtGui module should be built...
Checking to see if the QtHelp module should be built...
Checking to see if the QtMultimedia module should be built...
Checking to see if the QtNetwork module should be built...
Checking to see if the QtDBus module should be built...
Checking to see if the QtDeclarative module should be built...
Checking to see if the QtScript module should be built...
Checking to see if the QtScriptTools module should be built...
Checking to see if the QtXml module should be built...
Checking to see if the QtOpenGL module should be built...
(..이하 생략..)
{% endhighlight %}

## 2-(2). make

{% highlight sh %}
root@localhost:/home/westporch/Downloads/PyQt-x11-gpl-4.11.4# make
{% endhighlight %}

## 2-(3). make install

{% highlight sh %}
root@localhost:/home/westporch/Downloads/PyQt-x11-gpl-4.11.4# make install
{% endhighlight %}

# 3. PyQt 설치 확인

PyQt를 설치할 때 python configure.py, make, make install을 실행한 폴더에서 하위 폴더인 examples/widgets로 이동합니다.

제 경로는 다음과 같습니다.

{% highlight sh %}
root@localhost:/home/westporch/Downloads/PyQt-x11-gpl-4.11.4/examples/widgets# pwd
/home/westporch/Downloads/PyQt-x11-gpl-4.11.4/examples/widgets
root@localhost:/home/westporch/Downloads/PyQt-x11-gpl-4.11.4/examples/widgets# 
root@localhost:/home/westporch/Downloads/PyQt-x11-gpl-4.11.4/examples/widgets# ls
README          calendarwidget.py  groupbox.py     lineedits.py  shapedclock.py  styles.py   tooltips
analogclock.py  charactermap.py    icons           movie         sliders.py      stylesheet  wiggly.py
calculator.py   digitalclock.py    imageviewer.py  scribble.py   spinboxes.py    tetrix.py   windowflags.py
root@localhost:/home/westporch/Downloads/PyQt-x11-gpl-4.11.4/examples/widgets# 
{% endhighlight %}

**python digitalclock.py**를 실행했을 때 GUI 화면이 나타나면 PyQt가 제대로 설치된 것입니다.

# 4. Qt Designer 설치

[Qt Designer](http://doc.qt.io/qt-4.8/designer-manual.html)는 GUI 환경을 디자인하는데 도움을 줍니다. **apt-get install qt4-designer**을 실행하여 Qt Designer를 설치합니다.

{% highlight sh %}
root@localhost:/home/westporch# apt-get install qt4-designer
{% endhighlight %}


## 3-(1). cannot connect to X server :0 메시지가 발생할 경우

아래와 같은 메시지가 출력되면서 PyQt의 GUI 화면이 나타나지 않는 경우가 있습니다.

{% highlight sh %}
root@localhost:/home/westporch/Downloads/PyQt-x11-gpl-4.11.4/examples/widgets# python digitalclock.py 
No protocol specified
digitalclock.py: cannot connect to X server :0
root@localhost:/home/westporch/Downloads/PyQt-x11-gpl-4.11.4/examples/widgets#
{% endhighlight %}

이럴 때는 **su** 명령을 사용하기 전에 **xhost +**를 먼저 입력해야 합니다. 아래 화면을 참고해주세요.

{% highlight sh %}
westporch@localhost:~$ xhost +
access control disabled, clients can connect from any host
westporch@localhost:~$ su root
암호:
root@localhost:/home/westporch# 
root@localhost:/home/westporch# cd /home/westporch/Downloads/PyQt-x11-gpl-4.11.4/examples/widgets
root@localhost:/home/westporch/Downloads/PyQt-x11-gpl-4.11.4/examples/widgets# 
root@localhost:/home/westporch/Downloads/PyQt-x11-gpl-4.11.4/examples/widgets# python digitalclock.py 
{% endhighlight %}

![digitalclock](https://lh3.googleusercontent.com/-aGZGqIQzsOE/VqIkS9jwmkI/AAAAAAAACUk/i84ytILtUlc/s151-Ic42/PyQt_Digitalclock.png "PyQt로 실행한 GUI 화면")
