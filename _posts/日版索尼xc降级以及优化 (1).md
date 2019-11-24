---
layout: post
title:  "日版索尼xc降级以及优化"
categories: 教程
tags: 索尼 教程 优化
author: Small_tail
---

# 前言  
本来上周是想摸一篇XC的开箱的，不过怠惰了XP正好有人问XC的调教，我这边就把我的调教过程分享一下得了  








## 系统的选择
日版和港版的XC都支持6.0·7.0·8.0的安卓系统，虽然有人说8.0和7.0耗电其实差不多，**耗电大户其实是移动数据**（这个倒是没问题）。  
这里还是仁者见仁智者见智吧，8.0支持Poweramp的Hi-Res输出格式（虽然不是sony hi-res的芯片），而且底噪要比7.0小，7.0的话听说游戏性能方面要更胜一筹，续航的话7.0能比8.0多个30分钟左右（同样是4G+的情况，亮屏时间一个3：40一个4：10）所以还是看自己的需求吧。  
如果你是8.0要降级的话，直接使用索尼的[`Xperia Companion`](https://www.sonystyle.com.cn/minisite/cross/app/xperia-companion.htm)选择软件修复即可。  
如果你要升级，也同样可以使用这个软件qwq  
P.S:下载服务器是国外服务器，所以很慢，你可以在这期间冲一发或者使用`SSR`/cy
## 手机的调教
日本系统自带了许多用不上的软件，如果你可以解锁的话那可以直接Root卸载。如果你不能解锁的话也可以通过ADB对当前用户进行卸载（设置里有多用户的选项，应该能懂吧）。如果恢复出厂的话，那么还得再删一遍。
1. 点击[此处](https://developer.android.google.cn/studio/releases/platform-tools.html)下载**独立的 Android SDK 平台工具软件包**
2. 解压到任意路径（~~比如我最爱的桌面~~）后，打开文件夹，对空白处`SHIFT`+`右键`，选择`在此处打开PowerShell窗口`
3. 连接手机
4. 复制下面的代码即可卸载部分预装软件
5. 你可以将代码后的包名改成自己需要卸载的包名，`-k`是保留用户数据的意思，自己卸载的话可以去掉。这里丢一个[一个老哥的讲解](https://www.coolapk.com/feed/13556696?shareKey=ZDBmZWVjODk2N2UzNWRkOWVlYWU~&shareUid=642591&shareFrom=com.coolapk.market_9.6.3)

当然，你也可以用这个**独立的 Android SDK 平台工具软件包**干些别的事情，这就得看你自己了，如果用不上的话直接删了就行。另外晨钟酱的工具箱也能冻结和卸载软件（虽然感觉卸不干净，另外那些为什么只是冻结不是卸载）。不过真正的大人当然是选择全都要啊。两边都跑一遍然后重启手机。晨钟酱这个工具箱留着，优化的时候可以用到。下载地址：[👁](https://www.coolapk.com/feed/11397755?shareKey=MGVjNTMwNjU0MzkxNWRkOWVlYzA~&shareUid=642591&shareFrom=com.coolapk.market_9.6.3)其实只是动态地址，为了尊重大佬还是去捧个厂吧qwq，实在不想下酷安的话也可以去这[👁](https://sn9.us/file/22501768-406593116 )另一双神秘的眼[👀](6666)

<details>
  <summary><mark><font color=darkred>点击查看代码</font></mark></summary>
  <pre><code>  
.\adb devices

.\adb shell

pm uninstall -k --user 0 jp.co.fsi.fs1seg
pm uninstall -k --user 0 jp.dmapnavi.navi02
pm uninstall -k --user 0 com.sony.drbd.reader.other.jp
pm uninstall -k --user 0 com.rsupport.rs.activity.ntt
pm uninstall -k --user 0 com.mcafee.vsm_android_dcm
pm uninstall -k --user 0 com.nttdocomo.android.areamail
pm uninstall -k --user 0 com.nttdocomo.android.bugreport
pm uninstall -k --user 0 com.nttdocomo.android.atf
pm uninstall -k --user 0 jp.co.nttdocomo.dbook
pm uninstall -k --user 0 com.nttdocomo.android.accountwipe
pm uninstall -k --user 0 com.nttdocomo.android.pf.dcmippushaggregator
pm uninstall -k --user 0 com.ntt.docomo.android.pf.dcmwappush
pm uninstall -k --user 0 jp.co.omronsoft.android.decoemojimanager_docomo
pm uninstall -k --user 0 jp.co.nttdocomo.saigaiban
pm uninstall -k --user 0 com.nttdocomo.android.store
pm uninstall -k --user 0 com.nttdocomo.android.applicationmanager
pm uninstall -k --user 0 com.nttdocomo.android.applicationmanager.RecommendActivity
pm uninstall -k --user 0 com.nttdocomo.android.accountauthenticator
pm uninstall -k --user 0 com.nttdocomo.android.sdcardbackup
pm uninstall -k --user 0 com.nttdocomo.android.sdcardbackup.view.LaunchActivity
pm uninstall -k --user 0 com.nttdocomo.android.cloudset
pm uninstall -k --user 0 com.nttdocomo.android.initialization
pm uninstall -k --user 0 com.nttdocomo.android.lac
pm uninstall -k --user 0 com.nttdocomo.android.dhome
pm uninstall -k --user 0 com.nextbit.app
pm uninstall -k --user 0 jp.co.nttdocomo.lcsapp
pm uninstall -k --user 0 jp.co.nttdocomo.lcsappsub
pm uninstall -k --user 0 jp.co.nttdocomo.carriermail
pm uninstall -k --user 0 com.android.contacts
pm uninstall -k --user 0 com.nttdocomo.android.docomoset
pm uninstall -k --user 0 com.nttdocomo.android.dpoint
pm uninstall -k --user 0 com.google.android.apps.docs
pm uninstall -k --user 0 com.nttdocomo.android.idmanager
pm uninstall -k --user 0 com.nttdocomo.android.dmenu2
pm uninstall -k --user 0 com.nttdocomo.android.docomo_market.ui.StartupActivity
pm uninstall -k --user 0 com.sonymobile.pobox.skin.easy
pm uninstall -k --user 0 com.google.android.apps.photos
pm uninstall -k --user 0 com.google.android.videos
pm uninstall -k --user 0 com.google.android.music
pm uninstall -k --user 0 com.sonymobile.pobox.skin.gummi
pm uninstall -k --user 0 com.ipg.gguide.dcm_app.android
pm uninstall -k --user 0 com.nttdocomo.android.voicetranslation
pm uninstall -k --user 0 com.google.android.talk
pm uninstall -k --user 0 com.google.android.talk.SigningInActivity
pm uninstall -k --user 0 jp.id_credit_sp.android
pm uninstall -k --user 0 com.instagram.android
pm uninstall -k --user 0 com.somc.so02j.manual
pm uninstall -k --user 0 com.nttdocomo.android.iconcier
pm uninstall -k --user 0 com.nttdocomo.android.iconcier_contents
pm uninstall -k --user 0 com.amazon.kindle
pm uninstall -k --user 0 jp.co.lawson.activity
pm uninstall -k --user 0 com.sonymobile.lifelog
pm uninstall -k --user 0 jp.co.mcdonalds.android
pm uninstall -k --user 0 com.nttdocomo.android.mediaplayer
pm uninstall -k --user 0 com.facebook.orca
pm uninstall -k --user 0 com.nttdocomo.android.voiceeditor
pm uninstall -k --user 0 com.sony.nfx.app.sfrc
pm uninstall -k --user 0 com.nttdocomo.osaifu.tsmproxy
pm uninstall -k --user 0 com.sonyericsson.updatecenter
pm uninstall -k --user 0 com.sonymobile.androidapp.cameraaddon.stickercreator
pm uninstall -k --user 0 com.android.dialer
pm uninstall -k --user 0 com.nttdocomo.android.socialphonebook
pm uninstall -k --user 0 com.nttdocomo.android.wipe
pm uninstall -k --user 0 com.rsupport.rsperm.ntt
pm uninstall -k --user 0 com.nttdocomo.android.rwpushcontroller
pm uninstall -k --user 0 com.nttdocomo.android.schedulememo
pm uninstall -k --user 0 com.nttdocomo.android.screenlockservice
pm uninstall -k --user 0 com.nttdocomo.android.settings.lac
pm uninstall -k --user 0 com.google.android.apps.docs.editors.slides
pm uninstall -k --user 0 com.google.android.apps.docs.editors.sheets
pm uninstall -k --user 0 com.nttdocomo.android.phonemotion
pm uninstall -k --user 0 com.nttdocomo.android.toruca
pm uninstall -k --user 0 com.twitter.android
pm uninstall -k --user 0 com.sonymobile.pobox.skin.wood
pm uninstall -k --user 0 com.google.android.youtube
pm uninstall -k --user 0 com.sonyericsson.androidapp.sehome
pm uninstall -k --user 0 com.felicanetworks.mfm.main
pm uninstall -k --user 0 com.nttdocomo.android.devicehelp
pm uninstall -k --user 0 com.felicanetworks.mfm
pm uninstall -k --user 0 com.nttdocomo.android.mascot
pm uninstall -k --user 0 com.nttdocomo.android.databackup
pm uninstall -k --user 0 com.nttdocomo.android.cloudstorageservice
pm uninstall -k --user 0 com.nttdocomo.android.dcmvoicerecognition
pm uninstall -k --user 0 com.nttdocomo.android.photocollection
pm uninstall -k --user 0 com.nttdocomo.android.moneyrecord
pm uninstall -k --user 0 com.facebook.system
pm uninstall -k --user 0 com.sony.tvsideview.videoph
pm uninstall -k --user 0 com.sonyericsson.textinput.chinese
pm uninstall -k --user 0 com.sonyericsson.warrantytime
pm uninstall -k --user 0 com.sonymobile.enterprise.service
pm uninstall -k --user 0 com.sonymobile.gettoknowit
pm uninstall -k --user 0 com.sonymobile.moviecreator
pm uninstall -k --user 0 com.sonymobile.moviecreator.rmm
pm uninstall -k --user 0 com.sonymobile.music.googlelyricsplugin
pm uninstall -k --user 0 com.sonymobile.music.wikipediaplugin
pm uninstall -k --user 0 com.sonymobile.mx.android
pm uninstall -k --user 0 com.sonymobile.sketch
pm uninstall -k --user 0 com.sonymobile.support
pm uninstall -k --user 0 com.facebook.appmanager
pm uninstall -k --user 0 com.facebook.katana
pm uninstall -k --user 0 com.spotify.music
pm uninstall -k --user 0 com.sonymobile.getmore.client
pm uninstall -k --user 0 com.sony.tvsideview.phone
pm uninstall -k --user 0 com.sonyericsson.trackid
pm uninstall -k --user 0 com.amazon.mShop.android.shopping
pm uninstall -k --user 0 com.scee.psxandroid
pm uninstall -k --user 0 com.sonymobile.entrance
pm uninstall -k --user 0 com.s.antivirus
pm uninstall -k --user 0 com.sonyericsson.xhs
pm uninstall -k --user 0 com.sonymobile.xperialounge.services
pm uninstall -k --user 0 com.sonymobile.xperiaservices
pm uninstall -k --user 0 com.sonymobile.music.youtubekaraokeplugin
pm uninstall -k --user 0 com.sonymobile.tvout.wifidisplay
pm uninstall -k --user 0 com.sonymobile.music.youtubeplugin
pm uninstall -k --user 0 com.sonyericsson.trackid.res.overlay_305
pm uninstall -k --user 0 com.mobisystems.fileman
pm uninstall --user 0 com.sonymobile.assist 
pm uninstall --user 0 com.google.android.googlequicksearchbox
pm uninstall --user 0 com.google.android.calendar
pm uninstall --user 0 com.google.android.apps.maps
pm uninstall --user 0 com.google.android.apps.photos
pm uninstall --user 0 com.google.android.apps.docs
pm uninstall --user 0 com.google.android.gm
pm uninstall --user 0 com.google.android.videos
pm uninstall --user 0 com.sonymobile.music.youtubeplugin
pm uninstall --user 0 com.sonymobile.music.youtubekaraokeplugin
pm uninstall --user 0 com.sonymobile.music.youtubeplugin
pm uninstall --user 0 com.google.android.youtube
pm uninstall --user 0 com.android.vending
pm uninstall --user 0 com.google.android.apps.docs.editors.docs
pm uninstall --user 0 com.sonymobile.assist 
pm uninstall --user 0 com.google.android.googlequicksearchbox
pm uninstall --user 0 com.google.android.calendar
pm uninstall --user 0 com.google.android.apps.maps
pm uninstall --user 0 com.google.android.apps.photos
pm uninstall --user 0 com.google.android.apps.docs
pm uninstall --user 0 com.google.android.gm
pm uninstall --user 0 com.google.android.videos
pm uninstall --user 0 com.sonymobile.music.youtubeplugin
pm uninstall --user 0 com.sonymobile.music.youtubekaraokeplugin
pm uninstall --user 0 com.sonymobile.music.youtubeplugin
pm uninstall --user 0 com.google.android.youtube
pm uninstall --user 0 com.android.vending
pm uninstall --user 0 com.google.android.apps.docs.editors.docs
pm uninstall --user 0 com.facebook.katana
pm uninstall --user 0 com.google.android.tts
pm uninstall --user 0 com.touchtype.swiftkey
exit

.\adb reboot


  </code></pre>
</details>
没有卸载干净的软件怎么办呢？（暗示谷歌套件）考虑到谷歌套件可能要用到的情况，这里推荐优化方案为“**小黑屋+黑域**”  
小黑屋激活起来要比冰箱简单（插卡用户选择`麦克韦斯妖模式`，没插卡的直接激活管理员模式（冰箱默认就是管理员模式，插卡用户表示难受）），而且可以冻结的应用要比冰箱多（免费版有限制了还行）  
黑域的话也是能一键激活，用来日常压后台没问题。  
激活的话推荐电脑端使用[`秋之盒`](https://www.atmb.top/),这里对一些ADB代码进行了封装，简便快捷，懒狗必备！  
小黑屋的话酷安直接下，黑域我用的社区版给大家分享一下，还蛮不错的。[👁](https://github.com/Small-tailqwq/img/raw/master/%E9%BB%91%E5%9F%9F%20%E7%A4%BE%E5%8C%BA%E7%89%88.apk)(Github真方便啊) 
P.S：使用秋之盒激活后有一定几率出现掉激活的情况，记得激活完把线拔了试试看，失效的话重复激活即可。  

## 事后的优化  
在小黑屋和黑域的加持下，3G运存还是够日常使用的。不过这个屏幕是不是有点小？下面的~~三大金刚~~导航栏是不是显得有点碍事？（这个优化是可选的，因为部分人还是喜欢三大...导航栏）  
1. 先下载一个[流体手势导航](https://github.com/Small-tailqwq/img/raw/master/%E6%B5%81%E4%BD%93%E6%89%8B%E5%8A%BF%E5%AF%BC%E8%88%AA.apk)（这玩意真的还不错，就是横屏状态下有**BUG**Xp）  
2. 把他的各种各样的权限激活啥的，左右滑动可以生效时使用晨钟酱的工具箱把导航栏隐藏就行了。
3. 开始享受全面屏手势的快感吧（虽然并不是全面屏XP  

## 对这个手机的感想
我这个是日版的，带气密但是不是天选之子解不了BL锁，不然就能享受双倍的快乐了。（白学禁止）    
下水的话试了几次，完全没事，擦干后指纹秒接，真的舒服。  
相机中规中矩，索尼一贯的涂抹。但也不是不能看。  
续航还行，假如你是把小说或者漫画下载到手机里开飞行模式看的话，亮屏10小时都不虚！  
外放还行，音量不算太大但没有明显破音。双扬声器说到底还是有音量差异的。  
指纹不能用于微信和支付宝（国内的傻逼机制），有汗就难受了，没汗的话还是很不错的（参考ipone6s）  
机身太几把厚了，跟个充电宝一样...屏幕又小，不过可以立起来是个加分项。  
**SONY**四个字母，一个70，手机其实是送的Xp  
> # 索尼大法好

最后丢一些我这台的照片吧~~~  
（ipone6s瞎拍的，~~苹果这拍照我真的玩不来~~）
![](https://raw.githubusercontent.com/Small-tailqwq/img/master/blog/1124/IMG_0204.JPG)
![](https://raw.githubusercontent.com/Small-tailqwq/img/master/blog/1124/IMG_0205.JPG)
![](https://raw.githubusercontent.com/Small-tailqwq/img/master/blog/1124/IMG_0206.JPG)
![](https://raw.githubusercontent.com/Small-tailqwq/img/master/blog/1124/IMG_0207.JPG)
