# selectdemo

> ul模拟select下拉效果（vue）

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
前段时间接手了一个项目，奇葩的客户不喜欢在客户端select选择做出来的效果是类似ios的select效果，给的设计图中的下拉选择列表是pc端用的那种下拉框，刚巧公司选用的前端技术栈mint-ui中没有类似于pc端的select下拉框，无奈只能自己写一个，查询了很多资料，发现select 的样式是很难改变，所以只能用ul来模拟select的下拉效果。
### 本文使用的技术栈主要有vue、lodash、less。
点击输入框ul 会有下拉的一个过渡效果，需要注意的是一定要给ul一个固定的高度，百分比、max-height、min-height 是没有过渡效果的。
由于伪元素after和before是不支持input元素使用的，所以此处添加了<i>来存放三角箭头。

具体代码可以看src/components/HelloWord.vue