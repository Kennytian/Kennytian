# 在 macOS 上的部署 Stable Diffusion

## 一. 准备工作
1. 安装 [Homebrew](https://brew.sh/)
2. 克隆  Stable Diffusion, `git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui`

> 注意：如果你没法科学上网（魔法上网），可以试试这家的服务 http://www.eevpnsafe.com/#/register?code=E2HTdlaA

## 二. 安装依赖
1. 安装 Python 3.10
2. 安装 torch 2.1.0

## 三. 运行
让命令行能够科学上网（魔法上网），否则好多依赖无法下载。命令行下执行：`export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890`

cd 进入`stable-diffusion-webui`目录，运行`bash webui.sh`，等待一段时间安装完依赖，程序会自动调用浏览器打开 http://127.0.0.1:7860。如果一直没有打开，可以尝试手动打开 http://127.0.0.1:7860。

> 如果的如下错误：
```
urllib3.exceptions.MaxRetryError: HTTPConnectionPool(host='127.0.0.1', port=1082): Max retries exceeded with url: http://127.0.0.1:7860/startup-events (Caused by ProxyError('Unable to connect to proxy', RemoteDisconnected('Remote end closed connection without response')))

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
```
只需要关掉科学上网（魔法上网）工具，再次运行`bash webui.sh`即可。

## 四. 配置
1. 默认只带了一个`v1-5-pruned-emaonly.safetensors`, 如果需要其他模型，可以到 https://civitai.com (C站) 和 https://huggingface.co/ (抱脸)下载。
2. 在`models`下放下模型，在`extensions`下放下插件。

## 十、技术支持
- 加微信了解更多细节

![关注公众号](./images/official_qrcode.webp)
