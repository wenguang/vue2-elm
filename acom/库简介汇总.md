


**shelljs**: 在js中使用unix命令，build.js中有使用，作自动化部署很有用
```
//局部模式
var shell = require('shelljs');
//全局模式下，就不需要用shell开头了。
//require('shelljs/global');
```
build.js就是全局模式，rm('-rf', assetsPath)，就直接这么用了。
参考：[用shelljs实现前端部署自动化](https://segmentfault.com/a/1190000016054416)

**ora**：实现node.js命令行环境的loading效果，显示各种状态的图标
```
ora = require('ora');
spinner = ora('Loading unicorns').start();

setTimeout(() => {
    spinner.color = 'yellow';
    spinner.text = 'Loading rainbows';
}, 1000);
spinner.start();//开始
spinner.stop();//结束
```

