---                               
layout: post
title: "lm-sensors" 
author: <a href="mailto:westporch@gmail.com">Westporch</a>
---

lm-sensors를 사용하면 CPU의 온도를 확인할 수 있습니다.

1.lm-sensors 설치
--------------------------

**apt-get install lm-sensors**

{% highlight sh %}
root@localhost:/home/westporch# apt-get install lm-sensors
패키지 목록을 읽는 중입니다... 완료
의존성 트리를 만드는 중입니다       
상태 정보를 읽는 중입니다... 완료
제안하는 패키지:
  fancontrol sensord read-edid i2c-tools
다음 새 패키지를 설치할 것입니다:
  lm-sensors
0개 업그레이드, 1개 새로 설치, 0개 제거 및 84개 업그레이드 안 함.
108 k바이트 아카이브를 받아야 합니다.
이 작업 후 420 k바이트의 디스크 공간을 더 사용하게 됩니다.
받기:1 http://ftp.daum.net/debian/ jessie/main lm-sensors i386 1:3.3.5-2 [108 kB]
내려받기 108 k바이트, 소요시간 10초 (10.4 k바이트/초)
Selecting previously unselected package lm-sensors.
(데이터베이스 읽는중 ...현재 133753개의 파일과 디렉터리가 설치되어 있습니다.)
Preparing to unpack .../lm-sensors_1%3a3.3.5-2_i386.deb ...
Unpacking lm-sensors (1:3.3.5-2) ...
Processing triggers for systemd (215-17+deb8u1) ...
Processing triggers for man-db (2.7.0.2-5) ...
lm-sensors (1:3.3.5-2) 설정하는 중입니다 ...
Processing triggers for systemd (215-17+deb8u1) ...
root@localhost:/home/westporch#
{% endhighlight %}

2.lm-sensors 설정
-----------------

**sensors-detect**를 입력하고 YES 또는 yes를 입력합니다.

{% highlight sh %}
root@localhost:/home/westporch# sensors-detect
# sensors-detect revision 6209 (2014-01-14 22:51:58 +0100)
# System: SAMSUNG ELECTRONICS CO., LTD. 900X3C/900X3D/900X4C/900X4D [0.1] (laptop)
# Board: SAMSUNG ELECTRONICS CO., LTD. SAMSUNG_NP1234567890

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): YES
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): YES
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): YES
Using driver `i2c-i801' for device 0000:00:1f.3: Intel Panther Point (PCH)
Module i2c-dev loaded successfully.

Next adapter: i915 gmbus ssc (i2c-0)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: i915 gmbus vga (i2c-1)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: i915 gmbus panel (i2c-2)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: i915 gmbus dpc (i2c-3)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: i915 gmbus dpb (i2c-4)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: i915 gmbus dpd (i2c-5)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: DPDDC-B (i2c-6)
Do you want to scan it? (yes/NO/selectively): yes


Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)yes
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/kmod start'
to load them.

Unloading i2c-dev... OK
Unloading cpuid... OK

root@localhost:/home/westporch# 
{% endhighlight %}


3.sensors 명령어 실행
---------------------

**sensors** 명령어를 입력하면 CPU 온도를 확인할 수 있습니다.

{% highlight sh %}
root@localhost:/home/westporch# sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +44.0°C  (crit = +106.0°C)
temp2:        +29.8°C  (crit = +106.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +46.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +46.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +42.0°C  (high = +87.0°C, crit = +105.0°C)

root@localhost:/home/westporch# 
{% endhighlight %}
