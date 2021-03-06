1. 理解request对象
    在监听request事件的时候，我们会在这个事件的回调函数
    中的第一个参数获取到request对象。通过这个对象，我们能够
    获取到关于请求的一些信息
    如：
        url:用于获取请求的url，但是这个url里面是不包含
        主机名，协议，或者端口号的。但是可以包含url的其他部分
        method:这个属性我们主要获取的就是请求所用的方法
        headers:这个属性主要是用于获取当前请求的header对象
            这个属性是一个对象，拥有请求的所有请求头.而且这个属性
            的所有的键都是小写的
    注意，当在服务器上得到request事件的时候，并不会立即获得请求体。
    这是因为请求体还没有到达，由于request是可读流，所以我们可以监听data事件
    ，将将请求体传送到一个可写流中  

2. 理解response对象
    response主要是用于响应客户端的，我们可以使用这个对象来写入
    响应头或者响应体

    写入响应头：
        我们可以使用response.writeHead(status, headers)
        来写我们的响应头。其中headers是一个对象而且是一个可选的参数
        。包含所有想要发送的响应头属性对象    

    设置响应头
        我们可以通过res.setHeader()这个方法来设置已有的响应头
        或者设置一个新的响应头。注意这个方法必须在使用res.write()和
        res.end()方法之前调用才会有效果.而且，如果已经在响应对象上使用了
        writeHead这个方法，那么这个方法仍然是不起作用的
    删除响应头：
        res.removeHeader(name)
        这个方法同样是要在响应头还未发出去之前就要设置的
    写入响应体：
        http服务器会在发送响应头之后发送响应体。写入响应体主要有如下两种方法
            一. 写入一个字符串
            二. 写入一个buffer对象

3. 以流的方式传送http的分块响应
    http的分块编码允许服务器持续的向客户端发送数据，而不需要发送数据的大小
    除非我们明确的指定了content-length的大小。否则node http会向客户端发送
    如下的响应头:transfer-encoding:chunk
    这个响应头的基本含义就是可以让客户端，接受若干的响应块作为响应的主体
    并在客户端在结束响应之前发送一个0长度的结束块。这对于向http客户端
    流式的传送文本，音频，视频数据非常有用

4. 关闭服务器
    关闭服务器，我们通常可以使用server.close()
    监听端口，我们通常可以使用server.listen(port, [host])