# 在本地部署 Ollama

## 一、下载 Ollama
根据不同平台选择性下载 https://ollama.com/download

## 二、下载 LLM 模型
- `ollama run qwen2`

更多模型下载：https://ollama.ai/library

## 三、启动 Ollama
- `ollama serve`

## 四、运行 Web UI 网站调用
- `docker run -p 3211:3000 -d --name chatbot-ollama ghcr.io/ivanfioravanti/chatbot-ollama:main`

这样就能用 Web 来切换使用 Ollama 了


## 十、技术支持
- 加微信了解更多细节

![关注公众号](./images/official_qrcode.webp)
