## Js实现导出数据到xls文件
`基本思路:` 获取html table的字符串,将其值转换为base64类型表示xls类型的数据,然后通过设置a标签的download属性的值为这个base64类型的数据将xls文件下载下来.

`文件: exportToXls.js`

#### exportToExcel 输入参数以及格式
> filename: 下载文件的文件名
> html: html table的字符串

#### genTableStr 生成html table的字符串
> header: 表头数据, 包含对象的数组,每个对象包含表头的名称和对应数据的key

```js
var header = [{
	title: 'ID',
	key: 'id'
}, {
	title: '姓名',
	key: 'name'
}, {
	title: '年龄',
	key: 'age'
}]
```

>表格数据: 包含对象的数组

```js
var data = [{
	id: 1,
	name: '张三',
	age: 20
}, {
	id: 2,
	name: '李四',
	age: 18
}]
```

#### 举例
```js
var tableHtml = genTableStr(header, data);
exportToExcel('测试', tableHtml);
```

## Js实现导出数据到txt文件
`基本思路:` 基本思路同上，需要拼一个base64的字符串,不同的地方就是需要把data设置成text/plain属性

`文件: exportToText.js`

#### 举例
```js
var fileName = 'test.txt';
var content = 'test\n'; //支持换行符，制表符等转移字符
exportToText('测试', tableHtml);
```

## Js实现下载文件
`基本思路:` 利用a标签的download属性

## Js实现有层次的打印JSON
`基本思路:` 利用递归思想,每一次递归就在字符串前多加一个制表符

`文件: printJson.js`


### 举例
```js
var test = {
    a: 'a',
    b: 'b',
    c: {
        c1: 'c1',
        c2: 'c2',
        c3: {
            c3: 'c3',
            c4: [5, 6, 7]
        }
    },
    d: [1, 2, 3]
};
console.log(printJSON(test));
```

输出结果

```
a:a
b:b
	c1:c1
	c2:c2
		c3:c3
		c4:[5,6,7]
d:[1,2,3]
```
