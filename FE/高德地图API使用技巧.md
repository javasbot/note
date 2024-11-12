高德地图API使用记录

```
const oneMarker = new AMap.Marker({
offset: new AMap.Pixel(-3, -3)  `相对于基点的偏移位置 像素坐标，确定地图上的一个像素点`
});

```

- 获取polygon的点击位置：` e.lnglat`
> 中心位置 `e.target.getBounds().getCenter()`

1. 输入地址搜索，使用[AutoComplete](https://lbs.amap.com/demo/javascript-api-v2/example/input/get-input-data)，显示返回的搜索结果列表，用户点击一个位置

2. // 撤销 先close再open就不会出现之前图形的白点 多边形编辑器的撤销和恢复，
```
const commandStack: any = {
	history: [],
	currentStep: -1,
	push(command) {
		this.history.push(command);
		this.currentStep++;
	},
	undo() {
		// 撤销操作
		console.log('撤销', this.currentStep);
		if (this.currentStep - 1 < 0) return;
		this.currentStep--;
		return this.history[this.currentStep];
	},
	redo() {
		// 恢复操作
		console.log('恢复操作', this.currentStep);
		if (this.currentStep + 1 > this.history.length - 1) return;
		this.currentStep++;
		return this.history[this.currentStep];
	}
};
```

```
  polygonEditorRef.current.close(); // 关闭编辑器
  const prevPath = commandStack.undo(); // 上一步的path
  polygonRef.current.setPath(prevPath); // 修改多边形的path
  polygonEditorRef.current.open(); // 重新打开编辑器
```
