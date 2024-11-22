1. server相关API的妙用
> 有的需求需要把React组件渲染成html DOM的字符串，比如高德地图的InfoWindow的content支持HTML要素字符串或者HTMLElement对象，将组件antd的Rate渲染成HTML字符串，可以使用[renderToStaticMarkup](https://zh-hans.react.dev/reference/react-dom/server/renderToStaticMarkup)

``` javascript
const Ratehtml = renderToStaticMarkup(
	<Rate
	 count={1}
	/>
);
  InfoWindowRef.setContent(`<div>infowindow的标题${Ratehtml}</div>`)
```
2. useContext的渲染优化
> useMemo是无效的，即使组件已被记忆化，当其使用的 context 发生变化时，它仍将重新渲染。记忆化只与从父组件传递给组件的 props 有关。
- 拆分Context
- 拆分组件为两层
[见代码](https://segmentfault.com/q/1010000044248290/a-1020000045496543)
