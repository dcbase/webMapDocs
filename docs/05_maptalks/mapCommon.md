MapCommon.js脚本文件主要封装了maptalks框架的基础公共方法

## isNumber
简介：判断是否为数字

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
| num |传入的数值| Number|   是   |  |

## zoomInOrOut
简介：设置地图的缩放

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------ |-------|-------|---|
| type|地图缩小还是放大（zoomIn｜zoomOut） | String|   是   |  |

## setMapZoom
简介：地图缩放到指定层级

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
| zoom |地图层级| Number|   是   |  |

## setPitchOrBearing
简介：设置地图倾斜、旋转

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
| type |倾斜或旋转（pitch｜bearing）| String|   是   |  |
| num |倾斜或旋转的角度| Number|   是   |  |

## flyToPoint
简介：飞行到指定位置

|参数名|描述         |参数类型|是否必选|默认值  
|-----     |------------|-------|-------|---|
| coord    |飞往的点位，传null即飞行到地图中心点| null｜Array(Number>)|   否   | 地图中心点 |
| zoom     |地图层级，传null即不缩放          | null｜Number       |   否   | 地图当前层级 |
| duration |地图飞行的时间                   | null｜Number       |   否   | 1500 |

## fitExtent
地图区域适配

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
| extent |适配范围| Extent（见maptalks官网）|   是   |  |
| zoomOffset |zoom offset| Number|   否   |  |

## baseLayerExists
判断BaseLayer图层存在与否

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
|  |  |            |      |  |

## layerExists
判断图层存在与否(BaseLayer除外)

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
| layerName |图层名| String|   是   |  |
| showError |是否显示错误信息| Boolean|   否   |  |

## setBaseLayer
添加BaseLayer

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
| name |BaseLayer名称| String|   是   |  |
| option |BaseLayer参数| Object|   是   |  |

## removeBaseLayer
移除BaseLayer图层

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
|     |            |       |       |  |

## setTileLayer
添加TileLayer图层

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
| name |图层名称| String|   是   |  |
| option |图层参数| Object|   是   |  |

## setWMSTileLayer
添加WMSTileLayer图层

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
| name |图层名称| String|   是   |  |
| option |图层参数| Object|   是   |  |

## setGroupTileLayer
添加GroupTileLaye图层

|参数名|描述            |参数类型       | 是否必选|默认值  |
|-----   |------------|-------       |-------|--------------------------------------------------------------      |
| name   |图层名称     | String       |   是   |                                                                  |
| arrays |图层数组     | Array(Object)|   是   | {type: "tile｜wmstile", name: "图层名称", option: {创建图层的参数}}  |

## setImageLayer
设置ImageLayer图层

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
| name |图层名称| String|   是   |  |
| option |图层参数| Object | Array(Object)|   是   |  |

## removeLayer
移除图层

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
| paras |图层名、图层对象| String ｜ Array(String) ｜ Layer ｜ Array(Layer)|   是   |  |

## showOrHideLayer
显示或隐藏图层

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
| layer |图层对象| Object|   是   |  |
| bool |是否隐藏| Boolean|   是   |  |

## getOrSetLayerZIndex
获取或设置图层的ZIndex

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
| layer |图层对象| Object|   是   |  |
| zinde |Z值| Number|   是   |  |
| type | {set｜get}| String|   是   |  |

## setMarker
设置marker

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
| coords |经纬度| Array(Number)|   是   |  |
| options |marker的属性信息：详情参考maptalks官网| Object|   是   |  |

## pointToJson
单个点数据转换为Json

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
| coords |经纬度| Array(Number)|   是   |  |
| props |要素的属性|Object|   是   |  |

## pointsToGeoJson
多点数据转换为Geojson

|参数名|描述         |参数类型|是否必选|默认值  
|-----|------------|-------|-------|---|
| arrys |点位数组[{ coords, properties }]| Array(Object)|   是   |  |
