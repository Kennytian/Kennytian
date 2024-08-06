# 一键备份并更新 Dify

## 一、创建备份目录
在 dify 同级目录下创建一个 `dify-ops` 目录，用于存放备份文件。
```bash
mkdir dify-ops
```

## 二、创建更新脚本
创建一个名为 `update-dify.sh` 的脚本文件，并添加以下内容：
```bash
cd ../dify/docker

git checkout main
git pull origin main

sudo docker compose pull

cp docker-compose.yaml docker-compose.yaml-$(date +%Y-%m-%d).bak

sudo docker compose down

sudo tar -cvf volumes-$(date +%Y-%m-%d).tgz volumes

sudo docker compose up -d

mv docker-compose.yaml-* volumes-* ../../dify-ops
```

## 三、执行脚本
在 dify 同级目录下执行脚本：
```bash
bash update-dify.sh
```

## 十、技术支持
- 加微信了解更多细节

![关注公众号](./images/official_qrcode.webp)
