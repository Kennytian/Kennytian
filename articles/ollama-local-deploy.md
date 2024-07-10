# 在本地部署 Ollama

## 一、下载 Ollama
根据不同平台选择性下载 https://ollama.com/download

或者使用 Docker

```shell
docker run -d -v ~/Downloads/ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
```

## 二、下载 LLM 模型
- `ollama run qwen2`

更多模型下载：https://ollama.ai/library

## 三、启动 Ollama
- `ollama serve`

## 四、运行 Web UI 网站调用
- `docker run -p 3211:3000 -d --restart=always --name chatbot-ollama ghcr.io/ivanfioravanti/chatbot-ollama:main`

这样就能用 Web 来切换使用 Ollama 了

> 注意： 如果没有设置为自动启动，可以通过如下命令为设置为自动启动：
```shell
docker update --restart=always chatbot-ollama
```
查看`chatbot-ollama`是否为自动启动：
```shell
docker inspect chatbot-ollama --format='{{.HostConfig.RestartPolicy.Name}}'
```

## 五、如何调用API
> 常用接口调用方式
```shell
curl http://localhost:11434/api/generate -d '{
  "model": "qwen2",
  "prompt": "你好",
  "stream": true
}'


curl http://localhost:11434/api/chat -d '{
  "model": "qwen2",
  "messages": [
    {
      "role": "user",
      "content": "你好"
    }
  ]
}'
```
> 列出模型

`curl http://localhost:11434/api/tags`

> 显示模型信息
```shell
curl http://localhost:11434/api/show -d '{
  "name": "qwen2"
}'
```

## 六、修改模型下载地址

```shell
launchctl setenv OLLAMA_MODELS "~/Downloads/ollama"
```



更多 API 接口请参考 https://github.com/ollama/ollama/blob/main/docs/api.md

## 十、技术支持
- 加微信了解更多细节

![关注公众号](./images/official_qrcode.webp)
