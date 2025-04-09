1. react-server相关API的使用

> 有的需求需要把React组件渲染成html DOM的字符串，比如高德地图的InfoWindow的content支持HTML要素字符串或者HTMLElement对象，将组件antd的Rate渲染成HTML字符串，可以使用[renderToStaticMarkup](https://zh-hans.react.dev/reference/react-dom/server/renderToStaticMarkup)

```javascript
const Ratehtml = renderToStaticMarkup(
	<Rate
	 count={1}
	/>
);
  InfoWindowRef.setContent(`<div>infowindow的标题${Ratehtml}</div>`)
```

但是react官网[不建议在客户端代码这样做](https://zh-hans.react.dev/reference/react-dom/server/renderToString#removing-rendertostring-from-the-client-code)，改成

```javascript
const getRatehtml = useCallback((params) => {
		const div = document.createElement('div');
		const root = createRoot(div);
		flushSync(() => {
			root.render(
				<Rate
					character={() => (
						<img
							src=""
							className=""
{...params}
						/>
					)}
				/>
			);
		});
		return div.innerHTML;
	}, []);
```

2. useContext的渲染优化

> useMemo是无效的，即使组件已被记忆化，当其使用的 context 发生变化时，它仍将重新渲染。记忆化只与从父组件传递给组件的 props 有关。

- 拆分Context
- 拆分组件为两层
  [见代码](https://segmentfault.com/q/1010000044248290/a-1020000045496543)

3. 如何量化react的优化效果
   使用 `Profiler`可以检测组件使用useMemo、useCallback、memo后的变化
![企业微信截图_65863e6e-c878-406b-b9fe-3dd4e745ee78](https://github.com/user-attachments/assets/d2c4dabe-be89-43c2-a87d-2c10e9861d4c)

4. React错误处理
> 方法1: [error boundary](https://zh-hans.react.dev/reference/react/Component#catching-rendering-errors-with-an-error-boundary)
> 方法2 react-router-dom的useRouteError
```
import type { FC } from "react";

import { useRouteError } from "react-router-dom";

const ErrorBoundary: FC = () => {
  const occurredByRoute = useRouteError();

  return <>{(occurredByRoute as { message: string }).message}</>;
};

export default ErrorBoundary;

```


