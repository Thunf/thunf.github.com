---
title: 从策划到传播 - 记趣店IPO快闪H5开发全过程
toc: true
tags:
  - H5
thumbnail: //img003.qufenqi.com/products/99/92/9992ff0d94a9aed7d83755f892ccf2a8.png
date: 2017-10-20 18:50:35
categories:
photo:
---


2017年10月18号，趣店集团在纽交所上市！为此，趣店QUX品牌设计组协同趣店FED大前端团队准备了一个小小的H5，为这个不平凡的一天呐喊助威。

<!-- more -->

<img src="//img003.qufenqi.com/products/37/fe/37fe01124bc702db9b4c33f1b06c5ba8.gif" style="max-width:125px;display: inline-block;"> <img src="//img002.qufenqi.com/products/16/93/16935e4337baa9c4278914aa030843d1.gif" style="max-width:125px;display: inline-block;"> <img src="//img003.qufenqi.com/products/05/35/053569cd91662c88799873879c162734.gif" style="max-width:125px;display: inline-block;"> <img src="//img003.qufenqi.com/products/5c/f7/5cf7e4052579e65d327232b3c19c18dd.gif" style="max-width:125px;display: inline-block;">

[趣店集团纽交所上市！我了个趣，真有你的！][url_h5_ipo] 你转发了么？

## 活动背景

2017年10月18号，在全体国人瞩目的大会之际，也是趣店人里程碑时刻：趣店集团实现了三年前许下的愿望 —— **在纽交所上市**

趣店QUX品牌设计组与FED大前端团队的小伙伴，协力完成了本次快闪H5传播的文案策划、视觉创作、动画开发直至上线传播，自项目确定到H5落地，主要参与者两人（UI+FE）耗费不到2周时间，完成了从无到有的首次实践。


## 文案策划

说到文案策划，由于上线时间没法商榷，而且大家都在忙各自项目，并没有可以跟进的小伙伴，只好临阵发挥了。

首现在内容主体上，确认了基本内容，主体就是官方的公司简介+成长历程，调性主打有趣好(嘚)玩(瑟)，并适当引入一些当季的新鲜~~蔬菜~~梗。当然最后也总结了一些边(shan)界(jian)条件：

- 将具体数字改为描述
    - 比如30、100等数字，改成好多、许多、很多很多
- 删减与钱相关的文案
    - 比如交易额、销售额等文案，只展示普遍理解的交易额（也显得比较有钱）
- 其他过于浮(zhuang)夸(bi)的文案等等...



## 视觉创作

### 效果选型

由于是第一次做这种**内容型**的H5项目，所以一开始便是寻找灵感，前前后后收集了近几年各种内容型的H5页面，下面放一些非常有个性的页面，以及个人认为值得学习的点：

1. [红楼梦 - 保利剧院][url_h5_1]：一镜到底，适合内容导向、可叙事可故事
2. [液体主义展美术馆 - 杜蕾斯][url_h5_2]：交互式，使用了重力感应控制界面，视差滚动、情景交互（适合引导展示）
3. [穿越故宫来看你 - 腾讯×故宫][url_h5_3]：视频嵌入、说唱、内容有趣（RAP魔性、创意满分）
4. [纪念哈利波特20周年 - 网易新闻][url_h5_4]：交互式、一镜到底，内容亲切，有音效搭配
5. [是什么改变了这个世界？ - 腾讯][url_h5_5]：H5动画、插画（内容魔性、创意赞）
6. [你玩过ROOM吗？ - 腾讯移动游戏][url_h5_10]：交互式，密室游戏（引导用户去发现和探索线索）
7. [薛之谦史上最疯狂的广告 - 腾讯动漫][url_h5_9]：视频嵌入，先搞笑后讲故事、适合传达内容
8. [出来种太阳迟早是要还的 - 百度外卖][url_h5_6]：视频嵌入、插画、儿歌形式、内容搞笑
9. [朕收到一条来自你妈的微信 - 故宫食品][url_h5_7]：视频嵌入，文案有趣，背景音乐及画面切换配合
10. [全厦门第二酷的快闪H5，挑战89秒不眨眼！ - 荣先生][url_h5_8]：H5动画，简洁大方，内容充实，音效搭配

