---
layout: post
title:  "Connect to Windows through bastion"
date:   2023-04-26 00:43:29 +0900
categories: EC2
tags: bastion
description: ''
image: ''
---

<p class="music-read">Connect to internal Windows server through bastion server</p>

#### 주의사항
> bastion 서버에서 접속 대상 서버로 연결할 수 있도록 보안 그룹 설정
> 이하 Windows 설정 진행

#### 1. bastion을 경유하여 대상 서버로 접속할 수 있도록 설정
{% highlight bash %}
ssh -L ${LOCAL_HOST_LISTEN_PORT}:${TARGET_SERVER_PRIVATE_IPV4}:3389 ec2-user@${BASTION_SERVER_IPV4} -i ${BASTION_SERVER_CONNECT_PEM_KEY}
{% endhighlight %}

#### 2. 설정 호스트에서 Listen 포트 확인
{% highlight bash %}
netstat -an | find "63389"
{% endhighlight %}

#### 3. 로컬 호스트를 통해 대상 서버로 연결
