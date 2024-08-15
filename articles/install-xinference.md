# Xinference

## 一、介绍
Xinference是一个开源的AI模型服务框架，支持多模型多任务。它与 Ollama 有什么不同呢？

| 特性       | Ollama   | Xinference|
|----------|----------|---------------|
| **主要用途** | 低资源推理优化| 多模型、多引擎通用推理平台|
| **硬件适应性**| 高灵活性，适合低端到高端硬件| 主要适用于高端硬件|
| **延迟** | 低延迟，适合实时应用| 根据配置不同，延迟可能较高|
| **模型支持** | 可能有限，专注于优化的模型| 泛支持多种模型和格式|
| **引擎支持** | 可能专注于特定推理引擎 | 支持 TensorFlow, PyTorch,ONNX等 |
| **扩展性** | 较低 | 高扩展性，适合大规模部署|
| **集成难度** | 简单，适合快速部署| 复杂，适合定制化需求的部署|
| **资源需求** | 较低，适合低资源场景 | 较高，适合需要高性能的场景|
| **优化特点**| 针对推理优化，特别是低端硬件 | 更泛的优化选择，支持长上下文|
| **用户群体**| 开发者、工程师，尤其在资源有限的场景 | 大规模企业、需要复杂推理的用户 |

## 二、安装
- `conda create -n xinference python=3.11.7`
- `conda activate xinference`
- `pip install "xinference[all]" -i https://pypi.mirrors.ustc.edu.cn/simple`

> 注意：如果发现哪个安装不了，就 conda install -c conda-forge packageName
> 1. conda install -c conda-forge openfst
> 2. conda install -c conda-forge pynini==2.1.5

这个安装过程非常慢，如果失败就重新执行 `pip install "xinference[all]" -i https://pypi.mirrors.ustc.edu.cn/simple`

## 三、验证安装
- `xinference --help`
- `xinference -v`

## 四、启动服务
- `xinference-local --host 0.0.0.0 --port 9997`

## 五、访问
- 界面操作：http://localhost:9997/ui
- 查看 `API` 文档：http://localhost:9997/docs

## 六、部署大模型
查询 `qwen1.5-chat` 模型相关参数组合，运行如下命令：
- `xinference engine -e http://localhost:9997 --model-name qwen1.5-chat`

显示如下信息：
```
Name          Engine        Format      Size (in billions)  Quantization
------------  ------------  --------  --------------------  --------------
qwen1.5-chat  Transformers  pytorch                    0_5  4-bit
...
qwen1.5-chat  Transformers  gptq                       0_5  Int4
...
qwen1.5-chat  Transformers  awq                        0_5  Int4
...
qwen1.5-chat  llama.cpp     ggufv2                     0_5  q2_k
...
```
解释：
- `Name`：模型名称
- `Engine`：模型引擎
  - Transformers 运行的是原始模型，需要大显存才能启动，速度慢，但精度最高
  - llama.cpp 运行的是量化后的模型，速度非常快，但精度有所缺失
- `Format`：模型格式，模型文件的保存格式
- `Size (in billions)`：模型大小
- `Quantization`：模型量化，将模型从高精度转换为低精度的方法，从而减少内存占用和计算成本。其中`none`代表没有经过量化，`4-bit`代表4-bit量化，`Int4`代表Int4量化，`q2_k`代表q2_k量化

> 最终选择：`qwen1.5-chat、Transformers、pytorch、1_8、none` 这种组合

## 十、技术支持
- 加微信了解更多细节

![关注公众号](./images/official_qrcode.webp)
