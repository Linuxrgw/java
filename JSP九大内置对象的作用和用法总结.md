# java
JSP全名为Java Server Pages，中文名叫java服务器页面。

JSP中一共预先定义了9个这样的对象，分别为：request、response、session、application、out、pagecontext、config、page、exception

1、request对象javax.servlet.http.HttpServletRequest 
request对象代表了客户端的请求信息，主要用于接受通过HTTP协议传送到服务器的数据。（包括头信息、系统信息、请求方式以及请求参数等）。request对 象
的作用域为一次请求。

当Request对象获取客户提交的汉字字符时，会出现乱码问题，必须进行特殊处理。首先，将获取的字符串用ISO-8859－1进行编码，并将编码存发岛一个字节数组中
，然后再将这个数组转化为字符串对象如下

Request常用的方法：getParameter(String strTextName) 获取表单提交的信息.

getProtocol() 获取客户使用的协议。

String strProtocol=request.getProtocol();

getServletPath() 获取客户提交信息的页面。String strServlet=request.getServletPath();

getMethod() 获取客户提交信息的方式 String strMethod=request.getMethod();

getHeader() 获取HTTP头文件中的accept,accept-encoding和Host的值,String strHeader=request.getHeader();

getRermoteAddr() 获取客户的IP地址。String strIP=request.getRemoteAddr();

getRemoteHost() 获取客户机的名称。String clientName=request.getRemoteHost(); 
getServerName() 获取服务器名称。 String serverName=request.getServerName(); 
getServerPort() 获取服务器的端口号。 int serverPort=request.getServerPort(); 
getParameterNames() 获取客户端提交的所有参数的名字。

Enumeration enum = request.getParameterNames();
while(enum.hasMoreElements())
{
    Strings(String)enum.nextElement();
    out.println(s);
}
1
2
3
4
5
6
2、response对象 javax.servlet.http.HttpServletResponse 
response 代表的是对客户端的响应，主要是将JSP容器处理过的对象传回到客户端。response对象也具有作用域，它只在JSP页面内有效。

具有动态响应contentType属性,当一个用户访问一个JSP页面时，如果该页面用page指令设置页面的contentType属性是text/html，那么JSP引擎将按照这个属性值
做出反应。

如果要动态改变这换个属性值来响应客户，就需要使用Response对象的setContentType(String s)方法来改变contentType的属性值。

response.setContentType(String s); 参数s可取text/html,application/x-msexcel,application/msword等。

在某些情况下，当响应客户时，需要将客户重新引导至另一个页面，可以使用Response的sendRedirect(URL)方法实现客户的重定向。

例如response.sendRedirect(index.jsp);

3、session对象 javax.servlet.http.HttpSession 
Session对象是一个JSP内置对象，它在第一个JSP页面被装载时自动创建，完成会话期管理。从一个客户打开浏览器并连接到服务器开始，到客户关闭浏览器离开
这个服务器结束，被称为一个会话。当一个客户访问一个服务器时，可能会在这个服务器的几个页面之间切换，服务器应当通过某种办法知道这是一个客户，
就需要Session对象。 
当一个客户首次访问服务器上的一个JSP页面时，JSP引擎产生一个Session对象，同时分配一个String类型的ID号，JSP引擎同时将这换个ID号发送到客户端，
存放在Cookie中，这样Session对象，直到客户关闭浏览器后，服务器端该客户的Session对象才取消，并且和客户的会话对应关系消失。当客户重新打开浏览器
再连接到该服务器时，服务器为该客户再创建一个新的Session对象。 
session 对象是由服务器自动创建的与用户请求相关的对象。服务器为每个用户都生成一个session对象，用于保存该用户的信息，跟踪用户的操作状态。

session对象内部使用Map类来保存数据，因此保存数据的格式为 “Key/value”。 session对象的value可以使复杂的对象类型，而不仅仅局限于字符串类型。

public String getId()：获取Session对象编号。

public void setAttribute(String key,Object obj)：将参数Object指定的对象obj添加到Session对象中，并为添加的对象指定一个索引关键字。

public Object getAttribute(String key)：获取Session对象中含有关键字的对象。

public Boolean isNew()：判断是否是一个新的客户。

4、application对象javax.servlet.ServletContext 
application 对象可将信息保存在服务器中，直到服务器关闭，否则application对象中保存的信息会在整个应用中都有效。与session对象相比，
application对象生命周期更长，类似于系统的“全局变量”。

