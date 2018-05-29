---
description: 音视频转码接口方便用户对音频、视频资源进行编码和格式转换。
---

# 音视频转码

{% api-method method="post" host="" path="/pfop/{bucket}/{objectid}" %}
{% api-method-summary %}
pfop
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="bucket" type="string" required=true %}
bucket名称
{% endapi-method-parameter %}

{% api-method-parameter name="objectid" type="string" required=true %}
objectid文件ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="x-ycore-cms-token" type="string" required=true %}
接口认证
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="fops" type="string" required=true %}
转码参数
{% endapi-method-parameter %}

{% api-method-parameter name="notifyURL" type="string" required=true %}
通知地址
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
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

## 接口规格 {#1}

 **注意：**接口规格不含任何空格与换行符，下列内容经过格式化以便阅读。

```text
avthumb/<Format>
       /ab/<BitRate>
       /aq/<AudioQuality>
       /ar/<SamplingRate>
       /r/<FrameRate>
       /vb/<VideoBitRate>
       /vcodec/<VideoCodec>
       /acodec/<AudioCodec>
       /scodec/<SubtitleCodec>
       /subtitle/<SubtitleURL>
       /ss/<SeekStart>
       /t/<Duration>
       /s/<Resolution>
       /autoscale/<Autoscale>
       /aspect/<Aspect>
       /stripmeta/<StripMeta>
       /h264Crf/<H264Crf>
       /rotate/<Degree>
       /wmImage/<EncodedRemoteImageUrl>
       /wmGravity/<Gravity>
       /wmText/<EncodedText>
       /wmGravityText/<GravityText>
       /wmFont/<font>
       /wmFontColor/<fontcolor>
       /wmFontSize/<fontsize>
       /writeXing/<Xing>
       /an/<AudioNo>
       /vn/<VideoNo> 
       /sn/<SubtitleNo> 
       /hlsMethod/<HLSMethod> 
       /gop/<GroupOfPictures>

```

