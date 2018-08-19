# JavaScript 第二节课

## 字符串函数
1.  查找字符串中指定位置的字符 ： charAt();
    ```js
    var str = 'lallalalljfjkkklkkkkddkld';
    var strRs = str.charAt(9);
    console.log(strRs);
    ```

2. 查找某一个子串出现的位置 : indexOf(); 如果找到该子串 返回该字符串的第一个字符的下标，如果不存在 则返回 -1
    ```js
    var str2 = 'hello word !';
    var index = str2.indexOf('word');
    console.log(index);
    ```

3. 从字符串中截取指定长度的子串 slice(start, end); 获取到的子串不包括结束位置的字符
    ```js
    var str3 = 'hello word !';
    var strRs = str3.slice(0, 5);
    console.log(strRs);

    var strRs2 = str3.slice(-6, str3.length);
    console.log(strRs2);
    ```

4. 根据指定长度来获取子串 substr(start, length); start: 开始位置  length: 要截取子串的长度
    ```js
    var str = 'Hello JavaScript !';
    var rs = str.substr(0, 5);
    console.log(rs);

    var rs2 = str.substr(-12, 10);
    console.log(rs2);
    ```


# 数据类型转换
## 隐式转换
### 其他数据类型转换为字符串类型
1. 只要其他数据和字符串进行相加操作，其他数据类型就会被隐式转换为字符串
    ```js
    var str = '2';
    var num = 100;
    var rs = str + num;
    console.log(typeof(str));
    console.log(typeof(num));
    console.log(rs);
    console.log(typeof(rs));
    ```

2. 其他数据类型转换为数字类型 除了加法之外，数字和数字字符串相互运算，数字字符串类型会转换为数字类型再运算,数字和非数字字符串相互运算，结果为NaN
    ```js
    var num1 = '100';
    var num2 = 200;
    console.log(num1 + num2);
    console.log(num1 - num2);
    console.log(num1 * num2);
    console.log(num1 / num2);

    var str2 = '100a';
    console.log(str2 + num2);
    console.log(str2 - num2);
    console.log(str2 * num2);
    console.log(str2 / num2);
    ```

3. null 会隐式转换为0
    ```js
    var num1 = 5;
    var num2 = null;
    console.log(num1 + num2);
    ``` 

4. 布尔类型转换为数字类型  true会隐式转换为1 false会隐式转换为0
    ```js
    var trueValue = true;
    var falseValue = false;
    console.log(trueValue * 5);
    console.log(trueValue + 5);
    console.log(falseValue * 5);
    console.log(falseValue + 5);
    ```

5. NaN 无法隐式转换为数字 
    ```js
    console.log(NaN + 5);
    ```

### 其他类型转换为Boolean 类型
1. 非0数字或者非空字符串 隐式转换为true  undefined 和 null,NaN 会隐式转换为false
    ```js
    if (1) {
    console.log(`真`);
    } else {
        console.log(`假`);
    }

    if (0) {
        console.log(`真`);
    } else {
        console.log(`假`);
    }

    if (undefined) {
        console.log(`真`);
    } else {
        console.log(`假`);
    }

    if (null) {
        console.log(`真`);
    } else {
        console.log(`假`);
    }

    if (NaN) {
    console.log(`真`);
    } else {
        console.log(`假`);
    }

    if ('') {
        console.log(`真`);
    } else {
        console.log(`假`);
    }
    ```


## 强制类型转换
1. String(); Number(); parseInt()
    ```js
    var num = 123456;
    var rs = String(num);
    var numStr = '123456';
    var numRs = Number(numStr);
    var str2 = 'abc123456';
    // console.log(Number(str2));

    var numStr3 = '123abc';
    var rs2 = parseInt(numStr3);
    var numStr4 = 333.3333666;
    var rs3 = parseInt(numStr4);  // 取整
    console.log(rs2);
    console.log(rs3);
    ```


# 三目运算符（三元运算符）
1. 语法 express1 ? express2 : express3
* 当express1 为true时执行express2 否则执行 express3
    ```js
    3 > 1 ? console.log('express2') : console.log('express3');

    var a = 80;
    var b = 200;
    var rs = num(a, b);
    console.log(rs);

    function num(val1, val2) {
        return val1 > val2 ? val1 : val2;
    }
    ```

# 条件语句
1. if(判断语句){为true时执行}else{为false时执行} 语句
    ```js
    if (3 > 2) {
        console.log(`true`);
    } else {
        console.log(`false`);
    }

    var num = 99;

    if (num == 100) {
        console.log(`学霸`);
        return;
    } else if (num < 100 && num > 90) {
        console.log(`优秀`);
        return;
    } else if (num < 90 && num > 80) {
        console.log(`优良`);
        return;
    } else if (num < 80 && num >= 60) {
        console.log(`及格，还需努力`);
        return;
    } else if (num < 60 && num >= 0) {
        console.log(`不及格`);
        return;
    } else {
        console.log(`你输入的分数不符合规范`);
    }
    ```