其实还有很多我没有遇到的H5，在以上各类H5中，对体验和成本，做了以下大致的分类总结：

- **一镜到底** 代表如以上：1、4
    - 体验：用户只需简单的滑动或触碰，就可以较为沉浸地浏览所要展示的内容
    - 成本：对内容要求连贯，尤其是视觉上需要大量资源，成本较大；开发可使用canvas库实现，成本一般
- **视频嵌入** 代表如以上：3、7、8、9
    - 体验：对网络环境依赖度高（弱网下呵呵哒），内容连贯流畅，兼容性好
    - 成本：前期制作依据要求，成本可控，如需拍摄及复杂动画则成本较大；后期调整需重新导出，成本较大
- **交互式** 代表如以上：2、4、6
    - 体验：需要用户操作推进内容展现，具有引导用户探索发现的特点，对内容要求要高
    - 成本：视觉素材较其他类型依赖较小，成本一般；开发上需要定制交互及效果，成本较大
- **H5动画** 代表如以上：5、10
    - 体验：可以制作视频般顺畅的动画效果，主要以平面素材的拼贴变换为主，资源加载较视频具有优势
    - 成本：对素材较依赖，成本一般；开发可使用H5制作工具实现，成本一般

我们最终选择了**H5动画**的效果方案，同时在制作中也参考了10号H5的效果，在保证最终效果可预见的同时，尽可能节省设计和开发的成本。


### 主视觉

这里要感谢准妈UI晓涵的倾情创作，不仅要绘制视觉稿，还要一起商讨每一帧的动画效果。这部分工作，需要把黑白的文字从文稿中抽离出来，在一帧帧中赋予他们生命，让他们在纸上跃然。如此敲打整合，才能确定最终的视觉效果：

![IPO快闪H5最终版][img_ui]

关于趣店IPO视觉设计的更多信息，欢迎关注公众号**趣店用户体验中心**，获取最新品牌项目的文章推送，以及本次相关快闪H5的文章：[欢庆时刻！趣店IPO快闪～][url_qux]


## 开发方案

### 动画方案

由于我们第一次做这种H5需求，而且只有一周左右的设计&开发时间，快速评估后，如果在开发上投入太大，时间上并不允许，于是必须优先保证项目进展，那么在开发方案的选型上，就转向寻求可以方便生成H5动画的开发工具。期间在参考别家的动画H5时，顺便考察了一些JS动画库和开发工具，比如:

- [ThreeJS - 强大的WebGL图形库][url_threejs]，适合做炫酷的3D动画效果
- [CreateJS - 基于HTML5开发的一套模块化的库和工具][url_creatjs]，可以结合Adobe Animate快速实现效果
- [HYPE - 基于HTML5的创作工具][url_hype]，可以在网页上做出悦目的动画效果，无需 Flash 插件

最终在试用与评估后，决定试用HYPE来制作我们本次的快闪H5页面。下面是使用HYPE制作时的界面：

![HYPE界面][img_hype]

那么为什么选择了HYPE？其实原因很简单，大概为以下几点：

- **安装包很小**（ < 20MB），安装便捷
- **试用期内**可以使用HTML导出功能
- 所有静态资源可以**直接导出**到该项目的H5页面中
- 制作过程**界面化易操作**，几乎不需要代码开发，上手难度极低（PPT玩溜的可以直接上手）

关于HYPE，在完成整个H5后，简单总结了一下工具的优点和存在的不足：

- 优点
    - 可按场景分割动画，分别制作、管理，方便调整
    - 使用symbol可以制作复杂的循环动画
    - 自带常用动画库，也可以自定义动画方案
    - 界面化配置与交互开发并存（可嵌入代码）
- 不足
    - 导出项目的静态资源域名，配置不灵活
    - 图片资源无有效优化手段（如小图base64内联、生成雪碧图）
    - 未开放资源加载相关API（无法获取加载状态）
    - 内置IDE使用不方便

同时在使用时，总结了一些制作上的个人心得：

