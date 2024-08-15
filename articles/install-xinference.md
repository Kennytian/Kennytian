# Xinference

## 一、介绍
Xinference是一个开源的AI模型服务框架，支持多模型多任务。

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

## 十、技术支持
- 加微信了解更多细节

![关注公众号](./images/official_qrcode.webp)
