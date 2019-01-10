
jqGrid安装

jqGrid安装很简单，只需把相应的css、js文件加入到页面中即可。

/myproject/css/ 

	ui.jqgrid.css 
	
	/ui-lightness/ 
		/images/ 
		
		jquery-ui-1.7.2.custom.css

/myproject/js/ 

	/i18n/
	 
		grid.locale-bg.js
		 
		list of all language files
		 
		….
		 
		Changes.txt
		 
		jquery-1.3.2.min.js
		 
		jquery.jqGrid.min.js
		

 

在页面中写法：

Java代码 

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
  
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  
<head>
  
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
  
<title>My First Grid</title>
  
<link rel="stylesheet" type="text/css" media="screen" href="css/ui-lightness/jquery-ui-1.7.1.custom.css" />
  
<link rel="stylesheet" type="text/css" media="screen" href="js/src/css/ui.jqgrid.css" />
  
<link rel="stylesheet" type="text/css" media="screen" href="js/src/css/jquery.searchFilter.css" />
  
<style>
  
html, body {  
   margin: 0;
     
  padding: 0;
  
   font-size: 75%;
     
}
  
</style>
  
<script src="js/jquery-1.3.2.min.js" type="text/javascript"></script>
  
<script src="js/src/grid.loader.js" type="text/javascript"></script>
  
</head>
  
<body>
  
...
  
</body>
  
</html>
  

需要说明的是，jquery-ui的字体大小与jqgrid字体大小不一致，故需要在页面上在加上一段 style来指定页面上文字大小。
		
		
jqGrid皮肤
从3.5版本开始，jqGrid完全支持jquery UI的theme。我们可以从http://jqueryui.com/themeroller/下载我们所需要的theme。当然，你也可以编辑自己的theme。

jqGrid也并不需要把所有的css文件都引入进来，只需导入核心css文件“ui.theme.css ” 以及“ui.core.css”即可，文件位于目录development-bundle/themes下。

jqGrid原理
jqGrid是典型的B/S架构，服务器端只是提供数据管理，客户端只提供数据显示。换句话说，jqGrid可以以一种更加简单的方式来展现你数据库的信息，而且也可以把客户端数据传回给服务器端。

对于jqGrid我们所关心的就是：必须有一段代码把一些页面信息保存到数据库中，而且也能够把响应信息返回给客户端。jqGrid是用ajax来实现对请求与响应的处理。

