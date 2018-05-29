---
description: 实时音视频转码(avvod)用于对已经上传到CMS的音频、视频，在终端播放时按照指定参数进行实时转码。
---

# 实时音视频转码

## 接口规格 {#1}

**注意：**接口规格不含任何空格与换行符，下列内容经过格式化以便阅读。

```text
avvod/<Format> 
     /ab/<BitRate>
     /aq/<AudioQuelity>
     /ar/<SamlingRate>
     /r/<FrameRate>
     /vb/<VideoBitRate>
     /vcodec/<VideoCodec>
     /acodec/<AudioCodec>
     /s/<Resolution>
     /autosave/<AutoSave>

```



|  参数名称 |  类别 |  必填 |  说明 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `<Format>` | A/V | 是 | 目前只支持输出m3u8流（HLS协议） |
| `/ab/<BitRate>` | A | 否 | 静态码率（CBR），单位：比特每秒（bit/s），常用码率：64k，128k，192k，256k，320k等 |
| `/aq/<AudioQuality>` | A | 否 | 动态码率（VBR），取值范围为0-500，mp3\(0-9\),aac\(10-500\)。不能与上述静态码率参数共用 |
| `/ar/<SamplingRate>` | A | 否 | 音频采样频率，单位：赫兹（Hz），常用采样频率：8000，12000，22050，44100等 |
| `/r/<FrameRate>` | V | 否 | 视频帧率，每秒显示的帧数，单位：赫兹（Hz），常用帧率：24，25，30等，一般用默认值 |
| `/vb/<VideoBitRate>` | V | 否 | 视频比特率，单位：比特每秒 \(bit/s\)，常用视频码率有：128k、1.25m、5m等。若指定码率大于原视频码率，则使用原视频码率进行转码 |
| `/vcodec/<VideoCodec>` | V | 否 | 视频编码方案，支持方案：libx264，libvpx，libtheora，libxvid等，默认采用libx264 |
| `/acodec/<AudioCodec>` | A | 否 | 音频编码方案，支持方案：libmp3lame，libfaac等，默认采用libfaac |
| `/s/<Resolution>` | V | 否 | 指定视频分辨率，格式为\x\或者预定义值，width取值范围20-1920，height取值范围20-1080，奇数自动减一 |
| `/autosave/<AutoSave>` | A/V | 否 | 自动持久化存储，转码后所有文件存储在源视频同一bucket内，取值0（非持久化）或1（持久化存储），默认为0 |

