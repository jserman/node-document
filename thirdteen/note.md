在http的协议里面，请求有两个重要的属性：url和方法。最常见的方法是
get方法，它主要用于请求内容，同时还有其它的方法，如post，put，head和delete。
每一种方法都会从服务器获得不同的结果。

1. 创建get请求
    我们可以使用http.get()这个方法来创建一个get请求。
    这个方法的第一个参数是一个配置对象，第二个参数是一个回调函数。
    这个函数接收一个参数，表示响应的结果.
    配置对象，我们可以进行如下的配置：
    {
        host:请求的域名
        port:请求的端口号
        path:请求的路径
    }

2. 其它的请求动词
    我们也可以使用http.request()来创建通用的请求。使用http动词创建的
    请求，都是这种请求的快捷方式。上面的这个方法，同样是接受两个参数，第一个参数
    是一个配置对象，第二个参数就是一个回调函数。这个函数同样接受一个参数。表示请求的响应对象。

    主要http.request()函数返回的是clientequest对象。我们可以通过clientrequest.write(str, encoding)
    这个方式将字符串或者buffer写入该对象。但是，一定要注意,一定要注意，一定要注意我们
    一定要使用clientrequest.end()这个方法来结束我们的请求。否则服务器端是不会给出任何响应的。

    如果我们请求的服务器正在运行，那么这个时候，我们就会得到一个响应。
    那么这个响应就会触发clientrequest的response事件。同样，这个响应事件的事件监听器参数，
    也是一个响应对象，我们可以通过这个参数来查看服务器响应的状态码以及响应头

3. 查看响应头
    当http服务器响应的时候，响应事件就会起作用了，这个事件会触发所有的
    为其注册的回调函数。并将响应对象传给这些回调函数。响应对象是http.clientResponse的实例。
    我们可以立即查看这个对象的属性：
    response.httpVersion:服务器上的http的版本
    response.statusCode:服务器返回的状态码
    response.headers：服务器返回的响应头，是一个键值对
4. 获取响应的主体部分
    记住，响应的主体并不会在response事件发生的时候出现，我们可以通过在response上绑定data事件，这个事件的事件
    监听器有一个参数，就是我们所要获取的响应的主体部分。同时，我们也可以通过使用response.setEncoding()来创建通用的请求。使用http动词创建的
    设置响应主体返回的编码格式

5. 还有一个重要的知识点：使用http.Agent维护套接字池
    查看agent.js文件

6. 使用request模块简化http请求
    --->request.js