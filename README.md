# SearXNG Deployment Action

这是一个用于部署 SearXNG 搜索引擎并返回 JSON 格式结果的 GitHub Action。

## 功能特性

- 🚀 自动部署 SearXNG
- 📦 支持 Docker 部署
- 🔍 返回 JSON 格式的搜索结果
- ⚡ 快速配置和使用

## 用法

### 作为 Workflow

```yaml
- uses: h1collab/actions/deploy-searxng@main
  with:
    port: '8888'
    image: 'searxng/searxng:latest'
```

### 输入参数

| 参数 | 描述 | 默认值 | 必需 |
|------|------|--------|------|
| `port` | SearXNG 服务端口 | `8888` | 否 |
| `image` | Docker 镜像名称 | `searxng/searxng:latest` | 否 |
| `config-url` | 配置文件 URL | - | 否 |

### 输出参数

| 参数 | 描述 |
|------|------|
| `status` | 部署状态 (success/failure) |
| `url` | SearXNG 服务 URL |
| `result` | JSON 格式的响应结果 |

## 示例

```yaml
name: Deploy SearXNG
on: [push]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: h1collab/actions/deploy-searxng@main
        with:
          port: '8888'
      
      - name: Test Search
        run: |
          curl -s "http://localhost:8888/search?q=test&format=json" | jq .
```

## 许可证

MIT
