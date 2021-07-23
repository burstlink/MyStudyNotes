## bke项目nodejs一些积累

* 获取当前时区某一时刻的weekday

```javascript
// 获取当前时区当前的时间
const todayTimeZone = new Date().toLocalString(""en-US", {timeZone: "America/New_York"});
// 根据当前时间获取星期几
const weekDayTimeZone = new Date(todayTimeZone).getDay();
```

* 合并两个obejct

```javascript
// 方法一：
const first = {  
  name: 'Marcus',
  sub: { eyes: 'blue' }
}

const second = {  
  name: 'Node.js',
  sub: { hair: 'brown' }
}

const spread = { ...first, ...second } 
// { name: 'Node.js',
//   sub: { hair: 'brown' }
// }

// 方法二：

const first = {  
  name: 'Marcus',
  sub: { eyes: 'blue' }
}

const second = {  
  name: 'Node.js',
  sub: { hair: 'brown' }
}

const merged = Object.assign({}, first, second)  
// { name: 'Node.js',
//   sub: { hair: 'brown' }
// }

//方法三：
const merge = require('deepmerge')

const first = {  
  name: 'Marcus',
  sub: { eyes: 'blue' }
}

const second = {  
  name: 'Node.js',
  sub: { hair: 'brown' }
}

const merged = merge(first, second)

// { name: 'Node.js',
//   sub: { eyes: 'blue', hair: 'brown' }
// }

```

* 多组判断的三元运算
```javascript
function example(…) {
    return condition1 ? value1
            : condition2 ? value2
            : condition3 ? value3
            : value4;
    }
    // Equivalent to:

function example(…) {
    if (condition1) { return value1; }
    else if (condition2) { return value2; }
    else if (condition3) { return value3; }
    else { return value4; }
}
```

* 对object进行过滤
```javascript
const {pickBy} = require("loash");
pickBy({...obejct}, element => {
    return condition;
})
```
* 取obejct的key或者value的List
```javascript
const {values, keys} = require("loash");
keys(obeject);
values(obeject);
// 或者
Object.keys(obj)
Object.values(obj) 
```

* 取Array的最后一个值
```javascript
//方法1
array.slice(-1)[0]
//方法2 不会修改原来的array
array.slice(-1).pop()
//方法3
array[array.length-1]
//方法4
const {last} = require("loash");
last(array)
```

* 按照顺序执行promise列表任务
```javascript
[func1, func2, func3].reduce((p, f) => p.then(f), Promise.resolve()).then(result3 => { /* use result3 */ });
//或者函数式编程形式
const applyAsync = (acc,val) => acc.then(val);
const composeAsync = (...funcs) => x => funcs.reduce(applyAsync, Promise.resolve(x));
```
