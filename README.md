## eslint

- eslint check for these three things:

1. programmer errors
2. best practices
3. style issues

4. npm install -D eslint
5. 使用 npx eslint 可以看到命令 （注意 npx 的用法）
6. npx eslint --init
7. 在 src/index.js 文件中写入 bad code
   vscode 未安装 eslint 插件前，此时页面上无任何提示
   执行 npx eslint src/_.js 可以看到终端里显示的错误信息，终端提示 --fix 命令
   执行 npx eslint src/_.js --fix 错误已修复

8. 将上面的命令放到 scripts 里  
   "scripts": {
   "lint": "eslint '**/\*.js'",
   "lint:fix":"eslint '**/\*.js' --fix"
   },
   上面的命令可以写成
   npm run lint
   npm run lint:fix

9. 命令检查修复麻烦，使用编辑器的力量
   安装 eslint 插件 退出重启 界面上可以看到错误提示

10. 目录下新增.vscode 文件夹，新增 settings.json
    {
    "editor.formatOnSave": true,
    "eslint.autoFixOnSave": true,
    }
    页面上保存时代码会自动修复错误

husky + lint-stage

使用原因：在 vscode 上编辑时保存自动修复错误。但有些错误是不可修复的，也可能
有人在 vscode 以外的地方手动编辑文件，仍然会有错误代码。
为了保证提交代码的正确性，使用 husky. 一般配合 lint-staged 工具一起使用

8. npm i -D husky lint-staged

```
在package.json文件中添加下面配置

  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "*.js": [
      "npm run lint:fix",
      "git add"
    ]
  },
```

在 vscode 外修改代码，执行 git add . 和 git commit 可以看到提交前自动修复

## eslint rule

npm i react

通过 react 代码来说明 rules 的配置
JSX not allowed in files with extension '.js'
// https://eslint.org/
//https://github.com/airbnb/javascript
//https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-filename-extension.md

不要着急去配置 rules，可以先写一些代码，看下那些规则是你真正需要，哪些你并不关心
rule "error" "warning" "off"

0:"off" 1:"warning" 2:"error"



# prettier-demo

支持 js css less sass json markdown 等等

prettier focus on how your code looks

linting focus on how your code behaves

1.    npm install -D prettier
2.  npx prettier src/index.js 只在命令行显示格式化后的内容
3.  npx prettier src/index.js --write 写入硬盘
4.  修改配置 touch .prettierrc


    {
    "singleQuote": true
    }

5.  package.json 增加脚本

"format": "prettier \"src/\*_/_.js\" --write"
npm run format

6. editor integration that's where prettier shines
   编辑器安装 prettier 插件

7. react 代码示例
   npm i -D react
