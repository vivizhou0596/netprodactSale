# 一个简单的vue练习demo

标签（空格分隔）： vue vue-router  vue-cli
---

## 1、netProdactSale简介

### 1.1概述
这是一个简单的网络产品售卖系统，麻雀虽小五脏俱全，对于vue中的指令、父子组件通信，路由配置，组件缓存，动画，事件绑定等主要功能都有用到，是一个全面的vue练习项目，喜欢的话记得star；
### 1.2模块介绍
1、首页：注册，登陆，广告轮播，产品列表，新闻列表
2、产品详情：产品基本信息，产品参数说明（基本信息展现方式样式与功能相似，只是参数差异，所以抽离成了单选组件，多选组件及记数组件）
3、购买产品：展示购买的产品，可以选择付款银行（并没有真的实现银行付款，只是一个效果模拟），购买成功与失败，购买成功，进入的产品页能查看自己的产品

### 1.3安装说明

``` bash
# 安装依赖
npm install

# 前端re'jia localhost:8080
npm run dev

# 压缩打包
npm run build

# 压缩打包，并生产分析报告
npm run build --report
```

## 2、目录结构说明
因为vue-cli生成的项目结构，build，config等文件夹下关于webpack等的配置就不做说明了，只说明src下的

│  App.vue   
│  main.js    项目的入口文件以及路由配置
│
├─assets      静态资源img,css
│  │  logo.png
│  │
│  ├─banks
│  │      banks.png
│  │
│  ├─images
│  │      1.png
│  │      2.png
│  │      3.png
│  │      4.png
│  │
│  └─slideShow
│          pic1.jpg
│          pic2.jpg
│          pic3.jpg
│          pic4.jpg
│
├─components               组件：模态框，轮播组件，登陆，注册等页面组件
│  │  bankChooser.vue
│  │  checkOrder.vue
│  │  dialog.vue
│  │  layout.vue
│  │  logForm.vue
│  │  regForm.vue
│  │  slideShow.vue
│  │
│  └─base                  基础组件 ：单选，多选，时间，计数等功能组件
│          chooser.vue
│          counter.vue
│          datepicker.vue
│          multiplyChooser.vue
│          selection.vue
│
├─pages                  页面
│  │  detail.vue
│  │  index.vue
│  │  orderList.vue
│  │
│  └─detail
│          analysis.vue
│          count.vue
│          forecast.vue
│          publish.vue
│
└─router
        index.js

###写在最后，一个练手小项目，不足之处还请指出，大家共同进步