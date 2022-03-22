# FootprintMap
blog's footprint map
# 使用方式

## 克隆项目

**将足迹地图克隆到本地**

```
git clone https://github.com/Astotaben/FootprintMap.git
```

## 修改地图样式

```html
	<!--background-color: 地图背景颜色-->
	<div id="map" style="background-color:#353535"> </div>
	<script>
		$('#map').vectorMap({

			// 此处更改地图
			map: 'cn_merc_en',   // 中国地图
			//map: 'us-aea',     // 美国地图
			//map: 'world-mill', // 世界地图


			backgroundColor: 'transparent',
			zoomMin: 0.9, // 鼠标缩放时的最小比例
			zoomMax: 2.4, // 鼠标缩放时的最大比例
			focusOn: {
				x: 0.55,
				y: 2,
				scale: 0.9
			},
			regionStyle: {
				initial: {
					fill: '#e5e5e5',   // 地图颜色
					"fill-opacity": 1, // 省份（州）是否隐藏，鼠标滑动时显示; 1：显示，2：隐藏。
					stroke: 'none',
					"stroke-width": 0,
					"stroke-opacity": 1
				},
				hover: {
					fill: '#ccc',  // 鼠标滑动至某省份的高亮颜色。
					"fill-opacity": 0.8
				},
				selected: {
					fill: 'yellow'
				},
				selectedHover: {}
			},
			markerStyle: {
		        initial: {
		            fill: '#fd8888', // 足迹位置的填充颜色
		            stroke: '#fff'   // 足迹位置的描边颜色
		        },
				hover: {
					fill: '#fd2020', // 鼠标滑动至足迹位置后的填充颜色
					stroke: '#fff',  // 鼠标滑动至足迹位置后的描边颜色
					"fill-opacity": 0.8
				},
		    },
		});
	</script>
</html>
```

参照代码注释修改颜色和相关样式。

## 配置足迹数据

```javascript
	markers: [ // 足迹位置

		// {latLng: [经度（保留两位小数）, 纬度（保留两位小数）], name: '城市名称'},
		// 推荐查询经纬度网站：http://www.gpsspg.com/maps.htm

		{latLng: [39.90, 116.41], name: '北京'},
		{latLng: [31.24, 121.50], name: '上海'},

		{latLng: [46.06, 122.06], name: '内蒙古 - 乌兰浩特'}
	]
```

- **latLng：** 为足迹的经纬度，可以通过 https://jingweidu.bmcx.com/ 查询得到
- **name：** 足迹地点的名称

```javascript
var freq = [10, 10, 2, 1, 3, 3];
...
...
series: {
             markers: [{
             attribute: 'r',
             scale: [4, 8],
             values: freq
             }]
          },
```

- freq: 足迹地点的到访次数，范围为 [1, 10]

## 部署到博客

将足迹数据修改完毕后，将**项目传到你的 github 中进行托管，然后启用你的足迹地图项目的 github Page 服务，会得到服务地址： http://xxxx/xxxx/.**

**然后利用 iframe 将足迹地图内嵌到你博客中的相应位置，示例代码如下：**

```html
<iframe style="max-width: 100%" 
      frameborder="no" 
      border="0" 
      marginwidth="0" 
      marginheight="0" 
      width="100%" 
      height="750px" 
      src="替换成你的足迹地图链接">                                        
</iframe>
```

把制作好的足迹地图文件放在服务器上，把访问连接放在 `src` 中。

可适配手机端和等比例缩放。

# 参考
[博客中添加足迹地图](https://sunyunzeng.com/%E5%8D%9A%E5%AE%A2%E4%B8%AD%E6%B7%BB%E5%8A%A0%E8%B6%B3%E8%BF%B9%E5%9C%B0%E5%9B%BE/)

[教你用 jVectorMap 制作属于自己的旅行足迹](https://github.com/HelloWuJiaYi/jVectorMap-Footprint)

[JVectorMap基础知识](https://www.kancloud.cn/albafica_/thinkphp5/269578)

[JVectorMap](https://jvectormap.com/)
