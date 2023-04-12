##  ReactHooks模拟生命周期

### constructor
```
class Example extends Component {
    constructor() {
        super();
        this.state = {
            count: 0
        }
    }
    render() {
      return null;
  }
}
//hooks
function Example() {
  const [count, setCount] = useState(0);
  return null;
}

```
### componentDidMount
```
class Example extends React.Component {
  componentDidMount() {
    console.log('I am mounted!');
  }
  render() {
    return null;
  }
}

//hooks
function Example() {
  useEffect(() => console.log('mounted'), []);
  return null;
}
```
useEffect 拥有两个参数，第一个参数作为回调函数会在浏览器布局和绘制完成后调用，因此它不会阻碍浏览器的渲染进程。第二个参数是一个数组

- 当数组存在并有值时，如果数组中的任何值发生更改，则每次渲染后都会触发回调。
- 当它不存在时，每次渲染后都会触发回调。
- 当它是一个空列表时，回调只会被触发一次，类似于 componentDidMount。

###  shouldComponentUpdate
```
shouldComponentUpdate(nextProps, nextState){
  console.log('shouldComponentUpdate')
  // return true 更新组件
  // return false 则不更新组件
}
//hooks
const MyComponent = React.memo(
    _MyComponent, 
    (prevProps, nextProps) => nextProps.count !== prevProps.count
)

```
React.memo 包裹一个组件来对它的 props 进行浅比较,但这不是一个 hooks，因为它的写法和 hooks 不同,其实React.memo 等效于 PureComponent，但它只比较 props。

### componentDidUpdate
```
componentDidMount() {
  console.log('mounted or updated');
}

componentDidUpdate() {
  console.log('mounted or updated');
}

//hooks
useEffect(() => console.log('mounted or updated'));
```
这里的回调函数会在每次渲染后调用，因此不仅可以访问 componentDidUpdate，还可以访问componentDidMount，如果只想模拟 componentDidUpdate，我们可以这样来实现。
```
const mounted = useRef();
useEffect(() => {
  if (!mounted.current) {
    mounted.current = true;
  } else {
   console.log('I am didUpdate')
  }
});

```
useRef 在组件中创建“实例变量”。它作为一个标志来指示组件是否处于挂载或更新阶段。当组件更新完成后在会执行 else 里面的内容，以此来单独模拟 componentDidUpdate。


### componentWillUnmount
```
componentWillUnmount() {
  console.log('will unmount');
}
//hooks
useEffect(() => {
  return () => {
    console.log('will unmount');
  }
}, []);
```
当在 useEffect 的回调函数中返回一个函数时，这个函数会在组件卸载前被调用。我们可以在这里面清除定时器或事件监听器。