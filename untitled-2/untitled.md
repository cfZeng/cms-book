---
description: >-
  音视频切片接口用于支持HTTP Live Streaming播放。HTTP Live Streaming 是由 Apple 提出的基于 HTTP
  的流媒体传输协议。它将一整个音频、视频流切割成可由 HTTP 下载的一个个小的音视频流，并生成一个 M3U8 播放列表，客户端只需要获取资源的 M3U8
  播放列表即可播放音视频。以下用 HLS 代指 HTTP Live Streaming。
---

# 音视频切片

## 使用方法 {#1}

 命令可以根据需要自定义，如：

```text
avthumb/m3u8/noDomain/1/vb/500k/t/10

```

```text
fops = avthumb/m3u8/noDomain/1/vb/500k/t/10

```

{% api-method method="post" host="" path="{bucket}/{objectId}/m3u8/avthumb" %}
{% api-method-summary %}
avthumb
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

## 接口规格 {#2}

```text
avthumb/m3u8/noDomain/<NoDomain>
            /domain/<Domain>
            /segtime/<SegSeconds>
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
            /stripmeta/<StripMeta>
            /rotate/<Degree>
            /hlsKey/<HLSKey>
            /hlsKeyType/<HLSKeyType>
            /hlsKeyUrl/<HLSKeyUrl>
            /pattern/<Pattern>

```

参数名称

| 类别 | 必填 | 说明 |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `/noDomain/<NoDomain>` | A/V | 是 | 取值 0 或 1，默认为 0，**推荐取值为 1**。表示切片索引中的切片列表，是否使用相对地址，设置为 0 则使用绝对地址，设置为 1 则使用相对地址。 |
| `/domain/<Domain>` | A/V |  | 用户指定切片中ts文件的域名。 **注意：**域名需要urlbase64编码，且不能带http；该参数不能和noDomain/1共同使用。 |
| `/segtime/<SegSeconds>` | A/V |  | 用于自定义每一小段音/视频流的播放时长，单位为秒，取值范围为5-120秒，默认值为10秒。 |
| `/ab/<BitRate>` | A |  | 静态码率 \(CBR\)，单位为比特每秒 \(bit/s\)，常用的码率有：64k,128k,192k,256k,320k等。 |
| `/aq/<AudioQuality>` | A |  | 动态码率 \(VBR\)，取值范围为0-9，值越小码率越高。不能与静态码率参数共用。 |
| `/ar/<SamplingRate>` | A |  | 音频采样频率，单位为赫兹 \(Hz\)，常用的采样频率有：8000,12050,22050,44100等。 |
| `/r/<FrameRate>` | V |  | 视频帧率，每秒显示的帧数，单位为赫兹 \(Hz\)，常用的帧率有：24,25,30等，一般用默认值。 |
| `/vb/<VideoBitRate>` | V |  | 视频比特率，单位为比特每秒 \(bit/s\)，常用的视频比特率有：128k,1.25m,5m等。 |
| `/vcodec/<VideoCodec>` | V |  | 视频编码方案，支持的方案有：libx264,libvpx,libtheora,libxvid等，默认为libx264。 |
| `/acodec/<AudioCodec>` | A |  | 音频编码方案，支持的方案有：libmp3lame,libfaac,libvorbis等。 |
| `/scodec/<SubtitleCodec>` | V |  | 字幕编码方案，支持的方案有：mov\_text。该参数仅用于修改带字幕视频的字幕编码。 |
| `/subtitle/<SubtitleURL>` | V |  | 添加字幕，支持：srt格式字幕 \(uft-8编码和和utf-8 BOM编码\)，带有字幕的mkv文件，embed \(将原视频的字幕流嵌入目标视频\)。基于base64编码。 |
| `/ss/<SeekStart>` | V |  | 指定视频截取的开始时间，单位为秒，支持精确到毫秒，例如3.345s。用于视频截取，从一段视频中截取一段视频。 |
| `/t/<Duration>` | V |  | 指定视频截取的长度，单位为秒，支持精确到毫秒，例如1.500s。用于视频截取，从一段视频中截取一段视频。 |
| `/s/<Resolution>` | V |  | 指定视频分辨率，格式为：`<width>x<height>`，或者预定义值。 |
| `/stripmeta/<StripMeta>` | A/V |  | 是否清除文件的metadata，1为清除，0为保留。 |
| `/rotate/<Degree>` | V |  | 指定顺时针旋转的度数，取值可为：90,180,270,auto，默认为不旋转。 |
| `/hlsKey/<HLSKey>` | A/V |  | AES128加密视频的秘钥，必须是16个字节。 |
| `/hlsKeyType/<HLSKeyType>` | A/V |  | 密钥传递给我们的方式，0或不填。1.x\(1.0, 1.1, ...\)：见下面详细解释。 |
| `/hlsKeyUrl/<HLSKeyUrl>` | A/V |  | 密钥的访问url |
| `/pattern/<Pattern>` | A/V |  | 为各音视频流ts文件自定义命名。 因为一整段音视频流音视频切片后会生成一个M3U8播放列表和多个默认命名的音视频流ts文件。示例：_avthumb/m3u8/noDomain/1/pattern/eGlhb3hpYW8kKGNvdW50KQ==_，其中_eGlhb3hpYW8kKGNvdW50KQ==_是自定义ts文件名，如：qiniu$\(count\)的[URL安全的Base64编码](https://developer.qiniu.com/kodo/manual/appendix#urlsafe-base64)，其中$\(count\)是必须存在的六位占位符数字串，qiniu可以自己定义。最后得到类似：qiniu000000,qiniu000001,……,qiniu000006命名的ts文件。 |

