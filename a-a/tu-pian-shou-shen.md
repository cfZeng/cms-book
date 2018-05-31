---
description: '图片瘦身尽可能在不影响画质的情况下，对JPEG、PNG格式的图片实时压缩，大幅度缩小文件的体积:加快客户端图片的加载速度，提升用户体验;'
---

# 图片瘦身

{% api-method method="get" host="" path="{bucket}/{objectId}?imageslim" %}
{% api-method-summary %}
imageslim
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="objectId" type="string" required=true %}
文件ID值
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



