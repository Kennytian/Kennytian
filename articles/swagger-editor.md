# Swagger 编辑器

## 一、介绍
Swagger 编辑器是一个在线的 Swagger 编辑器，可以快速创建、编辑、测试和分享 Swagger 文档。Swagger 文档格式分为 YAML 和 JSON 两种格式。网上也有很多相互转换的工具。

> 注意: 有使用 Swagger 时，尽量使用 3.1 的版本

## 二、使用方法
打开 https://editor-next.swagger.io/ ，就在线上编辑 Swagger 文档，右侧的预览功能可以查看生成的 JSON 格式的 Swagger 文档。

## 三、根据 Curl 请求生成 Swagger 文档
打开 https://codesandbox.io/p/sandbox/damp-sky-kn1rei

## 四、示例
### 4.1 测试接口
```json
{
  "openapi": "3.1.0",
  "info": { "title": "测试接口", "version": "1.0.0" },
  "servers": [
    {
      "url": "https://jsonplaceholder.typicode.com"
    }
  ],
  "paths": {
    "/posts": {
      "post": {
        "summary": "请求什么就返回什么",
        "operationId": "echo",
        "requestBody": {
          "content": {
            "application/json": {
              "schema": {
                "$ref": "#/components/schemas/User"
              }
            }
          },
          "required": true
        },
        "responses": {
          "201": {
            "description": "用户创建",
            "content": {
              "application/json": {
                "schema": {
                  "$ref": "#/components/schemas/User"
                }
              }
            }
          },
          "default": {
            "description": "Unexpected error"
          }
        }
      }
    }
  },
  "components": {
    "schemas": {
      "User": {
        "type": "object",
        "properties": {
          "name": {
            "type": "string",
            "description": "用户名"
          },
          "age": {
            "type": "integer",
            "description": "用户年龄"
          },
          "isAdult": {
            "type": "boolean",
            "description": "是否为成人"
          }
        },
        "required": [
          "name",
          "age",
          "isAdult"
        ]
      }
    }
  }
}
```

### 4.2 Flux Pro 文生图
```json
{
  "openapi": "3.1.0",
  "info": {
    "title": "Flux Pro 文生图",
    "description": "前Stability.ai成员创建的black forest labs公司，用于图片生成",
    "version": "1.0.0"
  },
  "tags": [],
  "servers": [
    {
      "url": "https://api.302.ai"
    }
  ],
  "paths": {
    "/302/submit/flux-pro": {
      "post": {
        "parameters": [
          {
            "in": "header",
            "name": "authorization",
            "schema": {
              "type": "string",
              "example": "Bearer sk-xxx"
            },
            "required": true
          }
        ],
        "requestBody": {
          "content": {
            "application/json": {
              "schema": {
                "type": "object",
                "properties": {
                  "prompt": {
                    "type": "string",
                    "example": "a dog"
                  },
                  "image_size": {
                    "type": "object",
                    "properties": {
                      "width": {
                        "type": "integer",
                        "example": 1024
                      },
                      "height": {
                        "type": "integer",
                        "example": 1024
                      }
                    }
                  },
                  "num_inference_steps": {
                    "type": "integer",
                    "example": 1
                  },
                  "guidance_scale": {
                    "type": "integer",
                    "example": 3.5
                  }
                }
              }
            }
          }
        },
        "responses": {
          "200": {
            "description": "OK",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "completed_at": { "type": "string" },
                    "created_at": { "type": "string" },
                    "error": { "type": "string" },
                    "id": { "type": "string" },
                    "model": { "type": "string" },
                    "output": { "type": "string" },
                    "started_at": { "type": "string" },
                    "status": { "type": "string" }
                  },
                  "required": [
                    "completed_at",
                    "created_at",
                    "error",
                    "id",
                    "model",
                    "output",
                    "started_at",
                    "status"
                  ]
                },
                "examples": {
                  "1": {
                    "summary": "成功示例",
                    "value": {
                      "completed_at": "",
                      "created_at": "",
                      "error": "",
                      "id": "",
                      "model": "",
                      "output": "",
                      "started_at": "",
                      "status": ""
                    }
                  }
                }
              }
            }
          }
        },
        "security": [
          {
            "bearerAuth": []
          }
        ]
      }
    }
  },
  "components": {
    "schemas": {},
    "securitySchemes": {
      "bearerAuth": {
        "type": "http",
        "scheme": "bearer",
        "bearerFormat": "JWT"
      }
    }
  }
}

```

## 十、技术支持
- 加微信了解更多细节

![关注公众号](./images/official_qrcode.webp)