2. switch() {} 缺点 无法进行范围判断 break 防止穿透
    ```js
    var n = 100;

    switch (n) {
        case 10:
            {
                console.log(`我是${n}`);
                break;
            }
        case 100:
            {
                console.log(`我是${n}`);
                break;
            }
        default:
            {
                console.log(`错误`);
                break;
            }
    }
    ```

# 循环语句
* 循环：重复做某一件事情.在编程中为重复执行某一段代码
1. for(expression1;expression2;expression3){重复执行的代码片段}
* expression1 循环条件的起始值
* expression2 循环执行的条件
* expression3 循环执行结束的条件
    ```js
    for(let i = 0;i < 10; i ++) {
        console.log(`重复执行的代码片段`);
    }
    ```
* 嵌套循环

    ```html
    <!DOCTYPE html>
    <html lang="en">

    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>嵌套循环</title>
    </head>

    <body>
        <script type="text/javascript">
            for (let i = 1; i < 10; i++) {
                for (let k = 1; k < (2 * i); k++) {
                    document.write('*');
                }
                document.write('<br/>')
            }
        </script>
    </body>

    </html>
    ```
2. while (循环条件) {循环体}
    ```js
    var i = 0;

    while (i < 10) {
        console.log(i);
        i++;
    }
    ```

3. do...while() 循环
* do {循环体} while (循环条件);
    ```js
    var money = 1;

    do {
        console.log(`money为${money}`);
        money++;
    } while (money <= 20)
    ```

# 跳出循环
1. break 结束整个循环
    ```js
    for (let i = 1; i <= 10; i++) {
        if (i == 5) {
            break;
        }
        console.log(i);
    }
    ```

2. continue 跳过单次循环,进行下一次循环
    ```js
    for (let i = 1; i <= 10; i++) {
        if (i == 5) {
            continue;
        }
        console.log(i);
    }
    ```


# 数组
## 遍历数组元素
1. for 循环遍历

    ```js
    var arr = ['11', '22', '33', '44', '55'];

    for (let i = 0; i < arr.length; i++) {
        console.log(arr[i]);
    }
    ```
2. while循环遍历
    ```js
    var arr = ['11', '22', '33', '44', '55'];

    var i = 0;

    while (i < arr.length) {
        console.log(arr[i]);
        i++;
    }
    ```
3. for in 循环遍历
    ```js
    var arr = ['11', '22', '33', '44', '55'];

    for (let index in arr) {
        console.log(arr[index]);// 访问对象属性的方式访问
    }
    ```
4. forEach 遍历
* 缺点 1：不能break 结束循环 2：不能使用 return 返回结果
* 优点 短小精悍，比价明确的实现我们需要的效果
    ```js
    var arr = ['11', '22', '33', '44', '55'];

    arr.forEach(function (value) {
        console.log(value);
    })
    ```
## 操作数组元素
1. every() 用于检测所有元素是否都满足指定的条件
* 如果所有元素都满足条件则返回true
* 如果其中的一个元素不满足条件则返回false
    ```js
    var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];

    var rs = arr.every(function (value) {
        return value <= 5;
    })

    console.log(rs);
    ```
2. filter() 过滤数组函数
    ```js
    var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];

    var rs = arr.filter(function(value) {
        return value <= 6;
    })

    console.log(rs);
    ```
3. indexOf() 查询元素的数组中的位置 如果不存在则返回-1
    ```js
    var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];

    var rs = arr.indexOf(4);
    console.log(rs);
    ```
4. join(express1) 将数组元素用特殊字符合并为一个字符串 express1 为特殊字符
* 如果express1为空，默认添加(,)号
    ```js
    var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];

    var rs = arr.join('-');
    console.log(rs);
    ```
5. map() 方法返回一个新数组，数组中的元素为原始数组元素调用函数处理后的值
* map() 方法按照原始数组元素顺序依次处理元素。
* map() 不会对空数组进行检测。
* map() 不会改变原始数组。
    ```js
    var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];

    var rs = arr.map(function(value) {
        return value * 10;
    })
    ```
6. reverse() 翻转数组元素
    ```js
    var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];

    var rs = arr.reverse();

    console.log(rs);
    ```
7. some() 方法用于检测数组中的元素是否满足指定条件（函数提供）。
    ```js
    var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];

    var rs = arr.some(function(value) {
        return value >= 8;
    })

    console.log(rs);
    ```
8. sort() 方法用于对数组的元素进行排序。
    ```js
    var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 235, 122];

    // 升序排序
    arr.sort(function (a, b) {
        return a - b;
    })

    console.log(arr);

    // 降序
    arr.sort(function (a, b) {
        return b - a;
    })

    console.log(arr);

    // 安字母的顺序排序
    arr.sort();

    console.log(arr);
    ```
