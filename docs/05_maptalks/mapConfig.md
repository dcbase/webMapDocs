MapConfig.js脚本文件主要针对地图初始化、地图服务样式、地图服务url所做的配置，将功能集中，统一处理

#### 1、变量定义
（1）MAPNAME：定义地图变量挂载到window上的名称

（2）BDLightStyle：百度地图白色风格样式

（3）BDNightStyle：百度地图暗色风格样式

（4）BDTileUrl：百度瓦片地图url

（5）BDLightUrl：百度瓦片地图url（白色风格）

（6）BDNightUrl：百度瓦片地图url（暗色风格）

（7）BDImageUrl：百度影像图服务

（8）BDTraffic：百度路况图

（9）mapConfig：地图配置

```javascript
{
    zoom: 13,
    minZoom: 3,
    maxZoom: 19,
    center: [120.2052342, 30.2489634], // 杭州
    spatialReference: {
        projection: "baidu"
    },
    maxPitch: 60,
    baseLayer: new maptalks.TileLayer("base", {
        spatialReference: {
            projection: "baidu"
        },
        urlTemplate: BDNightUrl,
        subdomains: [0, 1, 2]
    }),
}
```