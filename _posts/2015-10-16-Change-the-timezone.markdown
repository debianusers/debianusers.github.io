---                     
layout: post
title: "타임존(Timezone) 변경" 
author: <a href="mailto:westporch@gmail.com">Westporch</a>
---

1.현재 설정된 타임존 확인
------------------------

_timedatectl_

{% highlight ruby %}
root@localhost:/home/westporch# timedatectl
      Local time: 금 2015-11-20 11:34:20 KST
  Universal time: 금 2015-11-20 02:34:20 UTC
        RTC time: 금 2015-11-20 11:34:23
       Time zone: Asia/Seoul (KST, +0900)
     NTP enabled: no
NTP synchronized: no
 RTC in local TZ: yes
      DST active: n/a

Warning: The RTC is configured to maintain time in the local time zone. This
         mode is not fully supported and will create various problems with time
         zone changes and daylight saving time adjustments. If at all possible, use
         RTC in UTC by calling 'timedatectl set-local-rtc 0'.
root@localhost:/home/westporch#
{% endhighlight %}

2.Timezone 변경
-------------------

**timedatectl set-timezone '표준 시간대'**

(**표준 시간대**는 *timedatectl list-timezones* 명령어로 확인할 수 있습니다.)
 
{% highlight ruby %}
root@localhost:/home/westporch# timedatectl list-timezones
Africa/Abidjan
Africa/Accra
Africa/Addis_Ababa
Africa/Algiers
Africa/Asmara
(... 이하 생략...)
{% endhighlight %}

타임존을 KST -> JST로 변경하겠습니다. (**timedatectl set-timezone Asia/Tokyo**)

{% highlight ruby %}
root@localhost:/home/westporch# timedatectl set-timezone Asia/Tokyo
{% endhighlight %}

타임존이 JST로 변경되었습니다.
{% highlight ruby %}
root@localhost:/home/westporch# timedatectl
      Local time: 금 2015-11-20 11:37:19 JST
  Universal time: 금 2015-11-20 02:37:19 UTC
        RTC time: 금 2015-11-20 11:37:20
       Time zone: Asia/Tokyo (JST, +0900)
     NTP enabled: no
NTP synchronized: no
 RTC in local TZ: yes
      DST active: n/a

Warning: The RTC is configured to maintain time in the local time zone. This
         mode is not fully supported and will create various problems with time
         zone changes and daylight saving time adjustments. If at all possible, use
         RTC in UTC by calling 'timedatectl set-local-rtc 0'.
root@localhost:/home/westporch#
{% endhighlight %}
