# Optimization-of-seckill
对原seckill九价秒杀程序的二次开发和优化
## 使用方法
前提：  
一定要保证当前时间与互联网时间一致，精确到秒！！！

需要会用fiddler抓微信小程序的包，具体操作自行搜索（PC微信+fildder非常简单）


### 具体步骤
1. 抓取微信小程序的包header,格式大概如下：
```
GET https://miaomiao.scmttec.com/seckill/seckill/list.do?offset=0&limit=10&regionCode=5101 HTTP/1.1
Host: miaomiao.scmttec.com
Connection: keep-alive
accept: application/json, text/plain, */*
tk: wxapptoken:10:56ce0d6ad845798561edd70a30d200d2207
cookie: _xzkj_=wxapptoken:10:56ce0db70a30dD
charset: utf-8
x-requested-with: XMLHttpRequest
content-type: application/json
User-Agent: Mozilla/5.0 (Linux; Android 5.1.1; OPPO R17 Pro Build/NMF26X; wv) AppleWebKit/537.36 (KHTML, like Gecko) Version/4.0 Chrome/74.0.3729.136 Mobile Safari/537.36 MMWEBID/1042 MicroMessenger/7.0.17.1720(0x27001134) Process/appbrand0 WeChat/arm32 NetType/WIFI Language/zh_CN ABI/arm32
Accept-Encoding: gzip,compress,br,deflate
Referer: https://servicewechat.com/wxff8cad2e9bf18719/4/page-frame.html
```
> 注意，这些并不是都是必须的，其实只需要包括tk、Cookie开头的的两行即可

2. 运行程序，点击设置Cookie，输入上一步抓取的包，点击解析，保存（如果格式与上面的例子的不一致，需要手动输入tk和cookie）
3. 点击设置成员，选中列表中的成员，点击确定(需要提前在约苗中填写)
4. 点击刷新疫苗列表，即可在列表中看到秒杀列表
5. 在秒杀开始的前一段时间（要保证cookie在有效期内），点击开始即可，程序会在距开始时间一定时间内启动并发秒杀
6. 抢购成功后，需要手动登录约苗小程序，选择接种日期（如果预约时间选择不了不用着急，系统会自动给你预约时间，有些秒杀无法选择接种时间，只能系统自动分配时间）

### 注意事项

1. 仅供交流使用，切勿用于商业用途
2. 并未测试小程序的Cookie的过期时间，大概是一个小时到两个小时之间
3. 目前代码只能在成都区域工作，后期考虑可能增加选择区域的功能
4. 同一个cookie和st可以多个程序使用，电脑配置高、带宽高的话，成功率高（限制了并发频率，不清楚是依据规则IP还是用户）
