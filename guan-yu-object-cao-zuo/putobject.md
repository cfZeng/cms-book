---
description: Put Object用于上传文件。
---

# PutObject

{% api-method method="put" host="" path="/object/{bucket}/{objectName}" %}
{% api-method-summary %}
Put Object
{% endapi-method-summary %}

{% api-method-description %}
Put Object用于上传文件。
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="bucket" type="string" required=false %}
bucket
{% endapi-method-parameter %}

{% api-method-parameter name="objectName" type="string" %}
objectName
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="x-cms-isEncrypt" type="boolean" required=false %}
文件是否加密
{% endapi-method-parameter %}

{% api-method-parameter name="x-cms-callback" type="string" required=false %}
回调地址
{% endapi-method-parameter %}

{% api-method-parameter name="x-cms-meta-\*" type="string" %}
创建对象时，可以在HTTP请求中加入以“x-amz-meta-”开头的消息头，用来加入自定义的元数据，以便对对象进行自定义管理。当用户获取此对象或查询此对象元数据时，加入的自定义元数据将会在返回消息的头中出现。HTTP请求不包含消息体，长度不能超过8KB。
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="Content-MD5" %}
按照RFC 1864标准计算出消息体的MD5摘要字符串，即消息体128-bit MD5值经过base64编码后得到的字符串。
{% endapi-method-parameter %}

{% api-method-parameter name="Authentication" type="string" required=true %}
Authentication token to track down who is emptying our stocks.
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



