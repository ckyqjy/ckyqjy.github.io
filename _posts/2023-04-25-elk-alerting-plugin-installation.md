---
layout: post
title:  "ELK Alerting Plugin Installation"
date:   2023-04-25 01:43:29 +0900
categories: ELK
tags: Open Distro, ELK
description: ''
image: ''
---

<p class="music-read">Open Distro Alerting Plugin Installation for ELK 7.10.2</p>

### 주의사항
- sudo유저로 진행
- 자바 1.8버전 이상
- git 2.5버전 이상으로 설치
      
### ELK 7.10.2버전 설치
{% highlight bash %}
wget https://artifacts.elastic.co/packages/7.x/yum/7.10.2/elasticsearch-7.10.2-x86_64.rpm
wget https://artifacts.elastic.co/packages/7.x/yum/7.10.2/kibana-7.10.2-x86_64.rpm
wget https://artifacts.elastic.co/packages/7.x/yum/7.10.2/logstash-7.10.2-x86_64.rpm
wget https://artifacts.elastic.co/packages/7.x/yum/7.10.2/filebeat-7.10.2-x86_64.rpm
yum -y install elasticsearch-7.10.2-x86_64.rpm
yum -y install kibana-7.10.2-x86_64.rpm
yum -y install logstash-7.10.2-x86_64.rpm
yum -y install filebeat-7.10.2-x86_64.rpm
{% endhighlight %}

### Plugin Installation 참고
- 오픈디스트로 엘라스틱서치 플러그인: https://github.com/opendistro-for-elasticsearch/alerting
- 오픈디스트로 키바나 플러그인: https://github.com/opendistro-for-elasticsearch/alerting-kibana-plugin
- 키바나 bootstrap 이슈 참고: https://github.com/elastic/kibana/issues/47214

### kibana 7.10.2 Source Code
{% highlight bash %}
wget https://github.com/elastic/kibana/archive/refs/tags/v7.10.2.tar.gz
{% endhighlight %}

### alerting-kibana-plugin-latest Source Code
{% highlight bash %}
wget https://github.com/opendistro-for-elasticsearch/alerting-kibana-plugin/archive/refs/heads/main.zip
{% endhighlight %}

### nodejs installation
{% highlight bash %}
wget https://nodejs.org/dist/v10.23.1/node-v10.23.1-linux-x64.tar.xz
tar xf [node-v14.15.3-linux-x64.tar.xz]
mv ./[node-v14.15.3-linux-x64] /usr/local/lib/node
export NODEJS_HOME=/usr/local/lib/node
export PATH=$NODEJS_HOME/bin:$PATH
. ~/.bashrc
{% endhighlight %}

### yarn installation
{% highlight bash %}
cd /opt
wget https://yarnpkg.com/latest.tar.gz --no-check-certificate
tar zvxf latest.tar.gz
export PATH=/opt/yarn/bin:$PATH
{% endhighlight %}

### elasticsearch plugin installation
{% highlight bash %}
/usr/share/elasticsearch/bin/elasticsearch-plugin install file:///usr/share/elasticsearch/bin/opendistro-alerting-1.13.1.0-SNAPSHOT.zip
{% endhighlight %}

### kibana plugin installation
{% highlight bash %}
/usr/share/kibana/bin/kibana-plugin install file:///usr/share/kibana/bin/opendistroAlertingKibana-1.13.0.0.zip
{% endhighlight %}