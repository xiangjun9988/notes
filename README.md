##### VSCode Insiders debgu babel code
```
  npm init -y; npm i -D eslint babel-cli babel-preset-es2015-node6
```

##### 新建兩個文件夾
- .babelrc
```
{
  "presets":["es2015-node6"]
}
```
- .eslintrc.json
```
{
  "parserOptions":{
    "ecmaVersion":6,
    "sourceType":"module"
  }
}
```

##### 新建文件夹和文件
- src和modules
- index.js 和 Person.js
```
//Person.js
"use strict";

    export default class Person {
      constructor(name = "不知道") {
        this.name = name;
      }

      speak() {
        console.log(this.name);
      }
    }
```
```
//index.js
    "user strict";

    import Person from "./modules/person";

    const jake = new Person("jake");
    const annon = new Person();

    jake.speak();
    annon.speak();

```
##### 修改package.json
```
"scripts": {
    "build":"babel src --out-dir dist --watch --source-maps",//添加命令部分
    "test": "echo \"Error: no test specified\" && exit 1"
  }
```

##### 执行编译命令
```
  npm run build
```

##### 切换到VSCode 的调试模式下->点击修改配置
```
  "program": "${workspaceRoot}\\src\\index.js",
  "sourceMaps" : true
```
