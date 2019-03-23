
这里定义一些环境变量、项目生成的路径、是否压缩包、代理路径等，项目构建部署时用到，build目录的文件多引入它

**注意commonJS风格的编写**
```
module.exports = {
    build: {
        env: {
            NODE_ENV: '"production"'
        },
        assetsRoot: path.resolve(__dirname, '../elm')
        //...
    },
    dev: {
        env: {
            NODE_ENV: '"development"'
        },
        port: 8000
        //...
    }
}
```

build.js对它的引入是这样的
```
var config = require('../config')
config.build.assetsRoot
```
**require是把整个config目录引入，相关于一个包，index.js这个文件暴露给外部2个对象，build和dev**

