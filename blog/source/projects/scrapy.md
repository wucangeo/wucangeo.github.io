---
title: 土地流转交易数据挖掘分析
date: 2016-02-04 13:51:10
tags: 项目经历
categories: projects
---

## 土地流转交易数据挖掘分析 
* 实施时间
	* 2015-07 ~ 2015-08
* 项目背景
	* 由于 `土地流转`项目和论文数据需要，快速学习[python](https://www.python.org/)并使用开源工具[Scrapy](http://scrapy.org/)抓取了[土流网](http://www.tuliu.com/)的历史交易数据。
* 承担工作
	* 学习Scrapy
	* 抓取数据
	* 数据分析
* 使用技术
	* [python](https://www.python.org/), [Scrapy](http://scrapy.org/)
* 项目源代码地址
	* [https://github.com/wucangeo/ScrapyData](https://github.com/wucangeo/ScrapyData)


### 土流网数据示例

![土流网](http://7xlak7.com1.z0.glb.clouddn.com/blog/images/projects/scrapyData/tuliuwang1.jpg)
![土流网](http://7xlak7.com1.z0.glb.clouddn.com/blog/images/projects/scrapyData/tuliuwang2.jpg)

### 土流网信息源码分析
``` html
<h2>基本信息</h2>
<div class="content-table clearfix">
    <dl>
        <dt>土地类型</dt>
        <dd><a href="http://daxing.tuliu.com/nongcunzhaijidi/">农村宅基地</a></dd>
    </dl>
    <dl>
        <dt>流转性质</dt>
        <dd><a href="/zulin/">租赁</a></dd>
    </dl>
    <dl>
        <dt>发布时间</dt>
        <dd>2015-07-31</dd>
    </dl>
    <dl>
        <dt>更新时间</dt>
        <dd>2015-08-12</dd>
    </dl>
    <dl>
        <dt>土地面积</dt>
        <dd>416平米</dd>
    </dl>
    <dl>
        <dt>流转年限</dt>
        <dd>70年</dd>
    </dl>
    <dl>
        <dt>价格</dt>
        <dd>
            <ul>
                <li>一口价：3万元</li>
            </ul>
        </dd>
    </dl>
    <dl>
        <dt>付款方式</dt>
        <dd>面议</dd>
    </dl>
</div>
```


### Scrapy数据抓取核心代码
``` python
import scrapy
from scrapy.spiders import CrawlSpider, Rule
from scrapy.linkextractors import LinkExtractor
from scrapy.exporters import JsonItemExporter

from scrapy.spiders import Spider
from scrapy.selector import Selector
from ScrapyData.items import Website

class LandSpider(Spider):
    name = "land"
    allowed_domains = ["tuliu.com"]    
    start_urls = [
        "http://tuliu.com/view-372131.html"

    获取100条
    initUrl = "http://tuliu.com/view-3721"
    for i in range(100):
        url = initUrl + str(i).zfill(2) + ".html"
        print(url)
        start_urls.append(url)

    def parse(self, response):
        """
        The lines below is a spider contract. For more info see:
        http://doc.scrapy.org/en/latest/topics/contracts.html
        @url http://www.dmoz.org/Computers/Programming/Languages/Python/Resources/
        @scrapes name
        """
        sel = Selector(response)
        sites = sel.xpath('//div[@class="attribute"]')
        items = []

        for site in sites:
            item = Website()

            # names = site.xpath('string(dl/dd[1]/p[2]/a/text())').extract()
            # nameitem = []
            # for name in names:
            #     nameitem.append(name.encode('unicode-escape'))
            item['name'] = site.xpath('string(dl/dd[1]/p[2]/a/text())').extract()
            item['url'] = site.xpath('string(dl/dd[2]/p[2]/a/text())').extract()
            item['description'] = site.xpath('string(dl/dd[3]/p[2]/text())').extract()
            items.append(item)

        return items
```

### 数据抓取结果保存在MySQL数据库中
` 图片待补充 `

