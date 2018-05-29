---
description: >-
  EXIF(EXchangeable Image File
  Format)是专门为数码相机的照片设定的可交换图像文件格式，通过在图片下载URL后附加exif指示符（区分大小写）获取。
---

# 图片EXIF信息

 **注意：**缩略图等经过云处理的新图片不支持该方法。

{% api-method method="get" host="" path="{bucket}/{objectId}/exif" %}
{% api-method-summary %}
exif
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="objectId" type="string" required=true %}
文件ID 
{% endapi-method-parameter %}

{% api-method-parameter name="bucket" type="string" required=true %}
bucket名称
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

## 请求报文 {#1}

### 请求语法 {#-}

```text
这儿编写抓包报文
```

## 响应报文 {#2}

### 响应语法 {#-}

```text
未确定响应结果
```



