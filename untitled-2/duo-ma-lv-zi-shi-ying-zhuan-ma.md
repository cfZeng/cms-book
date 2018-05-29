---
description: 多码率自适应转码(adapt)用于对已经上传到CMS的视频转码成包含多种码率的HLS视频流。以便能随着终端网络带宽的变化动态选择适应的码率播放。
---

# 多码率自适应转码

## 接口规格 {#1}

**注意：**接口规格不含任何空格与换行符，下列内容经过格式化以便阅读。

```text
      adapt/<Format>
           /envBandWidth/<EnvBandWidth>
           /multiAb/<MultiAb>
           /multiResolution/<MultiResolution>
           /multiVb/<MultiVb>
           /multiPrefix/<MultiPrefix> 
           /vb/<VideoBitrate>
           /ab/<AudioBitrate>
           /resolution/<Resolution>
           /hlstime/<HlsTime>

```



| 类别 参数名称 |  类别 |  必填 |  说明 |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `<Format>` | V | 是 | 目前只支持m3u8，后续考虑支持dash等 |  |
| `/envBandWidth/<EnvBandWidth>` | V | 是 | 不同码流切换的带宽标准，采用符号`,`分隔多个网络带宽，个数范围\[2,5\]，取值范围\[50000,30000000\]，单位是b/s。注：个数与存在的multi参数值个数需要保持一致，建议与设置的码率值接近，带宽值采用升序方式。 |  |
| `/multiAb/<MultiAb>` | V | 否 | 与ab参数不共存，单位：比特每秒（bit/s），采用符号`,`分隔多个音频码率，个数范围\[2,5\]，例如64k,128k,256k。注：码率个数与其他存在的multi参数值个数需要保持一致，魔法变量$\(origin\)表示原音频码率。 |  |
| `/multiVb/<MultiVb>` | V | 否 | 与vb参数不共存，单位：比特每秒（bit/s），采用符号`,`分隔多个视频码率，个数范围\[2,5\]，例如128k,600k,1.25m。注：码率个数与其他存在的multi参数值个数需要保持一致，魔法变量$\(origin\)表示原视频码率。 |  |
| `/multiResolution/<MultiResolution>` | V | 否 | 与resolution参数不共存，分辨率格式为 w:h ，w取值范围\[20,3840\]，h取值范围\[20,2160\]，采用符号`,`分隔多个视频分辨率，个数范围\[2,5\]，例如320:240,640:480,1080:720。注：会改变DAR，分辨率个数与其他存在的multi参数值个数需要保持一致，魔法变量$\(origin\)表示原视频分辨率。 |  |
| `/multiPrefix/<MultiPrefix>` | V | 否 | 设置文件内的m3u8名称，同时该名称作为子m3u8的所有ts文件名的前缀。采用字符`,`分隔多个prefix，示例：/multiPrefix/cWluaXUtYQ==,cWluaXUtYg==，其中cWluaXUtYQ==是定义的第一个m3u8文件的前缀，是qiniu-a的URL安全的Base64编码，cWluaXUtYg==是定义的第二个m3u8文件的前缀，是qiniu-b的URL安全的Base64编码，每个子m3u8文件中的ts名称为`前缀名称-$(count).ts`，其中$\(count\)是六位占位符数字串，最后得到的结果中会有两个子m3u8，名称为qiniu-a.m3u8 \(内部ts为qiniu-a\_000000.ts,qiniu-a\_000001.ts...\)和 qiniu-b.m3u8\(内部ts为qiniu-b\_000000.ts,qiniu-b\_000001.ts...\)。 |  |
| `/vb/<VideoBitRate>` | V | 否 | 视频比特率，单位：比特每秒（bit/s），常用视频比特率：128k, 1.25m, 5m 等。 |  |
| `/ab/<AudioBitRate>` | V | 否 | 单位：比特每秒（bit/s），常用码率：320k, 256k, 192k, 128k, 64k 等。 |  |
| `/resolution/<Resolution>` | V | 否 | 指定视频分辨率，格式为 w:h 或者预定义值，w取值范围\[20,3840\]，h取值范围\[20,2160\]。 |  |
| `/hlstime/<HlsTime>` | V | 否 | 用于 HLS 自定义每一小段音/视频流的播放时间长度，取值范围为: 10 - 60 （秒），默认值为 10（单位:秒）。 |  |