服务器启动后就产生了这个Application对象，当客户再所访问的网站的各个页面之间浏览时，这个Application对象都是同一个，直到服务器关闭。
但是与Session对象不同的时，所有客户的Application对象都时同一个，即所有客户共享这个内置的Application对象。

setAttribute(String key,Object obj)：将参数Object指定的对象obj添加到Application对象中，并为添加的对象指定一个索引关键字。

getAttribute(String key)：获取Application对象中含有关键字的对象。

5、out 对象javax.servlet.jsp.jspWriter 
out 对象用于在Web浏览器内输出信息，并且管理应用服务器上的输出缓冲区。在使用 out 对象输出数据时，可以对数据缓冲区进行操作，及时清除缓冲区中
的残余数据，为其他的输出让出缓冲空间。待数据输出完毕后，要及时关闭输出流。

Out对象时一个输出流，用来向客户端输出数据。Out对象用于各种数据的输出。其常用方法如下。

out.print()：输出各种类型数据。

out.newLine()：输出一个换行符。

out.close()：关闭流。

6、pageContext 对象javax.servlet.jsp.PageContext 
pageContext 对象的作用是取得任何范围的参数，通过它可以获取 JSP页面的out、request、reponse、session、application 等对象。

pageContext对象的创建和初始化都是由容器来完成的，在JSP页面中可以直接使用 pageContext对象。

page 对象代表JSP本身，只有在JSP页面内才是合法的。 page隐含对象本质上包含当前 Servlet接口引用的变量，类似于Java编程中的 this 指针。

7、config 对象javax.servlet.ServletConfig 
config 对象的主要作用是取得服务器的配置信息。通过 pageConext对象的 getServletConfig() 方法可以获取一个config对象。当一个Servlet 初始化时，
容器把某些信息通过 config对象传递给这个 Servlet。开发者可以在web.xml 文件中为应用程序环境中的Servlet程序和JSP页面提供初始化参数。

8 cookie 对象 
Cookie是Web服务器保存在用户硬盘上的一段文本。Cookie允许一个Web站点在用户电脑上保存信息并且随后再取回它。举例来说，一个Web站点可能会为
每一个访问者产生一个唯一的ID，然后以Cookie文件的形式保存在每个用户的机器上。

创建一个Cookie对象 调用Cookie对象的构造函数就可以创建Cookie对象。Cookie对象的构造函数有两个字符串参数：Cookie名字和Cookie值。

例如：Cookie c = new Cookie(username”,john”); 将Cookie对象传送到客户端。

JSP中，如果要将封装好的Cookie对象传送到客户端，可使用Response对象的addCookie()方法。

例如：response.addCookie(c)，读取保存到客户端的Cookie。

使用Request对象的getCookie()方法，执行时将所有客户端传来的Cookie对象以数组的形式排列，如果要取出符合需要的Cookie对象，就需要循环比较数组内
每个对象的关键字。设置Cookie对象的有效时间，用Cookie对象的setMaxAge()方法便可以设置Cookie对象的有效时间，

例如：Cookie c = newCookie(username”,”john”);c.setMaxAge(3600);

Cookie对象的典型应用时用来统计网站的访问人数。由于代理服务器、缓存等的使用，唯一能帮助网站精确统计来访人数的方法就是为每个访问者建立一个唯一ID。
使用Cookie，网站可以完成以下工作:

测定多少人访问过。测定访问者有多少是新用户（即第一次来访），多少是老用户。

测定一个用户多久访问一次网站。当一个用户第一次访问时，网站在数据库中建立一个新的ID，并把ID通过Cookie传送给用户。用户再次来访时，网站把
该用户ID对应的计数器加1，得到用户的来访次数。

9、exception 对象java.lang.Throwable 
exception 对象的作用是显示异常信息，只有在包含 isErrorPage=”true” 的页面中才可以被使用，在一般的JSP页面中使用该对象将无法编译JSP文件。

excepation对象和Java的所有对象一样，都具有系统提供的继承 结构。

exception 对象几乎定义了所有异常情况。在Java程序中，可以使用try/catch关键字来处理异常情况； 如果在JSP页面中出现没有捕获到的异常，就会生成 
exception 对象，并把 exception 对象传送到在page指令中设定的错误页面中，然后在错误页面中处理相应的 exception 对象。
