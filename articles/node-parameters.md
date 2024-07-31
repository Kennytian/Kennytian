# Node 命令行常见参数

## 一、起因
昨天编译 React Native 的时候，发现报如下错误：
```shell
FAILURE: Build failed with an exception.

* Where:
Settings file '/Users/kenny/rn-app/android/settings.gradle' line: 2

* What went wrong:
A problem occurred evaluating settings 'rnApp'.
> Could not read script '/Users/kenny/rn-app/node_modules/@react-native-community/cli-platform-android/native_modules.gradle' as it does not exist.
```

## 二、定位
经查 `@react-native-community/cli` 里的 issues，发现有人用 `node -p "require('@react-native-community/cli').bin;"` 来定位问题，最后根据这个命令找到了问题所在。

发现用 `PNPM` 安装的依赖，根本都没有把 `@react-native-community/cli` 安装进去，于是我尝试手动安装，执行 `pnpm i @react-native-community/cli -D`，再试使用 `node -p "require('@react-native-community/cli').bin;"`, 发现竟然出现：`/Users/kenny/rn-app/node_modules/.pnpm/@react-native-community+cli@14.0.0_typescript@5.5.4/node_modules/@react-native-community/cli/build/bin.js`，太奇怪了，怎么会在 `.pnpm` 目录正面呢？ 无法解决。

## 三、解决
1. 手动删除 package.json 文件 devDependencies 里的 `@react-native-community/cli`
2. 删除 `node_modules` 和 `pnpm-lock.yaml` 文件，使用 `bun install` 命令重新安装依赖。

## 四、总结
发现我在平时命令行下使用 Node 参数时，用的最多竟然只有 `node -v`，那今天就借这个机会来总结一下 Node 命令行常用参数。
- `--help`：显示帮助信息，如：`node --help`
- `-e`：执行脚本，如: `node -e "console.log('hello world')"`
- `-p`：执行脚本并打印结果，如：`node -p "require('@react-native-community/cli').bin"`
- `-v`：打印 Node 版本号，如：`node -v`
- `--`：指示 Node.js 命令行选项的结束，后面的参数不会被解释为选项，如：`npm run build:weapp -- --watch`（就是第一个 `--`）
- `--debug-port=`：设置调试端口
- `--inspect`：激活检查器
- `--inspect-brk`：激活检查器并在用户脚本的第一行代码处中断。
- `--max-old-space-size=`：设置 V8 垃圾回收器使用的内存量上限（以 MB 为单位）

## 十、技术支持
- 加微信了解更多细节

![关注公众号](./images/official_qrcode.webp)
