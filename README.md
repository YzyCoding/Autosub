# Autosub

[toc]

## 1. 介绍

Autosub是一个用于自动语音识别和字幕生成的实用程序。它以视频或音频文件为输入，执行语音活动检测以找到语音区域，向Google Web Speech API发出并行请求以生成这些区域的转录，（可选）将其翻译为其他语言，最后保存结果磁盘字幕。它支持多种输入和输出语言，并且当前可以产生SRT格式或JSON字幕。

## 2. 准备

1. 科学上网。当前购买的香港服务器，保证稳定性

2. [申请 Google Translate API Key](https://console.cloud.google.com/)

   > 需要绑定一张 VISA信用卡

   

   ![选择APIs](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjw5hefot9j311z0u0gnr.jpg)

   ![找到Tranalation API](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjw5lm2qpaj31eu0fcdg4.jpg)

   ![申请试用](https://tva1.sinaimg.cn/large/007S8ZIlly1gjw5o7x1mrj31ez0u0q4l.jpg)

   ![需要绑定信用卡](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjw5q4xwnmj30u00xndgx.jpg)

   ![创建项目](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjw5sxe4scj31ms0hc751.jpg)

   ![创建项目2](https://tva1.sinaimg.cn/large/007S8ZIlly1gjw5yyoprxj30xi0poaar.jpg)

   ![申请KEY](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjw66ziyhnj31so0tgmyu.jpg)

    

   已成功 申请 KEY ，可以调用如下URL测试 key是否有效

   ```python
   https://www.googleapis.com/language/translate/v2?key=you-key&source=en&target=de&q=Hello%20world
     
     {
     "data": {
       "translations": [
         {
           "translatedText": "Hallo Welt"
         }
       ]
     }
   }  
   ```

   

## 3. 安装

1. Install [ffmpeg](https://www.ffmpeg.org/)

   ```python
   1. yum install ffmpeg -y 安装ffmpeg
   2. ffmpeg 检查是否安装成功
   ```

   ![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjw74tqv9aj30za0a374o.jpg)



2. Run pip install autosub

   ```python
   1. python -V 查看版本
   2. pip install autosub 安装
   3. pip list 查看安装列表
   4. autosub -h 检查是否安装成功
   ```

​		![1](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjw6vj10twj30i60esmxc.jpg)

​		![2](https://tva1.sinaimg.cn/large/007S8ZIlgy1gjw6tq8s4tj30g70mwgm1.jpg)

​		![3](https://tva1.sinaimg.cn/large/007S8ZIlly1gjw6r1ivlyj30id0c8t8w.jpg)



## 4. 运行

* 生成中文字幕

  

  ```python
  autosub -S zh-CN -D zh-CN 1-1.mp4
  ```

  ![image.png](https://upload-images.jianshu.io/upload_images/9391038-f91d7a92995f469a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)![image2.png](https://upload-images.jianshu.io/upload_images/9391038-42e837e0a989ce94.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

  

* 中译英

  

  ```python
  autosub -S zh-CN -D en -K xxxxxxxxxxxx 1-1.mp4
  ```

  ![image.png](https://upload-images.jianshu.io/upload_images/9391038-34dd0c5ad2088b54.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

​		![image.png](https://upload-images.jianshu.io/upload_images/9391038-d997306376609c07.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



* 帮助

  

  ```python
  $ autosub -h
  usage: autosub [-h] [-C CONCURRENCY] [-o OUTPUT] [-F FORMAT] [-S SRC_LANGUAGE]
                 [-D DST_LANGUAGE] [-K API_KEY] [--list-formats]
                 [--list-languages]
                 [source_path]
  
  positional arguments:
    source_path           Path to the video or audio file to subtitle
  
  optional arguments:
    -h, --help            show this help message and exit
    -C CONCURRENCY, --concurrency CONCURRENCY
                          Number of concurrent API requests to make
    -o OUTPUT, --output OUTPUT
                          Output path for subtitles (by default, subtitles are
                          saved in the same directory and name as the source
                          path)
    -F FORMAT, --format FORMAT
                          Destination subtitle format
    -S SRC_LANGUAGE, --src-language SRC_LANGUAGE
                          Language spoken in source file
    -D DST_LANGUAGE, --dst-language DST_LANGUAGE
                          Desired language for the subtitles
    -K API_KEY, --api-key API_KEY
                          The Google Translate API key to be used. (Required for
                          subtitle translation)
    --list-formats        List all available subtitle formats
    --list-languages      List all available source/destination languages
  ```

  

* 支持语言列表

  

  ````python
  [root@izj6c46jnvhw9ajs6itxowz ~]# autosub --list-languages
  List of all languages:
  af	Afrikaans
  ar	Arabic
  az	Azerbaijani
  be	Belarusian
  bg	Bulgarian
  bn	Bengali
  bs	Bosnian
  ca	Catalan
  ceb	Cebuano
  cs	Czech
  cy	Welsh
  da	Danish
  de	German
  el	Greek
  en	English
  eo	Esperanto
  es	Spanish
  et	Estonian
  eu	Basque
  fa	Persian
  fi	Finnish
  fr	French
  ga	Irish
  gl	Galician
  gu	Gujarati
  ha	Hausa
  hi	Hindi
  hmn	Hmong
  hr	Croatian
  ht	Haitian Creole
  hu	Hungarian
  hy	Armenian
  id	Indonesian
  ig	Igbo
  is	Icelandic
  it	Italian
  iw	Hebrew
  ja	Japanese
  jw	Javanese
  ka	Georgian
  kk	Kazakh
  km	Khmer
  kn	Kannada
  ko	Korean
  la	Latin
  lo	Lao
  lt	Lithuanian
  lv	Latvian
  mg	Malagasy
  mi	Maori
  mk	Macedonian
  ml	Malayalam
  mn	Mongolian
  mr	Marathi
  ms	Malay
  mt	Maltese
  my	Myanmar (Burmese)
  ne	Nepali
  nl	Dutch
  no	Norwegian
  ny	Chichewa
  pa	Punjabi
  pl	Polish
  pt	Portuguese
  ro	Romanian
  ru	Russian
  si	Sinhala
  sk	Slovak
  sl	Slovenian
  so	Somali
  sq	Albanian
  sr	Serbian
  st	Sesotho
  su	Sudanese
  sv	Swedish
  sw	Swahili
  ta	Tamil
  te	Telugu
  tg	Tajik
  th	Thai
  tl	Filipino
  tr	Turkish
  uk	Ukrainian
  ur	Urdu
  uz	Uzbek
  vi	Vietnamese
  yi	Yiddish
  yo	Yoruba
  zh-CN	Chinese (Simplified)
  zh-TW	Chinese (Traditional)
  zu	Zulu
  ````



## 5. 调优

* 对比原视频生成中文SRT字幕来看，语音识别不是很准，可能需要对原视频降噪处理、ffmpeg调优、人工调整。

* 中文字幕不准导致英文翻译也不准，可以选择手改SRT字幕后再进行翻译。[Google文档翻译](https://translate.google.cn/#view=home&op=translate&sl=zh-CN&tl=en)

* 也可对比 [BingLingGroup-autosub](https://github.com/BingLingGroup/autosub) 看看效果，升级autosub，python版本

* 其他方案

  

## 6. 问题

>  第一遍MAC安装运行时，主要问题是代理不稳定导致请求超时，后面上了香港服务器一遍打通。

小问题：

* [srt文件 0kb](https://github.com/agermanidis/autosub/issues/100)

* autosub -h 找不到，需要`sudo`安装

* 代理网络问题

  

## 参考

[autosub](https://github.com/agermanidis/autosub)

[Google Translate文档](https://cloud.google.com/translate/docs)

[BingLingGroup-autosub](https://github.com/BingLingGroup/autosub)

