# 项目目录及使用

整理目录文件，对个别常用功能点描述


## 项目文件目录

    .
    ├── README.md                      ....................  // 项目描述文档                                         
    ├── babel.config.js                ....................  //                                      
    ├── package.json                   ....................  // 依赖包配置文档                  
    ├── public                         ....................  //            
    │   ├── favicon.ico                ....................  //                       
    │   ├── index.html                 ....................  //                      
    │   └── logo.ico                   ....................  //                   
    ├── src                            ....................  // 主文件夹       
    │   ├── App.vue                    ....................  //                  
    │   ├── assets                     ....................  // 静态文件 （图片）              
    │   │   └── logo.png               ....................  //                        
    │   ├── components                 ....................  // 公用组件                   
    │   │   ├── IScrollbar.vue         ....................  //    滚动条组件                       
    │   │   ├── SvgIcon.vue            ....................  //    svg字体图标组件                    
    │   │   ├── footer                 ....................  //    底部组件文件夹                  
    │   │   │   └── TimerBar.vue       ....................  //       时间进度条组件                         
    │   │   └── tools                  ....................  //    工具栏组件                 
    │   │       └── Search.vue         ....................  //       搜索组件                       
    │   ├── config                     ....................  // 公用配置                 
    │   │   └── index.js               ....................  //    服务器配置文件                    
    │   ├── icons                      ....................  // svg图标文件夹                
    │   │   ├── index.js               ....................  //    svg配置                    
    │   │   └── svg                    ....................  //    svg存放文件夹               
    │   │       ├── UAV.svg            ....................  //                           
    │   │       ├── video.svg          ....................  //                             
    │   │       └── wayCar.svg         ....................  //                              
    │   ├── layouts                    ....................  // 布局组件                  
    │   │   ├── LayoutContent.vue      ....................  //    内容区组件                             
    │   │   ├── LayoutFooter.vue       ....................  //    底部区组件                            
    │   │   ├── LayoutHeader.vue       ....................  //    头部区组件                            
    │   │   ├── index.js               ....................  //                        
    │   │   └── panel                  ....................  //    内容区面板组件                 
    │   │       ├── PanelInfo.vue      ....................  //       左侧面板组件                          
    │   │       ├── PanelMap.vue       ....................  //       地图功能组件                         
    │   │       └── PanelTools.vue     ....................  //       右侧工具栏组件                           
    │   ├── lib                        ....................  // 外部引入包              
    │   │   └── maptalks               ....................  //    maptalks方法                    
    │   │       ├── MapCommon.js       ....................  //       公用方法                         
    │   │       ├── MapConfig.js       ....................  //       配置文件                         
    │   │       └── MapModule.js       ....................  //                                
    │   ├── main.js                    ....................  // 主文件                  
    │   ├── mixins                     ....................  // mixins                 
    │   │   ├── index.js               ....................  //                        
    │   │   └── modules                ....................  //   mixins模块                    
    │   │       └── pollution.js       ....................  //                                
    │   ├── router                     ....................  // 路由                 
    │   │   └── index.js               ....................  //                        
    │   ├── services                   ....................  // 请求服务                   
    │   │   ├── index.js               ....................  //                        
    │   │   └── modules                ....................  //    请求服务模块                   
    │   │       ├── login.js           ....................  //                            
    │   │       └── pollution.js       ....................  //                                
    │   ├── store                      ....................  // VUEX状态管理文件                
    │   │   └── index.js               ....................  //                        
    │   ├── styles                     ....................  // 样式文件                
    │   │   ├── base.scss              ....................  //    基础样式                     
    │   │   ├── perfect-scrollbar.scss ....................  //    滚动条样式                                  
    │   │   ├── reset-element.scss     ....................  //    重置element样式                              
    │   │   ├── reset.scss             ....................  //    全局重置样式
    │   │   ├── theme.scss             ....................  //    主题样式                      
    │   │   └── variables.scss         ....................  //    公用变量样式                          
    │   ├── utils                      ....................  // 公用方法文件夹                  
    │   │   ├── request.js             ....................  //    axios二次封装                    
    │   │   └── tools.js               ....................  //                        
    │   └── views                      ....................  // 视图                
    │       ├── Map.vue                ....................  //                       
    │       └── pages                  ....................  //   模块文件                  
    │           ├── Air.index.vue      ....................  //      环境质量模块                              
    │           ├── Pollution          ....................  //      污染源子模块文件夹                       
    │           │   └── Statistics.vue ....................  //         汇总模块
    │           └── Pollution.index.vue....................  //      污染源模块主页面                                 
    ├── vue.config.js                  ....................  // webpack配置文件                    
    ├── yarn-error.log                 ....................  //                      
    └── yarn.lock                      ....................  //             

***

## services服务项目中使用

方便接口的统一管理

1、serviecs已在mian.js全局注册绑定

    Vue.prototype.$services = Services;


2、使用过程：每个模块需在services -> modules 文件夹中对应模块js文件添加接口，

然后在组件内通过`this.$services[modules][portName]`使用；代码如下


services -> modules -> pollution.js
```javascript
// 添加接口
const pollutionServices = {
    getStatistics: {
        url: '/pollute-source/statistics',  // 接口
        server: 'polluteNew', // 请求对应服务
        type: 'get', // 请求类型
    },
}

export default pollutionServices
```

views -> pages -> Pollution -> Statistics.vue
```javascript
//获取汇总信息
async getData(){
    // 传入请求参数
    const params = {
        gridCode: '01000000',
        dataType: 'hour',
        time: 1594191600000,
    }
    const data = await this.$services.pollution.getStatistics(params)
    this.dataList =  data.data
}
```

***

## svg图标使用

```html

<svg-icon icon-class="test"></svg-icon>

//添加样式
<style>
.iconTest{color:red;font-size:16px}
</style>


```

## CDN配置

直接在配置文件（`vue.config.js`）能找到cdn对象，在对应的数据增加链接即可

```javascript
// 配置cdn
const cdn = {
    css: ["https://cdn.jsdelivr.net/npm/maptalks/dist/maptalks.css"],
    js: [
        "https://cdn.jsdelivr.net/npm/maptalks/dist/maptalks.min.js",
        "https://cdn.jsdelivr.net/npm/@sakitam-gis/maptalks-wind@1.0.0-alpha.10/dist/maptalks-wind.js", //风场
        "https://cdn.jsdelivr.net/npm/maptalks.markercluster/dist/maptalks.markercluster.min.js", //聚合
    ]
}
```