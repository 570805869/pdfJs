# pdfjs-vueDemo

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```
文档：
[guide](http://vuejs-templates.github.io/webpack/) <br>
[docs for vue-loader](http://vuejs.github.io/vue-loader)

# 页面
> 官方demo：http://mozilla.github.io/pdf.js/web/viewer.html<br>
### 1. 预览本地pdf
- 1.将viewer.js 的 10053 放开，10054注释，输入路径 http://localhost:8080/static/pdf/web/viewer.html

  2.访问  http://localhost:8080/static/pdf/web/viewer.html?file=/static/pdf/web/demo.pdf
### 2. 预览服务器的pdf
- 1.let url = 'http://somedomain/doc/manuals/R-intro.pdf'
- 2.let url = 'http://image.cache.timepack.cn/nodejs.pdf'
 这两个url网上找的，虽然都是服务器pdf路径，通过<br>
  http://localhost:8080/static/pdf/web/viewer.html?file=http://image.cache.timepack.cn/nodejs.pdf<br>
 访问但是:
  - 上面第一个会报错
  - 第二个正常预览
是因为第一个的服务器端没有设置Access-Control-Allow-Origin:*，允许跨域，<br>
R-intro.pdf的预览就会报 '意外的服务器相应<br>
Unexpected server response (0) while retrieving PDF "http://somedomain/doc/manuals/R-intro.pdf". <br>
猜测会有人报'file origin does not match viewer.js' 我没报的原因是我简单粗暴的将viewer.js的1863行注释了！
但是配置服务器允许跨域不安全也不好，so，这就需要后台来配合了<br>
后台需要返回你一个流的形式的pdf，pdf.js插件是可以识别的，也不会报跨域问题！！！ <br>
- 3.还有一个是文档流格式，具体查看代码
