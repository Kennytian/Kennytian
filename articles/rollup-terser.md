# 如何用 rollup 压缩混淆，保护你的代码

通常的做法是使用 webpack 或者 rollup，它们都可以编译代码，但是它们有一个共同的问题，那就是它们不能「保护」你的代码。

## 安装rollup等依赖
```bash
pnpm i -D rollup @rollup/plugin-commonjs @rollup/plugin-node-resolve @rollup/plugin-terser @rollup/plugin-typescript
```

## 配置rollup.config.js
```js
import commonjs from '@rollup/plugin-commonjs';
import nodeResolve from '@rollup/plugin-node-resolve';
import terser from '@rollup/plugin-terser';
import typescript from '@rollup/plugin-typescript';

/** @type {import('rollup').RollupOptions} */
export default {
  input: ['src/generate.ts', 'src/main.ts'],
  output: { dir: 'dist', format: 'cjs' },
  plugins: [
    commonjs(),
    nodeResolve(),
    terser(),
    typescript({ module: 'esnext' }),
  ],
};
```
> 配置解释：
- `@rollup/plugin-commonjs`，目前大多数 NPM 上的包都以 CommonJS 模块的方式暴露，我们需要在 Rollup 处理它们之前将 CommonJS 转换为 ES2015
- `@rollup/plugin-node-resolve`，使Rollup能够解析Node.js风格的模块路径（如import myModule from 'my-module'），它会查找node_modules目录中的模块，就像Node.js运行时那样
- `@rollup/plugin-terser`，Terser就是本次保护代码的核心插件，它虽然是一个JavaScript压缩工具，该插件用于在构建过程中压缩输出的JS文件。它通过删除空白、注释以及进行其他优化来减小文件大小，从而提高加载速度和性能。但*它可以将输出的代码压缩+混淆，使代码更难被反编译*。
- `@rollup/plugin-typescript`，如果你的项目使用TypeScript编写（TypeScript项目必选），这个插件可以编译TypeScript源代码到JavaScript。它还处理TypeScript的类型检查，并确保你的项目可以在不支持TypeScript的环境中运行
- `input`，指定入口文件，可以是一个`字符串`，也可以是`一个数组`，数组中的每个元素都是一个入口文件，或者是一个`对象`，对象中包含`input`属性，指定入口文件，如：`{generate: 'src/generate.ts', main:'main.ts'}`
- `output`, 指定输出文件，可以是一个`字符串`，也可以是一个`对象`，对象中包含`dir`属性，指定输出目录，如：`{dir: 'dist', format: 'cjs'}`
- `plugins`，指定插件，可以是一个`数组`，数组中的每个元素都是一个插件，如：`[commonjs(), nodeResolve(), terser(), typescript({ module: 'esnext' })]`

## 运行 rollup
```bash
rollup -c
```

## 展示效果
`"use strict";var e=require("node:fs"),t=require("node:path"),r=require("node:crypto"),n=require("node:os"),o=require("os"),a=require("child_process"),i=require("fs");require("util");var s=require("./utils-IjaK3zhc.js"),u={options:{NOT_SUPPORTED_VALUE:"not supported",INTERVAL:1e3},isNotSupported(e){return e===this.options.NOT_SUPPORTED_VALUE}},c=u,l=o;c.cpu={average:function(){for(var e=0,t=0,r=l.cpus(),n=0,o=r.length;n<o;n++){var a=r[n];for(var i in a.times)t+=a.times[i];e+=a.times.idle}return{totalIdle:e,totalTick:t,avgIdle:e/r.length,avgTotal:t/r.length}},usage:function(e){var t=this;return e||(e=c.options.INTERVAL)
`

## 说在最后
1. JS项目保护工作不像二进制文件那样简单，编译、压缩、混淆，只能使代码更难被反编译，不代表就是绝对安全。所以，如果你的项目是核心代码、敏感数据，建议使用 WebAssembly(wasm) 编译成二进制文件，然后引用。
2. 使用市面上其它商业加密软件来保护你的代码。
