
# 爬取web日轻(カクヨム上面的)并到处为排版好的文档

## 原项目
### 用于整理[Web日轻](https://kakuyomu.jp/)成Markdown文档<br>
   * ``新添加的功能:``<br>
      1. 添加标签<br>
      2. 添加大章与小章的整理支持<br>
      3. 添加文档生成的时间<br>
      4. 解决换行问题<br>
      5. 解决如果小说书名中出现不能在文件名里面出现的字符的问题<br>
   * ``未来打算完成的事情:``<br>
      * [ ] 正文整理部分,把爬虫与Markdown文档生成的代码拆成两部分,以方便进行并行化处理<br>
      * [ ] 爬虫的速度提升<br>
         参考[知乎专栏](https://zhuanlan.zhihu.com/p/35359905)<br>
         注:上面专栏的源代码链接应该改成[这个](https://github.com/uupers/BiliSpider/blob/95c07da2f7abf4f318dc41dff8e6dd891045b799/%E6%9E%81%E9%80%9F%E8%A7%86%E9%A2%91%E7%88%AC%E8%99%AB2.2.nb)<br>
   * ``注意:``<br>
      因为是根据[妹と学園のアイドルを抱き枕代わりにして寝ていたらいつの間にか惚れられていた](https://kakuyomu.jp/works/1177354054893622559)这本书的结构完成的代码,所以无法适应全部的格式<br>
      已知的一些bug:<br>
      * [x] 遇到有章节的小说无法整理出章节,例如[兄を道連れに転生した妹は、兄妹婚を目指すようです](https://kakuyomu.jp/works/1177354054888616069)(这书是目前为止看到的章节结构最复杂的了)<br>
      这是那本书的目录样子:<br>
      ![ ](https://z3.ax1x.com/2021/07/16/WK2SFU.png)<br>
      * [x] 奇怪的换行(其实这bug一直有,只是其中一部分情况被用字符串替代换掉了)<br>
      ![ ](https://z3.ax1x.com/2021/07/23/Wys64x.png)
      * [x] 小说名里面有不能出现在文件名里面的字符<br>
      ![ ](https://z3.ax1x.com/2021/07/24/WccwDO.png)<br>

## 目前的结构
```mermaid
    graph TD
    a(爬取全部章节标题与对应的URL)-->b(分析章节结构)-->c(生成目录)-->d(爬取章节内容)-->e(转化成Markdown文档)-->f(导出为Markdown文档)
```

## 未来的计划

```mermaid
    graph TD
    a(现有的项目)
    a --> |维持Markdown文档| b(当没有大章节或者小章节时,标题级数不跳跃) --> c(目录部分结构变得和Markdown All In One一致<br>拥有转跳功能,通过缩进分别标题级数) --> d(使用Pandoc把Markdown转化成PDF,EPUB)
    a --> |重心将会移动到此处| e(使用LaTeX代替Markdown)
    d & e -->h(正文爬取与拼接拆开成两个模块) --> i(用URLSubmit代替URLRead来提升爬取时的速度) --> j(多核爬虫)
```
