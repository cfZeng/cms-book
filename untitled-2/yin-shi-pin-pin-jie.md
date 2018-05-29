---
description: 音视频拼接接口(avconcat)用于将指定的数个音频片段拼接成一段音频，或者将数个视频片段拼接成一段视频。
---

# 音视频拼接

注：

1. 不支持m3u8文件的拼接。如果要拼接m3u8文件，建议先转码再调用该接口拼接。



## 接口规格 {#1}

**注意：**接口规格不含任何空格与换行符，下列内容经过格式化以便阅读。

```text
avconcat/<Format>
        /<key1>
        /<key2>
        /<key3>
        /...

```

{% api-method method="post" host="" path="{bucket}/{objectId}/avconcat" %}
{% api-method-summary %}
avconcat
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

|  参数名称 |  必填 |  说明 |
| --- | --- | --- |
| `<Format>` | 是 | 目标视频的格式，例如 flv、mp4 等。 请参考[支持转换的视频格式](https://support.qiniu.com/hc/kb/article/182125/) |
| `<encodedUrlN>` | 是 | 经过[URL安全的Base64编码](https://developer.qiniu.com/kodo/manual/appendix#urlsafe-base64)的完整源文件URL ● 除去作为数据处理对象的源文件以外，还可以指定最多20个源文件（即总计21个片段）。 ● 所有源文件必须属于同一存储空间  ● 也可以把要拼接的第一个视频作为key传入。 |



