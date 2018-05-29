---
description: CMS提供三种水印接口：图片水印、文字水印。注意：watermark 接口支持的最大 gif 帧数为 200，超过 200，处理结果只返回原图。
---

# 图片水印处理

## 图片水印 {#1}

### 接口规格 {#-}

 **注意：**接口规格不含任何空格与换行符。

```text
watermark/1
         /image/<encodedImageURL>
         /dissolve/<dissolve>
         /gravity/<gravity>
         /dx/<distanceX>
         /dy/<distanceY>
         /ws/<watermarkScale>
```

{% api-method method="get" host="" path="/image/{bucket}/{objectId}?watermark/1/" %}
{% api-method-summary %}
watermark
{% endapi-method-summary %}

{% api-method-description %}
例子：http://192.168.0.77:6080/cms/image/{bucket}/{objectId}? watermark/1/image/aHR0cHM6Ly93d3cuYmFpZHUuY29tL2ltZy9iZF9sb2dvMS5wbmc=
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

|  参数名称 |  必填 |  说明 |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  /image/&lt;encodedImageURL&gt; |  是 |  水印源图片网址（经过URL安全的Base64编码），必须有效且返回一张图片。 |
|  /dissolve/&lt;dissolve&gt; |  |  水印透明度，取值范围1-100，默认值为100（完全不透明）。 |
|  /gravity/&lt;gravity&gt; |  |  水印位置，参考水印锚点参数表，默认值为`SouthEast`（右下角）。 |
|  /dx/&lt;distanceX&gt; |  |  横轴边距，单位:像素\(px\)，默认值为10。 |
|  /dy/&lt;distanceY&gt; |  |  纵轴边距，单位:像素\(px\)，默认值为10。 |
|  /ws/&lt;watermarkScale&gt; |  |  取值范围：1-100，水印图片会根据设置的百分比与原始尺寸ws。例如：水印尺寸300x200，ws=20, 水印宽=ws/100\*300=60,高=40，水印尺寸=60x40; |
|  |  |  |

```text
水印锚点参数表
NorthWest     |     North      |     NorthEast
              |                |    
              |                |    
--------------+----------------+--------------
              |                |    
West          |     Center     |          East 
              |                |    
--------------+----------------+--------------
              |                |    
              |                |    
SouthWest     |     South      |     SouthEast

```

```text
watermark/2
         /text/<encodedText>
         /font/<encodedFontName>
         /fontsize/<fontSize>
         /fill/<encodedTextColor>
         /dissolve/<dissolve>
         /gravity/<gravity>
         /dx/<distanceX>
         /dy/<distanceY>

```

{% api-method method="get" host="" path="/image/{bucket}/{objectId}?watermark/2/" %}
{% api-method-summary %}
文字水印
{% endapi-method-summary %}

{% api-method-description %}
例子: http://192.168.0.77:6080/cms/image/{bucket}/{objectId}? watermark/2/text/eGlqaXVmdQ==
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="objectId" type="string" required=false %}
文件ID
{% endapi-method-parameter %}

{% api-method-parameter name="bucket" type="string" required=false %}
bucket名称
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  /text/&lt;encodedText&gt; |  是 |  水印文字内容（经过URL安全的Base64编码） |
|  /font/&lt;encodedFontName&gt; |  |  水印文字字体（经过URL安全的Base64编码），默认为黑体 **注意：**中文水印必须指定中文字体。 |
|  /fontsize/&lt;fontSize&gt; |  |  水印文字大小，单位: 缇 ，等于1/20磅，默认值是240缇，参考DPI为72。 |
|  /fill/&lt;encodedTextColor&gt; |  |  水印文字颜色，RGB格式，可以是颜色名称（例如 red）或十六进制（例如 \#FF0000），参考[RGB颜色编码表](http://www.rapidtables.com/web/color/RGB_Color.htm)，默认为黑色。经过URL安全的Base64编码。 |
|  /dissolve/&lt;dissolve&gt; |  |  水印文字透明度，取值范围1-100，默认值100（完全不透明）。 |
|  /gravity/&lt;gravity&gt; |  |  水印位置，参考水印位置参数表，默认值为`SouthEast`（右下角）。 |
|  /dx/&lt;distanceX&gt; |  |  横轴边距，单位:像素\(px\)，默认值为10。 |
|  /dy/&lt;distanceY&gt; |  |  纵轴边距，单位:像素\(px\)，默认值为10。 |

