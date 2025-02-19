### 元素滚动方法
1. 顶部或底部元素使用[scrollIntoView](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/scrollIntoView)
2. 外层滚动容器使用`div.scrollTop = div.scrollHeight` 没有动效，如果内容是异步获取的话相对最准确
3. 外层滚动容器使用 ``` div.scrollTo({
			// 	top: div.scrollHeight - div.clientHeight,
			// 	behavior: 'smooth'
			// }); ``` 和`scrollIntoView`一样，如果内容是异步获取的话，有时候不会滚动最底部

### Web API相关
ResizeObserver监听的父元素包含图片子元素时，如果图片子元素没有设置固定高度，图片子元素渲染出来后(onload)导致父元素高度变化时可能不会触发ResizeObserver的回调
