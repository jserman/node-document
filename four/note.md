1. 创建缓冲区
    我们可以使用Buffer这个构造函数来创建我们的缓冲区。这个构造函数在创建对象的时候，可以指定缓冲区的内容，或者缓冲区的字节长度同时也能够指定缓冲区内容的字节编码，可接受编码：utf-8,ascii,base64
    如：
        const buf = new Buffer("hello","utf-8");  //指定内容的同时指定编码
        const buf = new Buffer(1024);  //指定缓冲区的字节长度.这里面包含的数据不是0，而是随机值
2. 我们可以通过[]语法来查看或者修改缓冲区的内容