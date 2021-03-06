## [AkShare](https://github.com/jindaxiang/akshare) 事件数据

### 新型冠状病毒-网易

接口: epidemic_163

目标地址: https://news.163.com/special/epidemic/

描述: 获取网易-新型冠状病毒-疫情数据

限量: 单次返回实时数据

输入参数

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="实时", 返回实时数据; indicator="历史", 返回历史数据, 可能不及时 |

输出参数

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| country      | str   | Y        |   |
| area      | str   | Y        |   |
| city      | str   | Y        |   |
| confirm      | int   | Y        |   |
| suspect      | int   | Y        |   |
| dead      | int   | Y        |   |
| heal      | int   | Y        |   |
						
接口示例

```python
import akshare as ak
epidemic_163_df = ak.epidemic_163(indicator="实时")
print(epidemic_163_df)
```

数据示例-实时

```
    country area city  confirm  suspect  dead  heal
0        中国   湖北   武汉     1590        0    85    42
1        中国   湖北   黄冈      213        0     4     2
2        中国   湖北   孝感      173        0     1     0
3        中国   湖北   荆门      114        0     3     0
4        中国   湖北  恩施州       38        0     0     0
..      ...  ...  ...      ...      ...   ...   ...
316    斯里兰卡                  1        0     0     0
317      中国   吉林  公主岭        1        0     0     0
318      中国   海南   琼海        1        0     0     0
319      中国   海南  琼中县        1        0     0     0
320      中国   海南   东方        1        0     0     0
```

数据示例-历史

```
      day   time country  area  dead  confirm  suspect  heal  city district
0    1.12             中国  湖北武汉     1       41        0   NaN  None     None
1    1.13             中国  湖北武汉     1       41        0   NaN  None     None
2    1.14             中国  湖北武汉     1       41        0   NaN  None     None
3    1.15             中国  湖北武汉     2       41        0   NaN  None     None
4    1.16             中国  湖北武汉     2       45        0   NaN  None     None
..    ...    ...     ...   ...   ...      ...      ...   ...   ...      ...
220  1.26  09:00      中国    台湾     0        3        0   0.0               
221  1.26  09:00      中国    新疆     0        4        0   0.0               
222  1.26  09:00      中国    澳门     0        5        0   0.0               
223  1.26  09:00      中国   内蒙古     0        7        0   0.0               
224  1.26  09:00      中国    青海     0        4        0   0.0  
```

### 新型冠状病毒-丁香园

接口: epidemic_dxy

目标地址: http://3g.dxy.cn/newh5/view/pneumonia?scene=2&clicktime=1579615030&enterid=1579615030&from=groupmessage&isappinstalled=0

描述: 获取丁香园-新型冠状病毒-疫情数据

限量: 单次返回实时数据

输入参数-info

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="info", 返回全国统计数据|

输出参数-info

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| 字符串      | str   | Y        |统计时间和情况概述   |

接口示例-info

```python
import akshare as ak
epidemic_dxy_df = ak.epidemic_dxy(indicator="info")
print(epidemic_dxy_df)
```

数据示例-info

```
截至 2020-01-24 14:33 数据统计全国 确诊 883 例 疑似 1073 例 治愈 35 例 死亡 26 例
```

输入参数-全国

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="全国", 返回全国各省市统计数据|

输出参数-全国

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| 地区      | str   | Y        | 区域   |
| 地区简称      | str   | Y        | 区域   |
| 确诊      | str   | Y        | 数据  |
| 疑似      | str   | Y        | 数据  |
| 治愈      | str   | Y        | 数据  |
| 死亡      | str   | Y        | 数据  |
| 备注      | str   | Y        | 数据  |
					
接口示例-全国

```python
import akshare as ak
epidemic_dxy_df = ak.epidemic_dxy(indicator="全国")
print(epidemic_dxy_df)
```

数据示例-全国

```
          地区 地区简称   确诊  疑似  治愈  死亡             备注
0        湖北省   湖北  729   0  32  39               
1        广东省   广东   78   0   2   0               
2        浙江省   浙江   62   0   1   0               
3        重庆市   重庆   57   0   0   0               
4        湖南省   湖南   43   0   0   0               
5        北京市   北京   41   0   3   0               
6        安徽省   安徽   39   0   0   0               
7        上海市   上海   33   0   1   0               
8        河南省   河南   32   0   0   0               
9        四川省   四川   28   0   0   0               
10       山东省   山东   27   0   0   0               
11   广西壮族自治区   广西   23   0   0   0               
12       江西省   江西   18   0   0   0               
13       福建省   福建   18  20   0   0  福建地区新增疑似 20 例
14       江苏省   江苏   18   0   1   0               
15       海南省   海南   17   0   0   0               
16       辽宁省   辽宁   16   0   0   0               
17       陕西省   陕西   15   0   0   0               
18       云南省   云南   11   0   0   0               
19       天津市   天津   10   0   0   0               
20      黑龙江省  黑龙江    9   0   0   1               
21       河北省   河北    8   0   0   1               
22       山西省   山西    6   0   0   0               
23        香港   香港    5   0   0   0               
24       贵州省   贵州    4   0   0   0               
25       吉林省   吉林    4   0   0   0               
26       甘肃省   甘肃    4   0   0   0               
27   宁夏回族自治区   宁夏    3   0   0   0               
28        台湾   台湾    3   0   0   0               
29  新疆维吾尔自治区   新疆    3   0   0   0               
30        澳门   澳门    2   0   0   0               
31    内蒙古自治区  内蒙古    2   0   0   0               
32       青海省   青海    1   0   0   0               
```

