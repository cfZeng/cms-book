---
description: >-
  imageMogr提供一系列高级图片处理功能，包括格式转换、缩放、裁剪、旋转等。imageMogr接口可支持处理的原图片格式有
  psd、jpeg、png、gif、webp、tiff、bmp。（webp不支持动图）注意：imageMogr接口支持的最大 gif 帧数为 200，超过
  200，处理结果只返回原图。
---

# 图片高级处理

## 接口规格 {#1}

 **注意：**接口规格不含任何空格与换行符。

```text
imageMogr/thumbnail/<imageSizeGeometry>
          /strip
          /gravity/<gravityType>
          /crop/<imageSizeAndOffsetGeometry>
          /rotate/<rotateDegree>
          /blur/<radius>x<sigma>
          /quality/<quality>
          /sharpen/<sharpen>

```

|  参数名称 |  说明 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  thumbnail |  参看缩放参数表默认为不缩放。 |
|  strip |  去除图片中的元信息。去除的信息有：bKGD、cHRM、EXIF、gAMA、iCCP、iTXt、sRGB、tEXt、zCCP、zTXt、date |
|  gravity |  参看图片处理重心参数表，目前在 imageView中只影响其后的裁剪偏移参数，默认为左上角\(NorthWest\)。 |
|  crop |  参看裁剪操作参数表，默认为不裁剪。 |
|  rotate |  旋转角度，取值范围为1-360，默认为不旋转。 |
|  blur |  高斯模糊参数。radius是模糊半径，取值范围为1-50。sigma是正态分布的标准差，必须大于0。图片格式为gif时，不支持该参数。 |
|  quality |  新图的图片质量。取值范围为1-100，默认75。 |
|  sharpen |  图片是否锐化，当设置值为1时打开锐化效果。 |

## 

{% api-method method="get" host="" path=" /image/{bucket}/{objectId}/" %}
{% api-method-summary %}
imageMogr
{% endapi-method-summary %}

{% api-method-description %}
例子\(不加参数默认原图\): http://192.168.0.77:6080/cms/image/{bucket}/{objectId}?imageMogr/{mode}/
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

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### 缩放操作参数表 {#-}

|  参数名称 |  必填 |  说明 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  /thumbnail/!&lt;Scale&gt;p |  |  基于原图大小，按指定百分比缩放。Scale取值范围1-999。 |
|  /thumbnail/!&lt;Scale&gt;px |  |  以百分比形式指定目标图片宽度，高度不变。Scale取值范围1-999。 |
|  /thumbnail/!x&lt;Scale&gt;p |  |  以百分比形式指定目标图片高度，宽度不变。Scale取值范围1-999。 |
|  /thumbnail/&lt;Width&gt;x |  |  指定目标图片宽度，高度等比缩放，Width取值范围1-9999。 |
|  /thumbnail/x&lt;Height&gt; |  |  指定目标图片高度，宽度等比缩放，Height取值范围1-9999。 |
|  /thumbnail/&lt;Width&gt;x&lt;Height&gt; |  |  等比缩放，比例值为宽缩放比和高缩放比的较小值，Width 和 Height 取值范围1-9999。 |
|  /thumbnail/!&lt;Width&gt;x&lt;Height&gt;r |  |  等比缩放，比例值为宽缩放比和高缩放比的较大值，Width 和 Height 取值范围1-9999。 |
|  /thumbnail/&lt;Width&gt;x&lt;Height&gt;! |  |  按指定宽高值强行缩略，可能导致目标图片变形，width和height取值范围1-9999。 |
|  /thumbnail/&lt;Width&gt;x&lt;Height&gt;&gt; |  |  等比缩小，比例值为宽缩放比和高缩放比的较小值。如果目标宽和高都大于原图宽和高，则不变，Width 和 Height 取值范围1-9999。 |
|  /thumbnail/&lt;Width&gt;x&lt;Height&gt;&lt; |  |  等比放大，比例值为宽缩放比和高缩放比的较小值。如果目标宽\(高\)小于原图宽\(高\)，则不变，Width 和 Height 取值范围1-9999。 |
|   |  |   |

### 图片处理重心参数表 {#-}

 在图片高级处理现有的功能中只影响其后的裁剪操作参数表，即裁剪操作以 gravity 为原点开始偏移后，进行裁剪操作。

```text
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

### 裁剪操作参数表 \(cropsize\) {#-cropsize-}

|  /crop/&lt;Width&gt;x |  指定目标图片宽度，高度不变。取值范围为0-10000。 |
| --- | --- | --- |
|  /crop/x&lt;Height&gt; |  指定目标图片高度，宽度不变。取值范围为0-10000。 |
|  /crop/&lt;Width&gt;x&lt;Height&gt; |  同时指定目标图片宽高。取值范围为0-10000。 |

### 裁剪偏移参数表 \(cropoffset\) {#-cropoffset-}



|  /crop/!{cropsize}a&lt;dx&gt;a&lt;dy&gt; |  相对于偏移锚点，向右偏移dx个像素，同时向下偏移dy个像素。取值范围不限，小于原图宽高即可。 |
| --- | --- | --- | --- |
|  /crop/!{cropsize}-&lt;dx&gt;a&lt;dy&gt; |  相对于偏移锚点，从指定宽度中减去dx个像素，同时向下偏移dy个像素。取值范围不限，小于原图宽高即可。 |
|  /crop/!{cropsize}a&lt;dx&gt;-&lt;dy&gt; |  相对于偏移锚点，向右偏移dx个像素，同时从指定高度中减去dy个像素。取值范围不限，小于原图宽高即可。 |
|  /crop/!{cropsize}-&lt;dx&gt;-&lt;dy&gt; |  相对于偏移锚点，从指定宽度中减去dx个像素，同时从指定高度中减去dy个像素。取值范围不限，小于原图宽高即可。 |

 /crop/!300x400a10a10 表示从源图坐标为 x:10,y:10 处截取 300x400 的子图片。 /crop/!300x400-10a10 表示从源图坐标为 x:0,y:10 处截取 290x400 的子图片。

