1. 清除在已有内容的canvas上层叠的图层(如在canvas上一段话上的背景色)

``` JavaScript
// 1. 将原始不包含背景色的图层保存成图片，将原始的context保存到ref；2. 需要跳转到新的页码或高亮新的一段话时，先用原来的context在原始位置填充原始图层的图片以实现去掉层叠在文本上的背景色
		if (tempSaveDataRef.current?.prevImg) {
			const { prevImg, x: prevX, y: prevY, prevContext } = tempSaveDataRef.current;
			prevContext.putImageData(prevImg, prevX, prevY);
tempSaveDataRef.current = null
		}
tempSaveDataRef.current = {x, y , prevImg: current2dContext.getImageData(x, y, width, height), prevContext}
// 后面就是画矩形的逻辑 fillStyl、fillRect等
```
