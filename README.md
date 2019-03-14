### vue-cli 3 安装选项:
1. Babel, Router(history mode), Vuex, CSS Pre-processors(Less), Linter(Prettier、lint on save), placing config(In dedicated config files)

### 此项目实现的功能：
1. git commit 时，进行代码格式化。比如：js中用了单引号，commit 时，会被修改为符合 Prettier 规范的双引号。
2. 检查 commit 信息文案是否合规。不符合规则，无法提交代码；commit 信息文案规范，commitlint.config.js 中 rules.type-enum 指定的关键字加上英文冒号再加空格，然后写具体文案，比如：`fix: 具体文案`

### 实现步骤
1. 安装所需模块：
`npm install lint-staged @commitlint/cli @commitlint/config-conventional prettier prettier-eslint-cli --save-dev`
2. package.json 添加如下代码：
```
    "gitHooks": {
        "commit-msg": "commitlint -E GIT_PARAMS",
        "pre-commit": "lint-staged"
    }
```
3. 添加文件：.lintstagedrc、commitlint.config.js。

### 使用 `vue-cli-service inspect` 来查看一个 Vue CLI 3 项目的 webpack 配置信息（包括：development、production）
1. --mode 指定环境模式 (默认值：development)
2. 运行命令，在终端输出：
开发环境：```npx vue-cli-service inspect --mode development```
生产环境：```npx vue-cli-service inspect --mode production```
3. 运行命令，将输出导入到 js 文件：
开发环境：```npx vue-cli-service inspect --mode development >> webpack.config.development.js```
生产环境：```npx vue-cli-service inspect --mode production >> webpack.config.production.js```
4. 在产生的 js 文件开头，添加：`module.exports = `，然后格式化即可查看。
5. 官方说明网址：https://cli.vuejs.org/zh/guide/cli-service.html#vue-cli-service-inspect

### .lintstagedrc 配置
`prettier-eslint --write`含义：
1. https://github.com/okonet/lint-staged#reformatting-the-code
```Tools like Prettier, ESLint/TSLint, or stylelint can reformat your code according to an appropriate config by running prettier --write/eslint --fix/tslint --fix/stylelint --fix. After the code is reformatted, we want it to be added to the same commit.```
2. https://prettier.io/docs/en/cli.html#write
```--write：This rewrites all processed files in place. This is comparable to the eslint --fix workflow.```
3. https://github.com/prettier/prettier-eslint-cli#--write
```
By default prettier-eslint will simply log the formatted version to the terminal. If you want to overwrite the file itself (a common use-case) then add --write.
```

### [prettier-eslint](https://github.com/prettier/prettier-eslint) 与 [prettier-eslint-cli](https://github.com/prettier/prettier-eslint-cli) 区别：
1. prettier-eslint [只能处理字符串](https://github.com/prettier/prettier-eslint-cli#the-problem)
2. prettier-eslint-cli [能处理一个或多个文件](https://github.com/prettier/prettier-eslint-cli#this-solution)
3. [默认情况下，prettier-eslint-cli 先运行 prettier，再运行`eslint --fix`](https://github.com/prettier/prettier-eslint-cli#--write)


# vue_cli_3_git_hooks_demo2

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
