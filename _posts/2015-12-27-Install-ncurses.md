---                               
layout: post
title: "NCurses 설치하기" 
author: <a href="mailto:westporch@gmail.com">Westporch</a>
---

# 1. NCurses 다운

ftp://ftp.gnu.org/pub/gnu/ncurses/ 에서 최신 버전의 NCurses를 다운받습니다.

2015.12.27 기준으로 최신 버전인 [ncurses-6.0](ftp://ftp.gnu.org/pub/gnu/ncurses/ncurses-6.0.tar.gz)을 설치하겠습니다.

{% highlight sh %}
root@RaspberryPi:~/Downloads# wget ftp://ftp.gnu.org/pub/gnu/ncurses/ncurses-6.0.tar.gz
--2015-12-27 14:47:12--  ftp://ftp.gnu.org/pub/gnu/ncurses/ncurses-6.0.tar.gz
           => ‘ncurses-6.0.tar.gz’
		   Resolving ftp.gnu.org (ftp.gnu.org)... 208.118.235.20, 2001:4830:134:3::b
		   Connecting to ftp.gnu.org (ftp.gnu.org)|208.118.235.20|:21... connected.
		   Logging in as anonymous ... Logged in!
		   ==> SYST ... done.    ==> PWD ... done.
		   ==> TYPE I ... done.  ==> CWD (1) /pub/gnu/ncurses ... done.
		   ==> SIZE ncurses-6.0.tar.gz ... 3131891
		   ==> PASV ... done.    ==> RETR ncurses-6.0.tar.gz ... done.
		   Length: 3131891 (3.0M) (unauthoritative)

		   ncurses-6.0.tar.gz          100%[===========================================>]   2.99M  1.50MB/s   in 2.0s   

		   2015-12-27 14:47:18 (1.50 MB/s) - ‘ncurses-6.0.tar.gz’ saved [3131891]

		   root@RaspberryPi:~/Downloads#
{% endhighlight %}

# 2. NCurses 설치

다운 받은 ncurses 파일의 압축을 해제합니다.

{% highlight sh %}
root@RaspberryPi:~/Downloads# ls
ncurses-6.0.tar.gz
root@RaspberryPi:~/Downloads# tar zxvf ncurses-6.0.tar.gz
root@RaspberryPi:~/Downloads# ls
ncurses-6.0  ncurses-6.0.tar.gz
root@RaspberryPi:~/Downloads#
{% endhighlight %}

압축을 해제한 ncurses-6.0 폴더로 이동합니다.

{% highlight sh %}
root@RaspberryPi:~/Downloads# cd ncurses-6.0
root@RaspberryPi:~/Downloads/ncurses-6.0#
{% endhighlight %}


## 2-(1). ./configure

{% highlight sh %}
root@RaspberryPi:~/Downloads/ncurses-6.0# ./configure
(...생략...)
Appending rules for normal model (form: ticlib+termlib+ext_tinfo+base+ext_funcs)
Appending rules for debug model (form: ticlib+termlib+ext_tinfo+base+ext_funcs)
Appending rules for normal model (test: ticlib+termlib+ext_tinfo+base+ext_funcs)
Appending rules for debug model (test: ticlib+termlib+ext_tinfo+base+ext_funcs)
creating headers.sh

** Configuration summary for NCURSES 6.0 20150808:

       extended funcs: yes
	   xterm terminfo: xterm-new

	   bin directory: /usr/bin
       lib directory: /usr/lib
       include directory: /usr/include
       man directory: /usr/share/man
       terminfo directory: /usr/share/terminfo

root@RaspberryPi:~/Downloads/ncurses-6.0#
{% endhighlight %}

## 2-(2). make

{% highlight sh %}
root@RaspberryPi:~/Downloads/ncurses-6.0# make
make[1]: Leaving directory '/root/Downloads/ncurses-6.0/misc'
root@RaspberryPi:~/Downloads/ncurses-6.0#
{% endhighlight %}


## 2-(3). make install

{% highlight sh %}
root@RaspberryPi:~/Downloads/ncurses-6.0# make install
installing std
installing stdcrt
installing vt100
installing vt300
/usr/bin/install -c ncurses-config /usr/bin/ncurses6-config
make[1]: Leaving directory '/root/Downloads/ncurses-6.0/misc'
root@RaspberryPi:~/Downloads/ncurses-6.0#
{% endhighlight %}

# 3. 설치 확인

NCurses 라이브러리를 이용하여 Hello World를 출력하는 프로그램을 만들어 보겠습니다.

## 3-(1). Hello World 프로그램

vi hello.c
{% highlight sh %}
root@RaspberryPi:~/NCurses# vi hello.c
{% endhighlight %}

hello.c 소스

{% highlight c %}
//hello.c   
#include <ncurses.h>

int main()
{
	    initscr();  // Start curses mode
	    printw("Hello World");  // Print Hello World
 	    refresh();  // Print it on to the real screen
	    getch();    // Wait for user input
	    endwin();   // End curses mode

	    return 0;
}
{% endhighlight %}

## 3-(2). 컴파일

{% highlight sh %}
root@RaspberryPi:~/NCurses# gcc -o hello hello.c -lncurses
root@RaspberryPi:~/NCurses# 
{% endhighlight %}

## 3-(3). 실행

{% highlight sh %}
root@RaspberryPi:~/NCurses# ls
hello  hello.c
root@RaspberryPi:~/NCurses# ./hello
{% endhighlight %}

*hello* 파일을 실행하면 Hello World가 출력됩니다.

{% highlight sh %}
Hello World
{% endhighlight %}
