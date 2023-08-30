#React
## 声明周期
构造->渲染->组建->渲染->...

1.挂载阶段（Mounting）：

+ constructor(): 在组件被创建时调用，用于初始化状态和绑定方法。
+ static getDerivedStateFromProps(props, state): 在组件实例化和接收新的props时调用，用于根据props更新state。
+ render(): 必须实现的方法，返回组件的JSX结构。
+ componentDidMount(): 在组件挂载到DOM后调用，可以进行异步操作、订阅事件等。

2.更新阶段（Updating）：

+ static getDerivedStateFromProps(props, state): 在接收新的props时调用，用于根据props更新state。
+ shouldComponentUpdate(nextProps, nextState): 在更新之前调用，用于决定是否重新渲染组件。
+ render(): 必须实现的方法，返回组件的JSX结构。
+ componentDidUpdate(prevProps, prevState): 在组件更新后调用，可以进行DOM操作或异步操作。

3.卸载阶段（Unmounting）：

+ componentWillUnmount(): 在组件从DOM中移除之前调用，用于清理定时器、取消订阅等。
此外，还有一些其他的生命周期方法，它们在特定情况下会被调用：

+ static getDerivedStateFromError(error): 在子组件抛出错误时调用，用于渲染备用UI。
+ componentDidCatch(error, info): 在子组件抛出错误后调用，用于记录错误信息。


