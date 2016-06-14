gulp-seajs-transport-ext
====================

transport seajs module gulp plugin
用于对seajs模块进行transport化

新增idleading

## Note

与[gulp-transport](https://github.com/popomore/gulp-transport)的区别是本插件不需要每个模块拥有package.json

## Install

```
$ npm install --save-dev gulp-seajs-transport-ext

```

## Usage

```
var transport = require("gulp-seajs-transport-ext");
var gulp = require("gulp");

gulp.task("default",function(){
  gulp.src("./testfiles/**/*.js")
        .pipe(transport())
        .pipe(gulp.dest("./dist"));
}) 
   
```
如果要生成一个相对路径的模块

```
var transport = require("gulp-seajs-transport-ext");
var gulp = require("gulp");

gulp.task("default",function(){
  gulp.src("./testfiles/abc/def/ggg.js",{base:"./testfiles/abc"})
        .pipe(transport({
        	idleading:"/static/"
        })) //此时seajs模块id为=>/static/def/ggg
        .pipe(gulp.dest("./dist"));
}) 
   

```

## API (0.1.0版本废弃,使用gulp自带的options设置base来)

**options.base**

Type: `String`

Default: `file.base`

transport时可以指定一个基准路径,使生成的模块ID都是相对于这个基准路径的

如某个文件为`/root/ab/c/d.js`

设置base为`/root/ab`

最后的结果为=>`c/d`



## Licence

MIT
