# 资料
[W3School JavaScript](http://www.w3school.com.cn/js/js_intro.asp)
[MDN 什么是JavaScript？](https://developer.mozilla.org/zh-CN/docs/Learn/JavaScript/First_steps/What_is_JavaScript)
[一文读懂JavaScript和ECMAScript的区别](http://developer.51cto.com/art/201711/557514.htm)
[W3School JavaScript历史](http://www.w3school.com.cn/js/pro_js_history.asp)

[Javascript高级程序设计]()

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