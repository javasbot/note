1. 清除在canvas上层叠的画面

``` JavaScript
// 通过将缓存的图片填充会原来的位置实现去掉之前高亮的的文本背景色
		if (savedImageData.current?.preImg) {
			const { preImg, x: prevX, y: prevY } = savedImageData.current;
			curContext.putImageData(preImg, prevX, prevY);
		}
savedImageData.current.x = x;
		savedImageData.current.y = adjustY;
		savedImageData.current.preImg = curContext.getImageData(x, adjustY, width, height);
```
