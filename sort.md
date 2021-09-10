# 自定义数组对象排序

数据结构如下：

```
let obj={
        "gte300lt500": 0,//300-500
        "gte1000lt3000": 0,//1000-3000
        "gte500lt1000": 0,
        "gte10000": 0,//大于10000
        "gte3000lt5000": 0,
        "lt300": 39,//小于300
        "gte5000lt10000": 0
    }

```
按从小到大排序，思路：
1. 先转换成对象数组
2. 提取出key中的第一个数字
3. 然后通过`sort(func)`比较
代码如下：
```
let c=[]
for( let [k,v] of Object.entries(obj)){
    c.push({
            name:k,
            value:v
        })
}
c.sort((a,b)=>{
        let k=a.name.match(/\d+/g);//[500，1000]
        let j=b.name.match(/\d+/g);
        if(k[0]==j[0]){
            if(k.length==1){
                k[1]=0
            }else if(j,length=1){
                j[1]=0
            }
            return k[1]-j[1]
        }
        return k[0]-j[0]
    })
    return c;//返回排序后的对象数组
}
```
## 其他
- `Object.entries(obj)` 对象转数组,返回类似`[[key,value],[key,value],...]`的二维数组，可以用`for(let [k,v] of Array)遍历`
- `Object.keys(obj)` 获取对象的key，返回key的数组`[key1,key2,...]`
- `Object.values(obj)`获取对象的value，返回value的数组`[value1,value2,...]`
- 字符串类型的方法`match(Rexg)`根据正则表达式以数组的形式返回匹配的值，例如：`str.match(/\d+\g)`匹配数字