输入参数-具体省份(如: 浙江省)

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="浙江省", 返回具体省市统计数据|

输出参数-具体省份(如: 浙江省)

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| 区域      | str   | Y        | 区域   |
| 确诊人数      | str   | Y        | 数据  |
| 疑似人数      | str   | Y        | 数据  |
| 治愈人数      | str   | Y        | 数据  |
| 死亡人数      | str   | Y        | 数据  |
					
接口示例-具体省份(如: 浙江省)

```python
import akshare as ak
epidemic_dxy_df = ak.epidemic_dxy(indicator="浙江省")
print(epidemic_dxy_df)
```

数据示例-具体省份(如: 浙江省)

```
   区域  确诊人数  疑似人数  治愈人数  死亡人数
0  台州    20     0     0     0
1  杭州    12     0     0     0
2  温州    10     0     1     0
3  宁波     6     0     0     0
4  绍兴     4     0     0     0
5  嘉兴     4     0     0     0
6  舟山     2     0     0     0
7  金华     2     0     0     0
8  衢州     2     0     0     0           
```

输入参数-news

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="news", 返回全国突发新闻数据|

输出参数-news

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| title      | str   | Y        |新闻标题   |
| summary      | str   | Y        | 数据概述  |
| infoSource      | str   | Y        | 新闻来源  |
| provinceName      | str   | Y        | 省份  |
| sourceUrl      | str   | Y        | 新闻地址  |

接口示例-news

```python
import akshare as ak
epidemic_dxy_df = ak.epidemic_dxy(indicator="news")
print(epidemic_dxy_df)
```

数据示例-news

