---
description: 视频帧缩略图接口(vframe)用于从视频流中截取指定时刻的单帧画面并按指定大小缩放成图片。
---

# 视频帧缩略图

## 接口规格 {#1}

```text
vframe/<Format>
      /offset/<Second>
      /w/<Width>
      /h/<Height>
      /rotate/<Degree>

```

{% api-method method="get" host="" path="{bucket}/{objectId}/vframe" %}
{% api-method-summary %}
vframe
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
{% api-method-parameter name=" x-ycore-cms-token" type="string" required=true %}
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

|  参数名称 |  必填 |  说明 |
| --- | --- | --- | --- | --- | --- |
| `<Format>` | 是 | 输出的目标截图格式，支持`jpg`、`png`等。 |
| `/offset/<Second>` | 是 | 指定截取视频的时刻，单位：秒，精确到毫秒。 |
| `/w/<Width>` |  | 缩略图宽度，单位：像素（px），取值范围为1-3840。 |
| `/h/<Height>` |  | 缩略图高度，单位：像素（px），取值范围为1-2160。 |
| `/rotate/<Degree>` |  | 指定顺时针旋转的度数，可取值为`90`、`180`、`270`、`auto`，默认为不旋转。 |

##  {#2}

