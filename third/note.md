nodejs中的模块的分类：
1. 加载核心模块
    node的核心模块是一些二进制文件，是由nodejs本身提供的。核心模块只能够通过文件的名称来引用，而不能通过文件的路径来引用。而且，在和第三方模块同名的情况下，nodejs会优先加载核心模块。
2. 加载文件模块
    主要就是通过相对路径或者绝对路径加载我们自己书写的模块，加载的时候，我们可以省略文件的后缀名。
3. 加载文件夹模块
    当使用node加载文件夹的时候，node会将文件夹看作是一个包。按照惯例，这个包应该包括一个package.json文件。这个文件包含了包定义相关的内容。如果这个文件不存在，那么node就会将index.js当作我们的入口文件。如果这个文件存在，那么nodejs就会寻找这个文件所定义的main属性，并把这个属性所指定的文件当作包的入口文件。一般情况下，我们都要包含package.josn文件
4. 从node_modules文件夹加载
    如果我们在加载文件的时候，传递给require方法的参数既不是绝对路径也不是相对路径，那么nodejs就会从node_modules文件夹中加载模块.这个时候，我们在加载模块的时候，就需要带上后缀了。
    如加载：./node_modules/module.js
        const module = require("module.js");
5. 缓存模块
    模块在首次加载俄时候会被缓存起来，这意味着，如果模块的名称能被解析为相同的文件名称，那么每次调用这个模块的时候都会返回同一个模块。