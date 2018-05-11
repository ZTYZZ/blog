# 资料
[W3School JavaScript](http://www.w3school.com.cn/js/js_intro.asp)

[MDN 什么是JavaScript？](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/First_steps/What_is_JavaScript)

[一文读懂JavaScript和ECMAScript的区别](http://developer.51cto.com/art/201711/557514.htm)

[W3School JavaScript历史](http://www.w3school.com.cn/js/pro_js_history.asp)


[Javascript高级程序设计]()
[W3School](http://www.w3school.com.cn/js/js_if_else.asp) 从if-else看到异常

[MDN](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/First_steps/Variables) 阅读完JavaScript第一步及JavaScript基础要件


[阅读 通过除2取余的方法来把十进制整数转化为二进制](https://baike.baidu.com/item/十进制转二进制/393189?fr=aladdin)

[阅读《javascript高级程序设计》第7章和第13章]()
# 相关的问题记录
1. 
```
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">    
    <title>IFE ECMAScript</title>
</head>
<body>        
    <input id="first-number" type="number" placeholder="第一个数字">
    <input id="second-number" type="number" placeholder="第二个数字">
    <button id="add-btn">加</button>
    <button id="minus-btn">减</button>
    <button id="times-btn">乘</button>
    <button id="divide-btn">除</button>
    <p id="result">运算结果</p>
    <script>
        var result;
        var firstNumber = document.getElementById("first-number").value;
        var secondNumber = document.getElementById("second-number").value;
        document.getElementById("add-btn").onclick = function() {
            result= firstNumber+secondNumber;
            document.getElementById("result").innerHTML = "运算结果为" + result;
        }
        document.getElementById("minus-btn").onclick = function() {
            result=firstNumber-secondNumber;
            document.getElementById("result").innerHTML = "运算结果为" + result;
        }
        document.getElementById("times-btn").onclick = function() {
            result = firstNumber*secondNumber;
            document.getElementById("result").innerHTML = "运算结果为" + result;
        }

        document.getElementById("divide-btn").onclick = function() {
            result = firstNumber/secondNumber;
            document.getElementById("result").innerHTML = "运算结果为" + result;
        }

        
    </script>
</body>
</html>
```
以上代码为什么在运行是，并不会真正实现加减乘除？说明原因～。
2. 字符串有哪些方法？
3. 字符串中的转换大小写方法是什么？调用此方法时，原字符串会改变吗？
4. 字符串的`replace()`方法了解一下？同样的子串会全部替换成功吗？还是只匹配第一个？
5. js中，字符串有`valueOf()`方法吗？
6. 字符串如何转换成数组？
7. 数组如何转换成字符串？两种方法，并说出两种方法的不同点。
8. 数组在进行push和pop方法的时候，原数组的数据变不变化，调用结束后，返回的是什么？是新数组吗？
9. 和上面类似的方法有什么？如8题。