- 导入资源前，墙裂建议**规范文件名**（尤其不要以中文和各种符号命名）
    - 否则导出后，由于资源名异常的问题很难调整（同时后期替换资源时，在资源库中操作难度很大）
- 善于使用**组合功能（Group）**，同时给组设置相对页面居中的定位方式
- **导出GIF**时，需要将页面背景色设置为透明，否则会出现异常
- 需要**循环播放的动画**建议在Symbol中实现
    - 方式为：在Symbol编辑界面中，给时间轴结束点设置返回动画开始
- **避免使用大量基础元素拼接**，即使是重复的组合
    - 如果可以用图片，就用图片，尽可能减少界面中元素的数量


### 分享功能

这个项目除了H5的制作外，还有一个必须搞定的事：**在微信中分享时，需要显示适合微信界面的分享效果**（如下图分享给好友时的对比，左边为不做任何设置时的分享效果，右图为配置后的分享效果），而这需要搭配[微信JSSDK][url_wxjssdk]完成。

![微信分享内容（左：未设置分享信息  右：配置微信JSSDK效果）][img_wx_share_panel]

具体的开发细节，按文档一步步完全可以走通，在这里就不累述细节，只讲几个比较关键的点：

- **设置JS接口安全域名**：公众号设置内设置此步，只可以填写3个域名或路径
    - 设置时，需要将一个**验证文件上传到设置域名的根目录**，在通过验证后，才可以保存设置
- **设置IP白名单**：
    - 只有设置了白名单的IP，才能通过微信接口**获取授权信息**，
- **务必保证服务端对access_token和jsapi_ticket的持久缓存**：
    - access_token和jsapi_ticket两者有效期均为7200秒
    - 两者的api调用次数非常有限，**频繁刷新**会导致api调用**触发频率限制**，服务将不再可用
    - 开发者必须在自己的服务端**全局缓存**
- **分享后再打开会变成http协议**：
    - 调试中发现，在分享配置中填写的https的url，在打开时，会变成http的协议（可通过nginx配置rewrite本次访问为https）
- **获取分享渠道**：
    - 不同的分享渠道会使用不同的回调，可以按各自被调用的情况收集渠道信息
- **获取地理位置接口**：
    - wx.getLocation 方法会在调用时提示用户授权，这个对用户体验影响极大，所以本次没有使用这个接口收集详细的地理位置信息

相关文档和demo资源：
- [微信网页授权说明][url_wx_share_access]
- [微信JSSDK示例页面][url_wx_share_demo] / [示例代码][url_wx_share_demo_code]


### 数据埋点

现在基本功能（页面展示、分享）都完备了，是不是感觉还少了点什么的？当然是埋点收集用户行为数据了。
实际在所有用户端项目中，都需要按指标去收集页面的数据，基本包含以下几大项：

- 基础信息
    - **PV / UV**：页面浏览事件的基础指标，一般埋点方案都有
    - **设备信息**：操作系统、浏览器及版本、设备型号、屏幕尺寸等
    - **网络信息**：访问IP、网络类型、地理位置信息等
- 用户分析
    - **用户路径**：在该项目中，具体为打开页面的渠道来源、分享出去的渠道，以及分享次数
    - **用户行为**：在该项目中，具体为用户点击播放、重播等事件，以及用户浏览时长
- 开发监控：
    - **页面性能**：开发必关注：首字节时间、首屏渲染时间、onload时间等
    - **错误监控**：开发必关注：资源加载报错、JS错误栈、全局异常等

按照以上整理的指标维度埋点，就可以充分收集访问信息了。在这里具体细节不做讨论，各家都有各自的埋点方案，在这个页面引入集团统一的埋点脚本后，还引入了百度统计，做这一步是为了设置一个稳定的数据参考，至少在上线后可以及时对比基础数据来校验自定义的埋点是否存在太大的数据偏差。


## 数据分析

虽然这个项目的生命周期很短，甚至于根本没有计划进行用户推广（实际也没有必要，上面也说了是为了庆祝我厂上市，用来呐喊助(嘚)威(瑟)的哈哈），但按照规范流程，也收集了较为完整的数据。

