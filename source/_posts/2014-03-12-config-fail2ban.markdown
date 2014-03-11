---
layout: post
title: "config Fail2Ban"
date: 2014-03-12 00:25:23 +0800
comments: true
categories: 
- ubuntu
- fail2ban
---
Fail2Ban 是一款用 Python 代码编写的入侵防御软件，它可以分析多种服务的日志文件 (例如 ssh apache postfix mysql 等) 来侦测可能的暴力攻击，并且自动创建防火墙 (例如 iptables) 规则来达到阻止攻击源访问的目的

这里以 Debian 为例，仅考虑如何防御 ssh 攻击的情况 (例如: 多次用不存在的用户名创建 ssh 连接，多次使用不同密码尝试登陆某 ssh 账户)，安装配置步骤如下

1安装

	apt-get update
	apt-get install fail2ban

2. (从 jail.conf 模板) 创建配置文件 jail.local

cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local`


3. 编辑配置文件
``` bash
	nano /etc/fail2ban/jail.local
```

4. 主要可以考虑配置的几个地方
``` bash
	[DEFAULT]
	ignoreip  白名单 IP 地址
	bantime 被禁时间长度 (秒)
	maxretry 多少次尝试攻击即可以考虑被禁止

	[ssh] 这个分支是默认开启的
	enabled = true
	port    = ssh
	filter  = sshd
	logpath  = /var/log/auth.log
	maxretry = 6
```
5. 重启 Fai2Ban 服务来应用新的配置

``` bash
	/etc/init.d/fail2ban restart
```

6. 就这么简单，其他的功能可以在配置文件内自行发挥