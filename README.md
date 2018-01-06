# LEARN YOU THE NODE.JS FOR MUCH WIN!  
  学习Node.JS 为了多赢！
  
 ## TIME SERVER (Exercise 10 of 13)  
   TIME SERVER(练习10 / 13 )
   
  Write a TCP time server!  
   编写一个 TCP 时间服务器！
   
  Your server should listen to TCP connections on the port provided by the first argument to your program. 
  你的服务器应该监听TCP提供的一个端口，以获取一些 TCP 连接，它会由第一个命令行参数传递给你的程序。
  
  For each connection you must write the current date & 24 hour time in the format:  
   对于每个TCP连接，您必须按以下格式编写当前日期和24小时制的时间：
   
     "YYYY-MM-DD hh:mm"  
    
  followed by a newline character. Month, day, hour and minute must be zero-filled to 2 integers. For example:  
   然后是一个换行符。月，日，小时和分钟必须由零补充成为一个两位整数。例如：
   
     "2013-07-06 17:42"  
    
  After sending the string, close the connection.  
   在发送完字符串后，关闭连接。
 ─────────────────────────────────────────────────────────────────────────────  
   
 ## HINTS  
    提示
   
  For this exercise we'll be creating a raw TCP server.
  在本练习中，我们将创建一个原始 TCP 服务器。
  
  There's no HTTP involved here so we need to use the net module from Node core which has all the basic networking functions.  
  这里不会涉及到HTTP，所以我们只需要使用Node核心中的具有所有基本网络功能的网络模块。
   
  The net module has a method named net.createServer() that takes a function. 
  net模块有一个名为net.createServer()的方法，它会接收一个函数。
  
  The function that you need to pass to net.createServer() is a connection listener that is called more than once.
  您需要传递给net.createServer（）的函数是一个多次调用的联系监听器。
  
  Every connection received by your server triggers another call to the listener.
  服务器接收到的每个连接都会触发另一个对该监听器的调用。
  
  The listener function has the signature:  
  这个监听器函数具有一个署名:
  
     function listener(socket) { /* ... */ }  
   
  net.createServer() also returns an instance of your server.
  net.createServer（）也会返回给你的服务器一个实例。
  
  You must call server.listen(portNumber) to start listening on a particular port.  
   你必须调用server.listen（portNumber）来让你的服务器开始监听一个特定的端口。
   
  A typical Node TCP server looks like this:  
  一个典型的 Node TCP 服务器如下所示：
   
     var net = require('net')  
     var server = net.createServer(function (socket) {  
       // socket handling logic  
     })  
     server.listen(8000)  
   
  Remember to use the port number supplied to you as the first command-line argument.  
   请记住请使用提供给您的端口号来作为第一个命令行参数。
   
  The socket object contains a lot of meta-data regarding the connection, but it is also a Node duplex Stream, in that it can be both read from, and written to. 
  socket对象包含许多关于连接的元数据( meta-data)，但它也是一个Node双工流，所以它是可以被读取和写入的。
  
  For this exercise we only need to write data and then close the socket.
  在本练习中，我们只需要写入数据，然后关闭socket就可以了。
   
  Use socket.write(data) to write data to the socket and socket.end() to close the socket.
  使用socket.write（data）将数据写入socket，并且使用socket.end（）关闭该socket。
  
  Alternatively, the .end() method also takes a data object so you can simplify to just: socket.end(data).
  另外，.end（）方法也可以接收一个数据对象，因此你可以简单的使用：socket.end（data）。
   
  Documentation on the net module can be found by pointing your browser here:  
  通过将浏览器指向以下位置，您可以找到网络模块上的文档:
   
  file:///Users/dllo/.nvm/versions/node/v8.9.4/lib/node_modules/learnyounode/node_apidoc/net.html
   
  To create the date, you'll need to create a custom format from a new Date() object. The methods that will be useful are:
  要创建一个日期，您需要使用新的Date（）对象并且创建一个自定义格式。这些方法将会很有用：
   
     date.getFullYear()  
     date.getMonth()     // starts at 0  
     date.getDate()      // returns the day of month  
     date.getHours()  
     date.getMinutes() 
   
  Or, if you want to be adventurous, use the strftime package from npm. The strftime(fmt, date) function takes date formats just like the unix date command.
  或者，如果您喜欢冒险，可以使用NPM提供的strftime软件包。
  其中 strftime(fmt, date) 这个方法可以接收一个和 unix 命令 date 相似的时间日期格式。
  
  You can read more about strftime at:
  (https://github.com/samsonjs/strftime)
  你可以阅读更多关于strftime的信息：
  (https://github.com/samsonjs/strftime)
   
 ─────────────────────────────────────────────────────────────────────────────  
   
   » To print these instructions again, run: learnyounode print
   如果想要再次打印这些说明，请运行： learnyounode print
   
   » To execute your program in a test environment, run: learnyounode run program.js                              
   如果想要在测试环境中执行程序，请运行: learnyounode run program.js
   
   » To verify your program, run: learnyounode verify program.js
   如果想要验证程序，请运行：learnyounode verify program.js
   
   » For help run: learnyounode help 
   如果想要寻求帮助请运行：learnyounode help