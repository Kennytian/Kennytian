# N8N - 自动化工作流入门

## 介绍
N8N 是一个开源的、可扩展的、无代码的、无服务器的、无代码工作流自动化平台。

## 场景
- 我们主要是做 业务系统（订单工单的多维表格）和 客户查询的业务系统之间数据同步
- 群消息 -> SQL 数据库 -> N8N -> OpenAI -> 运营告警邮件

## Docker 安装
```bash
services:
  n8n:
    image: n8nio/n8n:latest
    container_name: n8n
    ports:
      - "15678:5678"
    environment:
      - N8N_BASIC_AUTH_ACTIVE=true
      - N8N_BASIC_AUTH_USER=user
      - N8N_BASIC_AUTH_PASSWORD=L6MApCLF
      - N8N_DEFAULT_LOCALE=zh-CN
      - DB_TYPE=postgresdb
      - DB_POSTGRESDB_HOST=db
      - DB_POSTGRESDB_PORT=5432
      - DB_POSTGRESDB_DATABASE=askme
      - DB_POSTGRESDB_USER=postgres
      - DB_POSTGRESDB_PASSWORD=Ltdt9ZDJ2X1X
      - NODE_FUNCTION_ALLOW_EXTERNAL=axios,qs
      - GENERIC_TIMEZONE=Asia/Shanghai
      - TZ=Asia/Shanghai
    depends_on:
      - db
    restart: unless-stopped

  db:
    container_name: n8ndb
    #image: postgres:15-alpine
    image: postgis/postgis:13-3.4
    ports:
      - "5434:5432"
    volumes:
      - ./db-data:/var/lib/postgresql/data
    environment:
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=Ltdt9ZDJ2X1X
      - POSTGRES_DB=askme
    restart: unless-stopped

```

## 十、技术支持
- 加微信了解更多细节

![关注公众号](./images/official_qrcode.webp)