理论上，实际访问用户与集团用户群基本关系不大，**没有做任何针对性的推广，纯集团员工转发，以及转发后带来的自然浏览和转发**

以下为IPO当天开始至今的数据（实际情况同预测一致，3天后基本就没有访问量了），简单分析一二：

### PV/UV

从PV/UV的数据可以看出，访问量从IPO当天晚上9:30左右开始上扬，随后于22至23点内访问量达到最高值，该小时内约有近4000的访问次数及3000左右的访问用户，按照集团情况分析，达到了**10倍左右的扩散率**，随后访问量按夜间预期自然下降。

有意思的是，访问量在第二天早晨7至9点内再次升起，这代表又有相当一部分人在起床后、上班途中初次/再次访问了该页面（也许这部分访问者昨晚睡得比较早也说不定，美好的一天从刷朋友圈开始），此后一天内访问量缓慢下降也符合自然转发的预期现象。

- 注：**2017-10-18 21:30**：按北京时间计算，为纽交所当日开盘时间，集团小伙伴们此时正聚集在会议中心庆祝&观看直播，同时**开始在朋友圈大量转发IPO信息等**

![PV/UV][img_bi_pvuv]


### 来源分析

微信内页面的来源数据，也如预期一致（预计大部分流量从朋友圈来）。
从图上可以看出，从上线至今，来源为朋友圈的访问量达到了82%左右，而15%左右的流量为朋友间直接转发的链接。这意味着，在所有有效转发中，**分享到朋友圈比单独分享给指定朋友的概率，大了5倍**。
而转发到QQ及QQ空间的情况也存在，看来有些小伙伴也同时照顾了一下不使用微信的同学们。

![来源分析][img_bi_channel_from]


### 来源/分享转化分析

微信内页面的分享数据，却是没有预料到的情况。
从图上可以看出，约有50%的分享，是从朋友圈分享给了指定的朋友，约30%是从朋友圈再次转发到了朋友圈，还有约13%是从信息转发到了朋友圈。
- 这代表在微信中有效的分享里：
    - **约50%具有明确的目标人群**（比如A看到了这个消息，直接分享给了B，而不是群发到朋友圈广而告之）
    - 约30%是为了继续在朋友圈内传播这一消息
    - 约13%继续传播给明确的目标人群

![来源/分享转化分析][img_bi_channel_from_to]


### 转化漏斗

为了分析用户的行为，特地做了以下3个转化漏斗，分别代表的含义是：

- 浏览/分享转化转化漏斗
    - 约88%的用户是在微信中成功打开可分享的页面，其他浏览器打开比例大概是12%
    - 而在微信中具有成功分享能力的用户中，又有**约9.1%的用户进行了转发**


- 浏览/播放/分享转化转化漏斗 `增加了“播放”这个步骤`
    - 微信浏览器占比相同不再解释
    - 而在微信中浏览页面的用户又有**约80%点击了播放**，也就是有20%的微信用户没点击播放
    - 而在微信中点击了播放的用户中，又有约9.48%的用户进行了转发
    - 由此推算：成功打开可分享页面的微信用户中，**约1.4%直接进行了转发，没有继续浏览页面**


- 浏览/播放/重播转化漏斗
    - 在整体用户中，约78%的用户，选择了播放并观看H5播放
    - 在播放的用户中，**约9.43%的用户，完整播放了至少一遍，并点击了重播**

![转化漏斗][img_bi_channel_transform]


### 地域分析

- 从地域数据可以看出，约36%的用户来源于北京，其次为广东、上海
    - 看来本次分享用户的**人脉网络，在一线城市分布较多**
- 其中北京占比最大的原因，和我司小伙伴都在北京总部有直接的联系（这不是废话么哈哈）
    - 我司小伙伴们的人脉网络，北京同样应该占多数

![地域分析][img_bi_area]


### 网络分析

- 从网络类型数据可以看出，约68%的用户是在wifi网络下浏览了页面
    - 这意味着**大部分用户**在浏览时，**具备较好的网络情况**（相对移动数据网络较好）
