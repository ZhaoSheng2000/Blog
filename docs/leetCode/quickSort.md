## 快速排序
>递归调用，撸起袖子就是干！

1. 取中间「基准数」
2. 小于「基准数」，移到「基准数」左边
3. 大于「基准数」，移到「基准数」右边
4. 左右两边子集重复1，2，3.直到所有子集剩下一个元素

```
var quickSort = function (arr) {
    if (arr.length <= 1) return arr;//终止条件
    let midIdx = Math.floor(arr.length / 2);//中间基准数下标
    let mid = arr.splice(midIdx, 1)[0];//中间基准数
    let left = [];
    let right = [];
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] < mid) {
            left.push(arr[i])
        } else {
            right.push(arr[i])
        }
    }
    return quickSort(left).concat([mid], quickSort(right));
}
```