```
                                          title  ...                                          sourceUrl
0                                    福建新增 1 例病例  ...      http://m.weibo.cn/2656274875/4464277568378388
1                                      上海启动一级响应  ...      http://m.weibo.cn/2803301701/4464275537960579
2                                      北京启动一级响应  ...      http://m.weibo.cn/2803301701/4464275537960579
3                               北京 1 新冠肺炎确诊患者出院  ...      http://m.weibo.cn/2803301701/4464259805726673
4                           国务院征集新冠肺炎疫情防控工作问题线索  ...  https://mp.weixin.qq.com/s/vQ-m0wW2cVZGYfJtAAMeiQ
5                                     天津确诊第 7 例  ...      http://m.weibo.cn/2656274875/4464245485576951
6                                      天津启动一级响应  ...      http://m.weibo.cn/2803301701/4464245166727843
7                                      安徽启动一级响应  ...      http://m.weibo.cn/2803301701/4464244898679663
8                            重磅！发热咳嗽非新冠肺炎唯一首发症状  ...    http://m.weibo.cn/2803301701/4464244348901450 ​
9                                  宁夏新增确诊1例疑似1例  ...      http://m.weibo.cn/2656274875/4464239232497670
10                     山东今日新增确诊 6 例，山东累计确诊 15 例  ...      http://m.weibo.cn/2803301701/4464230751473157
11                        福建新增确诊 4 例，福建累计确诊 9 例  ...      http://m.weibo.cn/2803301701/4464229795391738
12                                     武汉关闭过江隧道  ...      http://m.weibo.cn/2803301701/4464223541240916
13                                  内蒙古确诊首例新冠肺炎  ...    http://m.weibo.cn/2803301701/4464216926774457 ​
14                                     辽宁新增确诊1例  ...      http://m.weibo.cn/2803301701/4464215920401389
15                              转发提醒：这个春节尽量不聚会！  ...      http://m.weibo.cn/2803301701/4464209549089465
16                        海南新增确诊病例4例，海南累计确诊病例8例  ...     https://m.weibo.cn/2803301701/4464204335127376
17                      湖南新增确诊 15 例：湖南累计确诊 24 例  ...                             http://dxys.com/xyJAVU
18                    江苏新增新冠肺炎确诊病例4例，江苏累计新冠肺炎9例  ...        https://m.weibo.cn/status/4464192113565122?
19                      重庆新增确诊病例18例，重庆累计确诊病例27例  ...        https://m.weibo.cn/status/4464192578727481?
20        吉林新增2例新型肺炎确诊病例，吉林省累计报告新型冠状病毒感染的肺炎病例3例  ...        https://m.weibo.cn/status/4464191185997393?
21                   韩联社报道称，韩国出现第二例新型冠状病毒肺炎确诊病例  ...        https://m.weibo.cn/status/4464190838721454?
22                                 新疆新冠肺炎确诊病例2例  ...        https://m.weibo.cn/status/4464190448434604?
23                   四川新增新冠肺炎7例，四川累计新冠肺炎确诊病例15例  ...        https://m.weibo.cn/status/4464188997392969?
24                      浙江新增确诊病例16例，浙江累计确诊病例43例  ...  https://weibo.com/2803301701/IqVPiqaGC?ref=hom...
25           1月23日0时-24时，湖北省新增新型冠状病毒感染的肺炎病例105例  ...        https://m.weibo.cn/status/4464187650423052?
26                                 日本确诊2例新型肺炎病例  ...        https://m.weibo.cn/status/4464186283758930?
27  1月23日0-24时，黑龙江省报告新型冠状病毒感染的肺炎新增确诊病例2例，死亡病例1例  ...        https://m.weibo.cn/status/4464184127847534?
28        1月23日10时至24时，安徽省报告新型冠状病毒感染的肺炎新增确诊病例6例  ...        https://m.weibo.cn/status/4464183024267897?
29                               山东新增3例新型肺炎确诊病例  ...  https://weibo.com/2656274875/IqVDCt7bx?ref=hom...
30                              广东新冠肺炎新增确诊病例21例  ...  https://weibo.com/2803301701/IqVDxtTVg?ref=hom...
31                               河南新冠肺炎新增确诊病例4例  ...  https://weibo.com/2803301701/IqVxI77w5?ref=hom...
32                               全国确诊830例新型肺炎病例  ...  https://weibo.com/2656274875/IqVnfb1Hm?from=pa...
33                               上海新增4例新冠肺炎确诊病例  ...  https://weibo.com/2803301701/IqVhVnT9w?ref=hom...
34                                 武汉将以小汤山模式建医院  ...  https://weibo.com/2803301701/IqV7dq2sm?ref=hom...
35                         世卫组织：新型肺炎不构成国际突发卫生事件  ...  https://m.weibo.cn/status/4464150224652866?sud...
36                     北京新增4例新型肺炎确诊病例，累计确诊病例26例  ...        https://m.weibo.cn/status/4464099343625924?
37                               天津新增1例新型肺炎确诊病例  ...      http://m.weibo.cn/2656274875/4464091609170082
38                               广西新增新冠肺炎确诊病例8例  ...  https://www.weibo.com/2803301701/IqSJAANR5?fro...
39                           【湖北省新冠肺炎疫情防控指挥部通告】  ...  https://www.weibo.com/2803301701/IqSEcDHtL?fro...
40                           湖南启动重大突发公共卫生事件一级响应  ...  https://www.weibo.com/2803301701/IqSwMxPd0?fro...
41                         武汉开通24小时电话接收社会各界爱心捐赠  ...  https://mp.weixin.qq.com/s/cICSHZNVynQj7m63RSAv1Q
42                  文化和旅游部、国家文物局：出现疑似病人就地停止旅游活动  ...  https://mp.weixin.qq.com/s/cICSHZNVynQj7m63RSAv1Q
43                               河北 1 例新型肺炎病例死亡  ...  https://weibo.com/2656274875/IqSjFocrm?from=pa...
44                               江西新增 4 例新型肺炎病例  ...        https://m.weibo.cn/status/4464049040965675?
45                           湖北黄石 10 名疑似患者已隔离治疗  ...        https://m.weibo.cn/status/4464044838788193?
46                              昆明确诊第 2 例新型肺炎病例  ...        https://m.weibo.cn/status/4464047963266414?
47                              财政部拨10亿补助湖北防控疫情  ...      http://m.weibo.cn/2803301701/4464041822671982
```

输入参数-hospital

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="hospital", 返回全国发热门诊数据|

输出参数-hospital

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| 省级行政区      | str   | Y        |-   |
| 市级      | str   | Y        | -  |
| 机构-医院      | str   | Y        | -  |

接口示例-hospital

```python
import akshare as ak
epidemic_dxy_df = ak.epidemic_dxy(indicator="hospital")
print(epidemic_dxy_df)
```

数据示例-hospital

```
   省级行政区  市级      机构／医院
0    湖北省  全省  定点医院/发热门诊
1    湖北省  武汉  定点医院/发热门诊
2    湖北省  荆门  定点医院/发热门诊
3    湖北省  宜昌  定点医院/发热门诊
4    湖北省  恩施  定点医院/发热门诊
..   ...  ..        ...
69    宁夏   /  定点医院/发热门诊
70    西藏   /  定点医院/发热门诊
71    新疆   /  定点医院/发热门诊
72    青海   /       定点医院
73    甘肃   /       定点医院
```

输入参数-plot

| 名称   | 类型 | 必选 | 描述                                                                              |
| -------- | ---- | ---- | --- |
| indicator | str | Y | indicator="plot", 绘制-全国疫情趋势图|

输出参数-plot

| 名称          | 类型 | 默认显示 | 描述           |
| --------------- | ----- | -------- | ---------------- |
| 图片      | str   | Y        |图片, 需要自己保存   |

接口示例-plot

```python
import akshare as ak
ak.epidemic_dxy(indicator="plot")
```

图片示例-plot

![](https://jfds-1252952517.cos.ap-chengdu.myqcloud.com/akshare/readme/event/epidemic_trend.jpg)