- 3g+与4g用户分别占比21.47%和10%，其他用户占比不到0.5%，这意味着：
    - 在移动数据网络下，大部分用户群体也具备快速访问H5的条件（当然稳定性需视用户真实情景而定）

![网络分析][img_bi_network]


### 设备分析

- 按操作系统分布：
    - 浏览页面的用户中，IOS用户数量，几乎是安卓用户数量的2倍，**用户设备质量普遍较高**
- 按系统-浏览器分布：
    - 符合预计标准：微信内打开数量占绝大多数（约95%以上，毕竟主要的分享渠道就在微信内）
- 按设备厂商分布：
    - 同操作系统分布分析，但可以看出安卓用户里华为占较多，其次为小米、OPPO、Vivo等

![设备分析][img_bi_device]



## 其他

本次项目过后，又积累了很多之前未曾有过的经验，个人又有了新的技能增长点～










------



[url_h5_1]: http://wx.gz.focus.cn/html/helechina_201709/
[url_h5_2]: http://m.durex.com.cn/qr/artmuseum/
[url_h5_3]: http://nigg.treedom.cn
[url_h5_4]: http://news.163.com/special/fdh5_harrypotter20_19/
[url_h5_5]: http://qipai.qq.com/act/a20151210opening/
[url_h5_6]: http://www.wmy-ad.com/baidu/20160720/
[url_h5_7]: http://9be705463ff7.vt.iamh5.cn/v3/idea/7gEJ3FF5
[url_h5_8]: http://www.bbbaaayyy.com/baydesign/i/index.html
[url_h5_9]: http://game.qq.com/act/a20161121xzq/
[url_h5_10]: http://game.qq.com/cp/a20160310mstt/index.html
[url_h5_ipo]: https://h5.qufenqi.com/ipo/?e_channel_from=thunf
[url_threejs]: http://threejs.org/
[url_creatjs]: http://threejs.org/
[url_hype]: http://tumult.com/hype/
[url_qux]: http://mp.weixin.qq.com/s?__biz=MzI1NTg2NDYwNg==&mid=2247483699&idx=1&sn=5181a3aa43364af4514e0dc5806d197d&chksm=ea2e3b42dd59b25407d1b23102cc4e9d262ce3b70bef0fb7368c15613d59c5ad9ea54862c150&mpshare=1&scene=1&srcid=1023EeCT2CcdErGwJ4vRKqsR#rd
[url_wxjssdk]: https://mp.weixin.qq.com/wiki?t=resource/res_main&id=mp1421141115
[url_wx_share_access]: https://mp.weixin.qq.com/wiki?t=resource/res_main&id=mp1421140842
[url_wx_share_demo]: http://demo.open.weixin.qq.com/jssdk
[url_wx_share_demo_code]: http://demo.open.weixin.qq.com/jssdk/sample.zip


[img_ui]: http://img002.qufenqi.com/products/54/8f/548f1836a299a5d2fd7ac0d1f8693e2a.jpg
[img_hype]: http://img003.qufenqi.com/products/09/a2/09a25d697dcbe22ab6e65151cec097dd.jpg
[img_wx_share_panel]: http://img002.qufenqi.com/products/65/16/65164820071877645de26f6778acf815.png
[img_bi_pvuv]: http://img002.qufenqi.com/products/db/20/db2052eca4451e37b4ce8a4ec2737a2c.jpg
[img_bi_network]: http://img002.qufenqi.com/products/bd/dc/bddc3c94bf1957f4a2e69fe3dac2eda8.jpg
[img_bi_device]: http://img002.qufenqi.com/products/e0/68/e0680399fd30ec79d1852a1d9dc16407.jpg
[img_bi_channel_from]: http://img003.qufenqi.com/products/a2/07/a207576696986c3a1ef28a5acf4cab85.png
[img_bi_channel_from_to]: http://img003.qufenqi.com/products/c8/02/c80228b94066f4a19fdbb6477fe70f54.jpg
[img_bi_channel_transform]: http://img003.qufenqi.com/products/b7/56/b7565a2c9adc795786130beafd147dfa.jpg
[img_bi_area]: http://img002.qufenqi.com/products/91/86/9186d2da9afc34c496bd82cf6f64ae6d.jpg

