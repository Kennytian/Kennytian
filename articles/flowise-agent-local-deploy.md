## 本地部署 Flowise

### 一、介绍
Flowise 是一个开源的 LLM 应用开发平台，可以轻松构建 LLM 应用。开源地址：https://github.com/FlowiseAI/Flowise ，官网：https://flowiseai.com

### 二、环境准备
Flowise 支持多种部署方式，例如源代码部署、Docker 部署、Docker Compose 部署等，这里以 Docker 部署为例，介绍如何部署 Flowise。
- 源代码部署：安装 Node.js 18.15+，最好是20
- Docker 部署：安装 Docker
- Docker Compose 部署：安装 Docker Compose

以上，三选一就好了。

### 三、本地 LLM
Flowise 支持多种 LLM，例如 OpenAI、Google PaLM、Ollama 等，下面的演示以 Ollama 为例。如果你的网络或地区可以直接使用 OpenAI，那么使用 OpenAI 也是没问题的。

### 四、部署
我们以 Docker 部署为例，部署命令如下：

`docker run -d --name flowise --net=host flowiseai/flowise:latest`

在浏览器中访问 http://localhost:3000

> 注意：由于 Docker 默认的网络是 bridge，所以需要使用 host 网络模式才能访问到主机的  http://localhost:11434 上的 Ollama API 服务。

### 五、效果图
![](./images/flowise.webp)

## 十、技术支持
- 加微信了解更多细节

![关注公众号](./images/official_qrcode.webp)
