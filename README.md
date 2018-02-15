### 使用Node爬虫获取简书首页文章列表
>   superagent是nodejs里一个非常方便的客户端请求代码模块，superagent是一个轻量级的，渐进式的ajax API，可读性好，学习曲线低，内部依赖nodejs原生的请求API,适用于Node环境下。语法：request(RequestType, RequestUrl).end(callback(err, res));
>   cheerio是一个Node的库，可以理解为一个Node版本的jQuery，用来从网页中以 css selector取数据，使用方式和jQuery基本相同。
####    实现思路
*   **引入依赖**
*   **定义一个地址**
*   **发起请求**
*   **页面数据解析**
*   **分析页面数据**
*   **生成数据**
####    依赖
*   **superagent**
*   **cheerio**
>   npm install superagent cheerio --save-dev安装依赖即可
####    使用
*   **利用Node的require方法引入依赖**
```
const superagent = require('superagent');
const cheerio = require('cheerio');
```
*   **定义一个地址**
```
const reptileUrl = "http://www.jianshu.com/";
```
*   **发起请求并解析数据**
```
superagent.get(reptileUrl).end(function (err, res) {
    // 抛错拦截
     if(err){
         return throw Error(err);
     }
   /**
   * res.text 包含未解析前的响应内容
   * 我们通过cheerio的load方法解析整个文档，就是html页面所有内容，可以通过console.log($.html());在控制台查看
   */
   let $ = cheerio.load(res.text);
   // 分析数据，利用cheerio解析并剥离／生成需要的数据
});
```
####    完整案例
>   完整的案例，上传在GitHub托管，下载完成后进到目录使用包管理器安装依赖，然后运行项目，打开浏览器输入localhost:3000即可预览
####    小记
>   通过对Node爬虫的学习，可以加深对Node的印象，以及熟练对一些基础方法的使用，对于以后抓取大数据的处理，还是很有帮助
####    感谢
>   以上方法，基本是参考自SegmentFault作者jiayisheji的文章，文章链接地址：[10分钟教你撸一个nodejs爬虫系统](https://segmentfault.com/a/1190000009542336)