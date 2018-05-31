---
description: >-
  roundPic
  将图片生成圆角图片，并且可以指定图片的圆角大小。这个接口支持的原图片格式有png、jpg，处理后的图片格式为png。注意：处理前的图片大小不能超过20M。
---

# 图片圆角处理

## 接口规格 {#1}

**注意：**接口规格不含任何空格与换行符。

```text
roundPic/radius/<radius>
        /radiusx/<radiusx>
        /radiusy/<radiusy>

```

|  参数名称 |  必填 |  说明 |
| --- | --- | --- | --- |
|  /radius/&lt;radius&gt; |  否 |  圆角大小的参数，水平和垂直的值相同，可以使用像素数（如200）或百分比（如!25p）。不能与`radiusx`和`radiusy`同时使用。 |
|  /radiusx/&lt;radiusx&gt; |  否 |  圆角水平大小的参数，可以使用像素数（如200）或百分比（如!25p）。需要与`radiusy`同时使用。 |
|  /radiusy/&lt;radiusy&gt; |  否 |  圆角垂直大小的参数，可以使用像素数（如200）或百分比（如!25p）。需要与`radiusx`同时使用。 |

{% api-method method="get" host="" path="{bucket}/{objectId}?roundPic/radius/20" %}
{% api-method-summary %}
roundPic
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

