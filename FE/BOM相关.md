### 元素滚动方法
1. 顶部或底部元素使用[scrollIntoView](https://developer.mozilla.org/zh-CN/docs/Web/API/Element/scrollIntoView)
2. 外层滚动容器使用`div.scrollTop = div.scrollHeight` 没有动效，如果内容是异步获取的话相对最准确
3. 外层滚动容器使用 ``` div.scrollTo({
			// 	top: div.scrollHeight - div.clientHeight,
			// 	behavior: 'smooth'
			// }); ``` 和`scrollIntoView`一样，如果内容是异步获取的话，有时候不会滚动最底部
