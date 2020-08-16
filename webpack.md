#初步使用webpack打包构建
1. 运行'npm init '初始化项目,使用npm管理项目中的依赖包
2. 创建项目基本的目录结构 dist src文件夹(css文件夹, images文件夹, html, main.js, js文件夹)
3. 使用'npm i jquery --save' 安装jquery类库
4. 创建'main.js'并书写代码逻辑
5. 直接引用main.js会报错,需要使用webpack进行处理
6. 运行 'webpack 入口文件路径 输出文件路径'对main.js 进行处理
如: webpack ./src/main.js -o ./dist/bundle.js

##webpack-dev-server工具的使用:(实现自动打包编译功能)
    1. 运行 npm i webpack-dev-server -D 把工具安装到项目的本地开发依赖
    2. 在 package.json 文件 "test": "echo \"Error: no test specified\" && exit 1" 语句下加一句 ("dev": "webpack-dev-server")
    "dev": "webpack-dev-server --open --port 3000 --contentBase src --hot"
    //open 自动打开浏览器; port 3000 端口3000; contentBase src 内容根路径;
    // --hot 热重载,热更新,自动刷新
    3. 执行 npm run dev 
        注意:这里出现问题版本不兼容,需要卸载局部 webpack-dev-server
        具体方法看 "学习过程遇到问题" 文件中的第4个
    