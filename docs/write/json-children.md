### 查找json中的children路径

现有如下json（简化为对象），已知每个节点id唯一，编写findNode(id)，返回路径，如findNode(5) 输出 1->4->5
```
{
  id: 1,
  children: [
    { id: 2, children: [{ id: 3, children: [] }] },
    {
      id: 4,
      children: [
        { id: 5, children: [] },
        { id: 6, children: [] },
      ],
    },
    { id: 7, children: [] },
  ],
};
```
> dfs+辅助数组完成

```
function getNode(data, id, indexArray) {
    let arr = Array.from(indexArray)
    for (let i = 0; i < data.length; i++) {
        arr.push(data[i].id); //首先将这一层的id推进去
        if (data[i].id === id) { //找到了就返回结果
            return arr.splice(',').join('->'); //处理成要求的输出格式
        }
        let children = data[i].children; //当前的children
        if (children && children.length) {
            let result = getNode(children, id, arr) //dfs
            if (result) return result
        }
        arr.pop();//遍历以后没有
    }
    return false; //没有找到就返回false
}
console.log(getNode(data, 10, [])); //1->4->5
```