|  参数名称 |  类别 |  必填 |  说明 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  &lt;Format&gt; |  A/V |  是 |  封装格式，具体细节请参考支持转换的封装格式。 |
|  /ab/&lt;BitRate&gt; |  A |  |  音频码率，单位：比特每秒（bit/s），常用码率：64k，128k，192k，256k，320k等。在不改变音频编码格式时，若指定码率大于原音频码率，则使用原音频码率进行转码。 |
|  /aq/&lt;AudioQuality&gt; |  A |  |  音频质量，取值范围为0-9（mp3），10-500（aac），仅支持mp3和aac，值越小越高。不能与上述码率参数共用。 |
|  /ar/&lt;SamplingRate&gt; |  A |  |  音频采样频率，单位：赫兹（Hz），常用采样频率：8000，12050，22050，44100等。 |
|  /r/&lt;FrameRate&gt; |  V |  |  视频帧率，每秒显示的帧数，单位：赫兹（Hz），常用帧率：24，25，30等，一般用默认值。 |
|  /vb/&lt;VideoBitRate&gt; |  V |  |  视频码率，单位：比特每秒（bit/s），常用视频码率：128k，1.25m，5m等。在不改变视频编码格式时，若指定码率大于原视频码率，则使用原视频码率进行转码。 |
|  /vcodec/&lt;VideoCodec&gt; |  V |  |  视频编码格式，具体细节请参考支持转换额视频编码格式。 |
|  /acodec/&lt;AudioCodec&gt; |  A |  |  音频编码格式，具体细节请参考支持转换的音频编码格式。 |
|  /audioProfile/&lt;profile&gt; |  A |  |  设置音频的profile等级，支持：aac\_he。**注：**需配合 `libfdk_aac` 编码方案使用，如 `avthumb/m4a/acodec/libfdk_aac/audioProfile/aac_he`。 |
|  /scodec/&lt;SubtitleCodec&gt; |  V |  |  字幕编码方案，支持方案：`mov_text`。该参数仅用于修改带字幕视频的字幕编码。 |
|  /ss/&lt;SeekStart&gt; |  A/V |  |  指定音视频截取的开始时间，单位：秒，支持精确到毫秒，例如3.345s。用于视频截取，从一段视频中截取一段视频。 |
|  /t/&lt;Duration&gt; |  A/V |  |  指定视频截取的长度，单位：秒，支持精确到毫秒，例如1.500s。用于视频截取，从一段视频中截取一段视频。 |
|  /s/&lt;Resolution&gt; |  V |  |  指定视频分辨率，格式为`<width>x<height>`或者预定义值，`width` 取值范围 \[20,3840\]，`height` 取值范围 \[20,2160\]。 |
|  /autoscale/&lt;Autoscale&gt; |  V |  |  配合参数`/s/`使用，指定为1时，把视频按原始比例缩放到`/s/`指定的矩形框内，0或者不指定会强制缩放到对应分辨率，可能造成视频变形。 |
|  /aspect/&lt;Aspect&gt; |  V |  |  该参数为视频在播放器中显示的宽高比，格式为`<width>:<height>`。例如：取值`3:4`表示视频在播放器中播放是`宽:高`=`3:4`（注：此处取值仅为体现演示效果）。 |
|  /stripmeta/&lt;StripMeta&gt; |  A/V |  |  是否清除文件的`metadata`，1为清除，0为保留。 |
|  /h264Crf/&lt;H264Crf&gt; |  V |  |  设置h264的crf值，整数，取值范围\[18,28\]，值越小，画质更清晰。注意：不可与vb共用 |
|  /rotate/&lt;Degree&gt; |  V |  |  指定顺时针旋转的度数，可取值为`90`、`180`、`270`、`auto`，默认为不旋转。 |
|  /wmImage/&lt;EncodedRemoteImageUrl&gt; |  V |  |  水印图片的源路径，目前仅支持远程路径，需要经过`urlsafe_base64_encode`。水印具体介绍见[视频水印](https://developer.qiniu.com/dora/api/video-watermarking)。 |
|  /wmGravity/&lt;Gravity&gt; |  V |  |  视频图片水印位置，存在`/wmImage/`时生效。 |
|  /wmText/&lt;EncodedText&gt; |  V |  |  水印文本内容,需要经过`urlsafe_base64_encode`。 |
|  /wmGravityText/&lt;GravityText&gt; |  V |  |  文本位置（默认NorthEast） |
|  /wmFont/&lt;Font&gt; |  V |  |  文本字体，需要经过`urlsafe_base64_encode`，默认为黑体,注意：中文水印必须指定中文字体。 |
|  /wmFontColor/&lt;FontColor&gt; |  V |  |  水印文字颜色，需要经过`urlsafe_base64_encode`，RGB格式，可以是颜色名称（例如红色）或十六进制（例如\#FF0000），参考RGB颜色编码表，默认为黑色。 |
|  /wmFontSize&lt;FontSize&gt; |  V |  |  水印文字大小，单位: 缇，等于1/20磅，默认值0（默认大小） |
|  `/writeXing/<Xing>` |  A |  |  转码成mp3时是否写入xing header，默认1写入，写入会导致 `file`，`afinfo` 等命令识别出错误的码率。好处是在需要音频时长、帧数的时候只需要获取header。 |
|  `/an/<AudioNo>` |  A |  |  是否去除音频流，0为保留，1为去除。 默认值为0。 |
|  `/vn/<VideoNo>` |  V |  |  是否去除视频流，0为保留，1为去除。 默认值为0。 |
|  /subtitle/&lt;SubtitleURL&gt; |  V |  |  添加字幕，支持：srt 格式字幕（uft-8 编码和和 utf-8 BOM 编码）、带有字幕的 mkv 文件、embed（将原视频的字幕流嵌入目标视频）。基于 base64 编码。 |
|  `/sn/<SubtitleNo>` |  V |  |  是否去除字幕，0为保留，1为去除。默认值为0。 |
|  /hlsMethod/&lt;HLSMethod&gt; |  A/V |  |  |
|  /gop/&lt;GroupOfPictures&gt; |  V |  |  GOP参数，即视频流关键帧间的间隔帧数，取值\[0,3000\]的整数，默认为0表示采用指定视频编码格式的默认GOP值，例如libx264格式默认GOP值为250。 |

