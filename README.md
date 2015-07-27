# mapv - 方便的地图打点工具

TIPS:

mapv 是一款基于百度地图的海量点打点工具，用户可以通过直接打点，热力图等方式展示数据。

## 示例

访问[示例地址](http://huiyan-fe.github.io/mapv/examples/)

### 示例代码

#### 创建mapv对象
```js
// 第一步创建mapv示例
var mapv = new Mapv({
    map: map  // 百度地图的map实例
});
```

#### 创建点数据图层
```js

// 创建一个图层
var layer = new Mapv.Layer({
    zIndex: 3, // 图层的层级
    mapv: mapv, // 对应的mapv
    dataType: 'point', // 数据类型，point:点数据类型,polyline:线数据类型,polygon:面数据类型
    //数据，格式如下
    data: [
        {
            lng: 116.46507, // 经度
            lat: 39.929101, // 纬度
            count: 1 // 当前点的权重值
        },
        {
            lng: 116.43507,
            lat: 39.909101,
            count: 2
        }
    ],
    drawType: 'simple', // 渲染数据方式, simple:普通的打点,
    // 渲染数据参数
    drawOptions: {
        fillStyle: "rgba(255, 255, 50, 1)",  // 填充颜色
        strokeStyle: "rgba(50, 50, 255, 0.8)", // 描边颜色，不传就不描边
        lineWidth: 5, // 描边宽度
        radius: 5, // 半径大小
        unit: 'px' // 半径对应的单位，px:默认值，屏幕像素单位,m:米,对应地图上的大约距离,18级别时候1像素大约代表1米
    }
});
```
#### 创建线数据图层
```js
var layer = new Mapv.Layer({
    mapv: mapv,
    dataType: 'polyline',
    data: [
        {
            geo: [
                [116.39507, 39.879101],
                [116.49507, 39.889101],
                [116.46507, 39.929101],
                [116.43507, 39.909101]
            ],
            count: 10
        }
    ],
    drawType: 'simple',
    zIndex: 5,
    animation: true,
    drawOptions: {
        lineWidth: 2,
        strokeStyle: "rgba(0, 0, 255, 1)"
    },
    animationOptions: {
        radius: 10
    }
});
```
#### 创建面数据图层
```js
var layer = new Mapv.Layer({
    zIndex: 3,
    mapv: mapv,
    dataType: 'polygon',
    data: [
        {
            geo: [
                [116.39507, 39.879101],
                [116.49507, 39.889101],
                [116.46507, 39.929101],
                [116.43507, 39.909101]
            ],
            count: 10
        }
    ],
    drawType: 'simple',
    drawOptions: {
        lineWidth: 8,
        strokeStyle: "rgba(255, 255, 0, 1)",
        fillStyle: "rgba(255, 0, 0, 0.8)"
    }
});
```

#### bubble类型
![bubble类型](/doc/asset/img/bubble.png)

#### choropleth 类型
![bubble类型](/doc/asset/img/choropleth.png)

#### cluster 类型
![bubble类型](/doc/asset/img/cluster.png)

#### density 类型
![bubble类型](/doc/asset/img/density.png)

#### heatmap 类型
![bubble类型](/doc/asset/img/heatmap.png)
