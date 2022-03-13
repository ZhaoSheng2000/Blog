### 正则表达式匹配url

正则是在GitHub上[learn-regex](https://github.com/ziishaned/learn-regex/blob/master/translations/README-cn.md)学的。

进入正题：匹配URL中的param，value
```
let str = 'http://www.aaa.com?a=12aA1&b21=wwW1&ccc=123'

let key = str.match(/\w*=/g) //   [ 'a=', 'b21=', 'ccc=' ]
let newkey = key.map(k => {
    return k.split('=').join('') //[ 'a', 'b21', 'ccc' ]
})
let value = str.match(/=\w*/g) //[ '=12aA1', '=wwW1', '=123' ]
let newvalue = value.map(v => {
    return v.split('=').join(''); //[ '12aA1', 'wwW1', '123' ]
})

let obj = [];
for (let i = 0; i < newkey.length; i++) {
    let kv = {
        key: newkey[i],
        value: newvalue[i]
    }
    obj.push(kv)
}
console.log(obj);

```


