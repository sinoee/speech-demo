# speech-demo
项目地址：https://github.com/Baidu-AIP/speech-demo

文档地址：
- 语音识别：http://ai.baidu.com/docs#/ASR-API/top
- 语音合成：http://ai.baidu.com/docs#/TTS-API/top


百度语音rest api 调用语音识别，语音合成示例

**Rest API 接口为http 访问， 任意操作系统，任意语言，只要能对baidu域名发起http请求的，均可以使用。**

百度语音合成的接口支持跨域，但是获取token的接口不支持。浏览器直接发请求的示例见：https://github.com/Baidu-AIP/SPEECH-TTS-CORS

## 简介

以JAVA PHP python C BASH 作为示例，展示rest api的调用过程，选择一个运行即可。

## 目录结构

```
+--rest-api-asr  语音识别rest api
   /--bash_shell shell脚本
   /-- java 代码 
   /-- linux_c C代码 （windows Cygwin可以运行）
   /-- php 代码
   /-- python代码
 
 +--rest-api-tts 语音合成rest api
   /--bash_shell shell脚本
   /-- java 代码 
   /-- linux_c C代码 （windows Cygwin可以运行）
   /-- php 代码
   /-- python代码
 +-- sample-files 语音识别示例音频文件
```



原型：MRCPRecog (grammar, options)

grammar ---- 语法文件，可以是一个xml文件

options  ---- 选项，具体见下面的描述

 

MRCPRecog的选项参数
Name                            Description
p ------- profile to use in mrcp.conf
i  ------- digits to allow recognition to be interrupted with (by default DTMFs are sent to the MRCP server to recognize; otherwise, if "any" or other digits are specified, recognition will be interrupted)
      输入一个数字，识别就会被打断。可以填"any"，或一个数字
 
f  ------- filename on play (if empty or not specified, no file is played)
           一个wav文件的名字，会给客户播放这个提示音。
 
t ----- recognition timeout (msec)
           语音识别的超时时间，单位毫秒，如 t=10000 表示10秒。
 
b  ------  barge-in value (no barge-in allowed=0, barge-in allowed=1)
               是否允许语音打断，填0或1
 
 
gd  ----  grammar delimiters    语法分隔符
 
ct  -----  confidence threshold (0.0 - 1.0)   
               置信度阈值（不明白什么意思）
 
sl   -----  sensitivity level (0.0 - 1.0)    灵敏度等级
sva   -----  speed versus accuracy (0.0 - 1.0)  速度和准确性
 
nb  -----  n-best list length
 
nit   -----  no input timeout (msec)  没有输入时的超时时间
 
sct  -----   speech complete timeout (msec)
 
sint  -----  speech incomplete timeout (msec)
 
dit  -----  DTMF interdigit timeout (msec)
 
dtt  -----  DTMF terminate timeout (msec)
 
dttc  -----  DTMF terminate characters  DTMF打断的字符
 
sw  ----- save waveform (true/false)
 
nac  -----  new audio channel (true/false)  新的语音通道
 
spl  ------  speech language (en-US/en-GB/etc.)  语音识别的语言，英文或者中文
 
rm  -------  recognition mode (normal/hotword)  语音识别模式，普通或者热词
 
hmaxd -----  hotword max duration (msec)  热词最大时间
 
hmind  ----- hotword min duration (msec)  热词最小时间
 
cdb  -----  clear DTMF buffer (true/false)  清除DTMF缓存
 
enm  -----   early no match (true/false)
 
iwu  -----  input waveform URI
 
mt  ----  media type  媒体类型
 
epe
exit on play error (1: terminate recognition on file play error, 0: continue even if file play fails)
播放失败时的处理方式
1---结束识别
0--- 继续识别
 
uer  ----  URI-encoded results (1: URI-encode NLMSL results, 0: do not encode)
1--- 编码成NLMSL 结果
0--- 不要编码
 
od  ----  Output (prompt) delimiters.  输出的分隔符
 
sit
Start input timers value 
(0: no, 
1: yes [start with RECOGNIZE], 
2: auto [start when prompt is finished])
启动输入计时器值
0 --- 不
1 --- 允许，从识别开始
2 ---  自动，等提示音播放完毕再开始
