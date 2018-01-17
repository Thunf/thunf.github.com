---
title: 踩坑parameterLimit - 神秘的1000parse限制
toc: true
date: 2017-01-20 22:31:52
tags:
categories:
thumbnail: //img003.qufenqi.com/products/6b/16/6b16f016aa06578523cec21b21c1f8bd.jpg
photo:
---


项目中遇到一个诡异的问题：提交表单时，存在字段的值如[1,2,3,4,...,M,N]，但是在服务端解析到的值却是[1,2,3,...,M]，数据没有损坏，偏偏是最后几个字段的数据神秘消失掉，疯掉...

<!-- more -->

仔细排查了从请求发送到接收完成之间的业务代码，并没有发现什么的诡异的地方，只料想应该是存在某种限制，对提交的表单数据的属性（length? size? key?）存在最大限制，那么问题就来了...


## 查找限制

既然是限制，那就有可能是提交时或者接收时做了限制，总之数据不可能在传输时莫名其妙蒸发掉...

- 首现，确认发送了完整的数据：
    - 控制台（DevTools）
    - 抓包（Charles）

这两步都很简单，稍微看一下就可以确定数据都是全的，那么问题很可能就出在服务端了（反正不可能传输层稳定漏传了几个字节，还刚刚好对应少的那几个字段，反正我是不信）

- 然后，检查服务端收到数据：
    - 检查Response中获得的数据体（其实就是这步发现少了数据的）
    - 检查服务端收到的原始信息中，数据是否完整（只好去撸源码了）

话说这步排查了挺久，按依赖依次排查，最后在[qs/lib/parse.js][url_qs/parser.js]发现了一个地方👇

```js
internals.parseValues = function (str, options) {
    ...
    var parts = str.split(options.delimiter, options.parameterLimit === Infinity ? undefined : options.parameterLimit);
    ...
}
```

在qs中，找到如下对parameterLimit的定义：

> The depth limit helps mitigate abuse when qs is used to parse user input, and it is recommended to keep it a reasonably small number.
For similar reasons, by default qs will only **parse up to 1000 parameters**.  --- [ljharb/qs][url_qs]

确实在上述文件里，找到了这样的默认值：

```js
// qs/lib/parse.js
// Declare internals
var internals = {
    ...
    delimiter: '&',
    parameterLimit: 1000,
    ...
};
```

好了，这下可真相大白了，原来使用qs解析键值对的时候，给`split`传了第二个参数，也就是`str.split('&', 1000)`
而`split`的第二个参数，查看文档，定义如下：

```js
stringObject.split(separator, howmany)
```

这样一来，就可以解释的通了，默认只split了1000个键值对，而在提交的时候，恰好超出了1000的数量，最后超出的键值对就直接在parse的过程中丢失了。


## 思考&发现

按官方的说明，当QS用于解析用户输入时，深度限制有助于减少滥用，建议将其保持在适合的较小数量，对于参数限制也是相似的原因。

实际操作中，很少会有表单类型的数据大于1000键值对的情况。而本次查出的这个问题，恰好也反应了koa-grace中存在的问题，并随后进行了修正：在判断`Content-Type`时，优先判断是否JSON格式`application/json`（此前默认先判断`application/x-www-form-urlencoded`）。


查找问题的过程中，也发现了其他框架同样存在这种处理。比如在[Express.js][url_express]的官方组件[expressjs/body-parser][url_bodyparser]的文档中，发现了以下描述：

> The parameterLimit option controls the maximum number of parameters that are allowed in the URL-encoded data. If a request contains more parameters than this value, a 413 will be returned to the client. **Defaults to 1000.**

这样的处理(413)，至少还有迹可循，像上面那样非要到源码里确认的情况，真是坑了😂


## 年终吐槽

时值年前最后一天上班，明天就飞三亚开年会去了，居然还加班到公司没人才走，也是醉了...



[url_qs/parser.js]: https://github.com/ljharb/qs/blob/v4.0.0/lib/parse.js#L22
[url_qs]: https://github.com/ljharb/qs
[url_express]: https://github.com/expressjs
[url_bodyparser]: https://github.com/expressjs/body-parser




