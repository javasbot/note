高德地图API使用记录

```
const oneMarker = new AMap.Marker({
offset: new AMap.Pixel(-3, -3)  `相对于基点的偏移位置 像素坐标，确定地图上的一个像素点`
});

```

- 获取polygon的点击位置：` e.lnglat`
> 中心位置 `e.target.getBounds().getCenter()`

1. 输入地址搜索，使用[AutoComplete](https://lbs.amap.com/demo/javascript-api-v2/example/input/get-input-data)，显示返回的搜索结果列表，用户点击一个位置
