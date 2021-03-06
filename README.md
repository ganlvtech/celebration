# 站庆H5

## 概览

项目使用gulp进行流程控制，引入了sass和雪碧图支持。

项目结构说明：

- dist/: 生成的文件都在这里
  - index.html: 导入所有子页面之后的主页
  - sprite.png: 自动生成的雪碧图
  - sprite.css: 自动生成的雪碧图样式文件
  - all.css: 自动生成的打包的css
  - all.js: 自动生成的打包的js
  - media/bgm.mp3: 背景音乐
- src/: 开发目录
  - index.html: 网页入口
  - lib/: 第三方插件内容
  - pages/: 存放各页面，注意对应页面需要到`src/index.html`处引入
  - imgs/: 切图存放处，只支持png
    - icons/: 此处图片会自动生成雪碧图
  - css/: 使用sass预处理器，后缀为scss（可以认为是css的超集）
- gulpfile.js: gulp控制文件

## 运行

确保有nodejs环境，之后运行`npm install -g gulp`全局安装gulp，再运行`npm install`安装gulp相关依赖。首次运行时命令行输入`gulp build`进行相关的编译，编译生成的文件在dist目录下，之后运行`gulp watch`即可监听文件变化并自动进行编译。调试时打开`dist/index.html`即可。

下载<https://github.com/cantjie/eeyes-15th-anniversary>并解压到`dist/api`文件夹。

在`dist/`目录下执行`php -S 0.0.0.0:8000`

访问`http://127.0.0.1:8000/`即可

注意：非Windows用户可能需要手动`mkdir dist/upload`，并`chmod 777 dist/upload`。

`dist/media/bgm.mp3`仅在dist文件夹中存在，没有上传到Git仓库

## 开发

此处以添加word.html为例，说明页面开发流程，所有的开发均在src目录下完成。

1. 运行gulp watch
2. 在pages下新建word.html
3. 在index.html中引入对应的页面文件，`<!--=include ./pages/words.html -->`
4. 在js目录下添加你的页面的js文件，gulp会自动将该目录下的文件连接为一个文件`dist/all.js`
5. 在css目录下添加你的页面的scss文件，gulp会自动将该目录下的文件编译成css并连接为一个文件`dist/all.css`
6. 在imgs目录下添加你的页面的图片文件，若需要使用雪碧图（多用于小图标）则放入imgs/icons/目录下，会生成sprite.css和sprite.png，用法见sprite.css注释
7. 在lib目录下引入第三方库（若有需要），gulp会将其移动到dist/下