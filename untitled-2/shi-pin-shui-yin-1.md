# 视频水印

## 接口规格 {#1}

* 现在视频水印功能已经和转码`avthumb`功能合并，可以同时转码以及做水印。
* 在`avthumb`中添加`wmImage/wmGravity`与原先的`vwatermark`里面的`image/gravity`对应。
* 与原`vwatermark`相比，增加文字水印接口，新增参数`wmText` 、`wmGravityText`、 `wmFont`、`wmFontColor`、`wmFontSize`。

**注意：**接口规格不含任何空格与换行符，下列内容经过格式化以便阅读。

```text
avthumb/<format>
       /...
       /wmImage/<EncodedRemoteImageUrl>
       /wmGravity/<Gravity>
       /wmOffsetX/<offsetX>
       /wmOffsetY/<offsetY>
       /wmText/<EncodedText>
       /wmGravityText/<GravityText>
       /wmFont/<EncodeFont>
       /wmFontColor/<EncodeFontColor>
       /wmFontSize/<FontSize>
       /wmConstant/<Constant>

```

{% api-method method="post" host="" path="{bucket}/{objectId}/avthumb" %}
{% api-method-summary %}
avthumb
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
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `...` |  | [avthumb](https://developer.qiniu.com/dora/api/audio-and-video-transcoding-avthumb)的其他参数 |
| `<EncodedRemoteImageUrl><EncodedText>` | 至少填一项 | 水印的源路径，图片水印目前仅支持远程路径，需要经过`urlsafe_base64_encode`。 |
| `<Gravity>`及`<GravityText>` |  | 打水印的位置，参考[水印锚点参数表](https://developer.qiniu.com/dora/manual/1314/video-watermarking#vwatermark-anchor-spec)，默认值为`NorthEast`（右上角）。 |
| `/wmOffsetX/<offsetX>` |  | 视频图片水印位置的相对横向偏移量，当值为正数时则向右偏移，反之向左，有-10的固定偏移。 |
| `/wmOffsetY/<offsetY>` |  | 视频图片水印位置的相对纵向偏移量，当值为正数时则向下偏移，反之向上，有10的固定偏移。 |
| `<EncodeFont>` |  | 文本字体（详见支持[字体列表](https://support.qiniu.com/hc/kb/article/112878/)），需要经过`urlsafe_base64_encode`，默认为黑体。 **注意：**中文水印必须指定中文字体。 |
| `<EncodeFontColor>` |  | 水印文字颜色，需要经过`urlsafe_base64_encode`，RGB格式，可以是颜色名称（例如red）或十六进制（例如 \#FF0000），参考RGB颜色编码表，默认为黑色。 |
| `<FontSize>` |  | 水印文字大小，单位: 缇，等于1/20磅，默认值0（默认大小）。 |
| `<Constant>` |  | 用于设置水印图片是否随源视频DAR（display aspect ratio）变化而产生形变。不填值或设为0，水印图片会随源视频DAR变化而产生形变；设为1，水印图片保持原有宽高比。该参数仅对wmImage有效。 |

 **水印锚点参数表**

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

