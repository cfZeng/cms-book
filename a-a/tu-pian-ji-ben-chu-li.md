---
description: >-
  imageView
  提供简单快捷的图片格式转换、缩略、剪裁功能。只需要填写几个参数，即可对图片进行缩略操作，生成各种缩略图。imageView接口可支持处理的原图片格式有psd、jpeg、png、gif、webp、tiff、bmp。（webp不支持动图）注意：imageView
  接口支持的最大 gif 帧数为 200，超过 200，处理结果只返回原图。
---

# 图片基本处理

## 接口规格 {#1}

 **注意：**接口规格不含任何空格与换行符。

imageView/&lt;mode&gt;/w/&lt;LongEdge&gt;

                 /h/&lt;ShortEdge&gt;

                 /format/&lt;Format&gt;

                 /interlace/&lt;Interlace&gt;

                 / quality/&lt;Quality&gt;



## 

{% api-method method="get" host="" path=" /image/{bucket}/{objectId}/" %}
{% api-method-summary %}
imageView
{% endapi-method-summary %}

{% api-method-description %}
例子: http://192.168.0.77:6080/cms/image/{bucket}/{objectId}?imageView/ {mode}/
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="mode" type="string" required=true %}
模式
{% endapi-method-parameter %}

{% api-method-parameter name="bucket" type="string" required=true %}
bucket名称
{% endapi-method-parameter %}

{% api-method-parameter name="objectid" type="string" required=true %}
文件ID
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

##  {#1}

```text

 模式 说明/0/w/<LongEdge>/h/<ShortEdge>限定缩略图的长边最多为<LongEdge>，短边最多为<ShortEdge>，进行等比缩放，不裁剪。如果只指定 w 参数则表示限定长边（短边自适应），只指定 h 参数则表示限定短边（长边自适应）。/1/w/<Width>/h/<Height>限定缩略图的宽最少为<Width>，高最少为<Height>，进行等比缩放，居中裁剪。转后的缩略图通常恰好是 <Width>x<Height> 的大小（有一个边缩放的时候会因为超出矩形框而被裁剪掉多余部分）。如果只指定 w 参数或只指定 h 参数，代表限定为长宽相等的正方图。/2/w/<Width>/h/<Height>限定缩略图的宽最多为<Width>，高最多为<Height>，进行等比缩放，不裁剪。如果只指定 w 参数则表示限定宽（长自适应），只指定 h 参数则表示限定长（宽自适应）。它和模式0类似，区别只是限定宽和高，不是限定长边和短边。从应用场景来说，模式0适合移动设备上做缩略图，模式2适合PC上做缩略图。/3/w/<Width>/h/<Height>限定缩略图的宽最少为<Width>，高最少为<Height>，进行等比缩放，不裁剪。如果只指定 w 参数或只指定 h 参数，代表长宽限定为同样的值。你可以理解为模式1是模式3的结果再做居中裁剪得到的。/4/w/<LongEdge>/h/<ShortEdge>限定缩略图的长边最少为<LongEdge>，短边最少为<ShortEdge>，进行等比缩放，不裁剪。如果只指定 w 参数或只指定 h 参数，表示长边短边限定为同样的值。这个模式很适合在手持设备做图片的全屏查看（把这里的长边短边分别设为手机屏幕的分辨率即可），生成的图片尺寸刚好充满整个屏幕（某一个边可能会超出屏幕）。/5/w/<LongEdge>/h/<ShortEdge>限定缩略图的长边最少为<LongEdge>，短边最少为<ShortEdge>，进行等比缩放，居中裁剪。如果只指定 w 参数或只指定 h 参数，表示长边短边限定为同样的值。同上模式4，但超出限定的矩形部分会被裁剪。
```