9. splice(arg1, arg2, arg3) 方法向/从数组中添加/删除项目，然后返回被删除的项目。
* arg1 要从哪个位置插入项目
* arg2 从arg1这个位置开始要删除多少个项目
* arg3 要插入的项目
    ```js
    var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 235, 122];

    // 添加项目
    // arr.splice(0,0, 'tomcat');

    // console.log(arr);

    // 删除
    // arr.splice(0, 1);

    // console.log(arr);

    // 从中间插入项目
    arr.splice(arr.length / 2,0 , 'mid');

    console.log(arr);
    ```
10. pop() 方法用于删除并返回数组的最后一个元素。
* 请注意，这也会改变数组的长度
    ```js
    var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 235, 122];

    arr.pop();

    console.log(arr);
    ```
11. push() 方法可向数组的末尾添加一个或多个元素，并返回新的长度。
* 该方法会改变数组的长度。
    ```js
    var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 235, 122];

    arr.push(666);

    console.log(arr);
    ```
12. shift() 方法用于把数组的第一个元素从其中删除，并返回第一个元素的值。
* 该方法会改变数组的长度。
* 要删除并返回数组的最后一个元素，请使用 pop() 方法。
    ```js
    var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 235, 122];

    arr.shift();

    console.log(arr);
    ```
13. unshift() 方法可向数组的开头添加一个或更多元素，并返回新的长度。
* unshift() 方法将把它的参数插入 arrayObject 的头部，并将已经存在的元素顺次地移到较高的下标处，以便留出空间。该方法的第一个参数将成为数组的新元素 0，如果还有第二个参数，它将成为新的元素 1，以此类推。
* unshift() 方法不创建新的创建，而是直接修改原有的数组。
* 该方法会改变数组的长度。
* unshift() 方法无法在 Internet Explorer 中正确地工作！
* 要把一个或多个元素添加到数组的尾部，请使用 push() 方法。
    ```js
    var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 235, 122];

    arr.unshift('one');

    console.log(arr);
    ```
## 字符串转数组

1. split(separator, howmany) 方法用于把一个字符串分割成字符串数组。
* separator	必需。字符串或正则表达式，从该参数指定的地方分割 stringObject。
howmany	可选。该参数可指定返回的数组的最大长度。如果设置了该参数，返回的子串不会多于这个参数指定的数组。如果没有设置该参数，整个字符串都会被分割，不考虑它的长度。
* 如果把空字符串 ("") 用作 separator，那么 stringObject 中的每个字符之间都会被分割。
* String.split() 执行的操作与 Array.join 执行的操作是相反的。
    ```js
    var str = "Hello word!";

    var strArr = str.split(' ');

    console.log(strArr);
    ```

# 函数
* 函数是由事件驱动的或者当它被调用时执行的可重复使用的代码块。
## JavaScript 函数语法
1. 函数就是包裹在花括号中的代码块，前面使用了关键词 function：
* 一般情况下，形参和实参会一一对应
* 当调用函数时，并且为函数传递实参时，实参会被保存到arguments对象中
    ```js
    function functionname(形参列表)
    {
    这里是要执行的代码
    }
    // 调用
    functionname(实参列表);

    function test(arg1, arg2) {
    console.log(arg1);
    console.log(arg2);
    console.log(arguments);
    }

    test('11111111', '222222222', 3333333);

    function test() {
    for (let i in arguments) {
        console.log(arguments[i]);
        }
    }

    test(111, 222, 333, 444, 555, 666);
    ```
2. 匿名函数
* 语法
    ```js
    (function() {
        console.log('Hello Word !');
    })();

    (function () {
        console.log('Hello Word !');
    }());

    var func = function () {
        // 执行的代码块
    }

    func();
    ```

# 面向对象
## 创建对象得到方法
* 创建对象的同时为该对象添加属性和方法
1. 字面量方式创建对象
    ```js
    var obj = {
    height: 180,
    weight: 150,
    age: 22,
    play: function () {
        console.log(`玩游戏`);
    }
    };

    // 访问对象的属性
    // 1. 通过点语法访问

    console.log(obj.height);
    console.log(obj.weight);
    obj.play(); // 调用对象的方法

    // 2. 通过字符串方式获取对象属性

    console.log(obj['weight']);
    console.log(obj['height']);
    ```
2. 通过Object()构造函数创建对象
    ```js
    var obj = new Object();

    obj.name = 'tomcat';

    obj.age = 22;

    obj.phone = 10086;

    obj.play = function() {
        console.log(`打游戏`);
    }



    function createObjectFactory(name, age, play) {
        let obj = new Object();

        obj.name = name;

        obj.age = age;

        obj.play = function(value) {
            console.log(value);
        }

        return obj;
    }

    var rs = createObjectFactory('刘泽', 20);

    console.log(rs);

    rs.play('打游戏');
    ```