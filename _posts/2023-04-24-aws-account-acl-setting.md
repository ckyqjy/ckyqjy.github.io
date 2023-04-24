---
layout: post
title:  "AWS Account ACL Setting"
date:   2023-04-24 22:39:29 +0900
categories: AWS
tags: AWS
description: ''
image: ''
---

<p class="music-read">Account(Group) Access Control Setting For AWS</p>

### AWS에서 계정 ACL 설정
- IAM > 사용자 그룹 > 권한 > 권한 추가 > 인라인 정책 생성
- 아래의 JSON 추가
      
{% highlight json %}
{
    "Version": "2012-10-17",
    "Statement": 
    {
        "Effect": "Deny",
        "Action": "*",
        "Resource": "*",
        "Condition": {
            "NotIpAddress": {
                "aws.SourceIp": {
                    "{IP1}",
                    "{IP2}"
                }
            },
            "Bool": {
                "aws:ViaAWSService": "false"
            }
        }
    }
}
{% endhighlight %}