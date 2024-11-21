1. server相关API的妙用
> 有的需求需要把React组件渲染成html DOM的字符串，比如高德地图的InfoWindow的content支持HTML要素字符串或者HTMLElement对象，将组件antd的Rate渲染成HTML字符串，可以使用[renderToStaticMarkup](https://zh-hans.react.dev/reference/react-dom/server/renderToStaticMarkup)

``` javascript
const Ratehtml = renderToStaticMarkup(
	<Rate
	 value={1}
	/>
);
  InfoWindowRef.setContent(`<div>infowindow的标题${Ratehtml}</div>`)
```
