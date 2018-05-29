---
description: 音视频元信息接口(avinfo)用于获取指定音频、视频资源的元信息。
---

# 音视频元信息

{% api-method method="get" host="" path="{bucket}/{objectId}/avinfo" %}
{% api-method-summary %}
avinfo  
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="bucket" type="string" required=true %}
bucket名称
{% endapi-method-parameter %}

{% api-method-parameter name="objectId" type="string" required=true %}
文件ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="x-ycore-cms-token" type="string" required=true %}
接口认证
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## 请求语法 {#1}

```text
未确定
```

## 响应语法 {#2}

```text
未确定
```

## 响应内容 {#3}

 如果请求成功，返回包含如下内容的JSON字符串（已格式化，便于阅读）

