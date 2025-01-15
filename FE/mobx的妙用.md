- 在react开发中遇到常见的孙组件需要调用爷组件的方法，有常见的三种方式

1. 使用context
2. 使用EventBus
3. 用mobx
```
customCallback: any = null; // 重新回答的回调

	setcallback(callback) {
		this.customCallback = callback;
	}

	triggerCustomCallback() {
		if (this.customCallback) {
			this.customCallback();
		}
	}

// 爷组件
useEffect(() => {
		store.setcallback(needCallFun);

		return () => {
			store.setcallback(null); // Clean up on unmount
		};
	}, []);
// 孙组件
onClick={() => store.triggerCustomCallback()}
```
