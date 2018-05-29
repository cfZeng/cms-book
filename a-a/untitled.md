---
description: 图片基本信息包括图片格式、图片大小、色彩模型。在图片下载URL后附加imageInfo指示符（区分大小写），即可获取JSON格式的图片基本信息。
---

# 图片基本信息



{% api-method method="get" host="" path=" /image/{bucket}/{objectId}" %}
{% api-method-summary %}
imageInfo
{% endapi-method-summary %}

{% api-method-description %}
例子：http://192.168.0.77:6080/cms/image/xjf-image/1525925059047?imageInfo  
不加参数则返回原图
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
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{
    "name": "Cake's name",
    "recipe": "Cake's recipe name",
    "cake": "Binary cake"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Could not find a cake matching this query.
{% endapi-method-response-example-description %}

```javascript
{
    "message": "Ain't no cake like that."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

