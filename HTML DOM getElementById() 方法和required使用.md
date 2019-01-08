# java
HTML DOM getElementById() 方法
HTML DOM Document 对象

定义和用法
getElementById() 方法可返回对拥有指定 ID 的第一个对象的引用。

语法
document.getElementById(id)
说明
HTML DOM 定义了多种查找元素的方法，除了 getElementById() 之外，还有 getElementsByName() 和 getElementsByTagName()。

不过，如果您需要查找文档中的一个特定的元素，最有效的方法是 getElementById()。

在操作文档的一个特定的元素时，最好给该元素一个 id 属性，为它指定一个（在文档中）唯一的名称，然后就可以用该 ID 查找想要的元素。

实例
例子 1
<html>
<head>
<script type="text/javascript">
function getValue()
  {
  var x=document.getElementById("myHeader")
  alert(x.innerHTML)
  }
</script>
</head>
<body>

<h1 id="myHeader" onclick="getValue()">This is a header</h1>
<p>Click on the header to alert its value</p>

</body>
</html>
例子 2
getElementById() 是一个重要的方法，在 DOM 程序设计中，它的使用非常常见。我们为您定义了一个工具函数，这样您就可以通过一个较短的名字来使用 getElementById() 方法了：

function id(x) {
  if (typeof x == "string") return document.getElementById(x);
  return x;
  }
上面这个函数接受元素 ID 作为它们的参数。对于每个这样的参数，您只要在使用前编写 x = id(x) 就可以了。

---------------------------------------------------------------------------------
HTML 5 <input> required 属性
HTML 5 <input> 标签

实例
带有必填字段的表单：

<form action="demo_form.asp" method="get">
  Name: <input type="text" name="usr_name" required="required" />
  <input type="submit" />
</form>
亲自试一试
定义和用法
required 属性规定必需在提交之前填写输入字段。

如果使用该属性，则字段是必填（或必选）的。

注释：required 属性适用于以下 <input> 类型：text, search, url, telephone, email, password, date pickers, number, checkbox, radio 以及 file。

-----------------
