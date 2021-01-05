---
layout: page
title: About
description: 业精于勤，荒于嬉；行成于思，毁于随
keywords: wuaifx, 吾爱分享
comments: true
menu: 关于
permalink: /about/
---


我为人人，人人为我；为分享而生！
								     --吾爱分享

## 联系

<!-- 以下website不用替换成自己的  -->
<ul>
{% for website in site.data.social %}
<li>{{website.sitename }}：<a href="{{ website.url }}" target="_blank">@{{ website.name }}</a></li>
{% endfor %}
{% if site.url contains 'feibuer.github.io/website' %}
<li>
微信公众号：<br />
<img style="height:192px;width:192px;border:1px solid lightgrey;" src="{{ assets_base_url }}/assets/images/qrcode.jpg" alt="吾爱分享" />
</li>
{% endif %}
</ul>


## Skill Keywords

{% for skill in site.data.skills %}
### {{ skill.name }}
<div class="btn-inline">
{% for keyword in skill.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
