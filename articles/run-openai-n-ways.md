# 本地大模型启动 OpenAI 服务的N 种方式
## 一、VLLM
- `CUDA_VISIBLE_DEVICES=2 python -m vllm_entrypoints.openai.api_server --model /home/user/Download/Qwen2-7B-Instruct/ --max-model-len 10000 --gpu-memory-utilization 0.3` 

## 二、Fastchat
### 2.1启动控制器
- `python -m fastchat.serve.controller --host 0.0.0.0 --port 21003`

### 2.2 为模型工作进程设置环境变量，并启动 
- `python -m fastchat.serve.model_worker --model-path /home/user/Download/Qwen2-7B-Instruct/ --model-names qwen2 --num-gpus 1 --controller-address http://0.0.0.0:21003`

### 2.3 启动OpenAI API 服务器
- `python -m fastchat.serve.openai_api_server --host 0.0.0.0 --port 8200 --controller-address http://0.0.0.0:21003`

## 三、Llama Factory
- `CUDA_VISIBLE_DEVICES=2 llamafactory-cli api LLaMA-Factory/examples/inference/llama3_vllm.yaml`

## 四、Llama.cpp
- `conda activate llama_cpp`
- `CUDA_VISIBLE_DEVICES=2 ./llama-server --model models/qwen1.5-7b-FP16.gguf --host 0.0.0.0 --port 8000 --gpu-layers 1000`

## 五、 Ollama
- `ollama run qwen2`

## 十、技术支持
- 加微信了解更多细节

![关注公众号](./images/official_qrcode.webp)
