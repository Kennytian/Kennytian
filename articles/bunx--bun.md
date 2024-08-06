# Bunx 命令的 --bun 有什么作用？

这里拿`create-next-app@latest` 为例，其它的包管理器，都是:
- `npx create-next-app@latest my-app --typescript --tailwind --eslint`
- `yarn create create-next-app@latest my-app --typescript --tailwind --eslint`
- `pnpm dlx create-next-app@latest my-app --typescript --tailwind --eslint`

总结表格如下：


但要是使用`bunx`，需要加上`--bun`，比如：
- `bunx --bun create-next-app@latest my-app --typescript --tailwind --eslint`

这是为什么？这里就要引入一样叫`Shebang`的概念了，它是一个由井号 # 和叹号 ! 构成的字符序列 #!，它出现在文本文件的第一行的前两个字符位置。在类 Unix 操作系统中，Shebang 用于指示文件应该由哪个解释器来执行。如：

```shell
#!/bin/sh
#!/usr/bin/env node
#!/usr/bin/env bun
#!/usr/bin/python -o
```

那么如果没有加`--bun`，bunx 就会使用默认 shebang 指示的脚本解释器来执行。

但如果加了`--bun`，就会忽略原有的解释器，强制用 `bun` 来执行脚本。

## 十、技术支持
- 加微信了解更多细节

![关注公众号](./images/official_qrcode.webp)
