---
name: skill-qimen-api
description: 
EN: Xiaoqi Intelligent Calculation provides traditional metaphysics API services including BaZi (Eight Characters) and Qi Men Dun Jia. Rooted in data analysis and cognitive science, it offers rational decision-making references.
CN: 小奇智算提供八字、奇门遁甲等传统命理API服务，基于数据分析与认知科学，提供理性决策参考。
metadata: {"claw":{"emoji":"☯️"}}
---

# 小奇智算 API 能力 | Xiaoqi Intelligent Calculation API Skill

GET APIKEY：https://www.xiaoqizhisuan.cn

## 可用工具 | Available Tools
### 1. bazi_dayun - 八字大运查询 | BaZi Great Fortune Query
```
价格 | Price: ¥0.2 / time / 次
参数 | Parameters: No parameters required, user's BaZi information is automatically acquired / 无需参数，自动获取用户八字信息
返回 | Return: Detailed data of BaZi, Great Fortune and Fleeting Year / 八字、大运、流年详细信息
```

### 2. qimen_paipan - 奇门排盘（JSON 数据）| Qi Men Chart Generation (JSON Data)
```
价格 | Price: ¥0.5 / time / 次
参数 | Parameters: question (Optional) - Inquiry question / question（可选）- 求测问题
返回 | Return: Qi Men chart data in JSON format / JSON格式排盘数据
```

### 3. qimen_paipan_image - 奇门排盘+HTML网页图 | Qi Men Chart Generation + HTML Webpage Chart
```
价格 | Price: ¥0.8 / time / 次
参数 | Parameters: question (Optional) - Inquiry question / question（可选）- 求测问题
返回 | Return: Interactive HTML webpage chart for viewing / HTML网页排盘，可交互查看
```

### 4. qimen_jiepan - 即时盘解析准备 | Immediate Chart Analysis Preparation
```
价格 | Price: ¥1.0 / time / 次
参数 | Parameters: question (Required) - Inquiry question / question（必填）- 求测问题
返回 | Return: Useful God, analysis ideas, webpage chart, dedicated prompt / 用神、分析思路、网页排盘、提示词
```

### 5. qimen_jiepan_lifetime - 终身盘解析准备 | Lifetime Chart Analysis Preparation
```
价格 | Price: ¥1.2 / time / 次
参数 | Parameters: question (Required) - Inquiry question / question（必填）- 求测问题
返回 | Return: BaZi & Great Fortune, Useful God, analysis ideas, webpage chart, dedicated prompt / 八字大运、用神、分析思路、网页排盘、提示词
```

### 6. qimen_full - 即时局完整解盘 | Complete Immediate Chart Interpretation
```
价格 | Price: ¥1.5 / time / 次
参数 | Parameters: question (Required) - Inquiry question / question（必填）- 求测问题
返回 | Return: Webpage chart, Useful God, analysis ideas, prompt, LLM-generated interpretation / 网页排盘、用神、分析思路、提示词、大模型解盘文案
```

### 7. qimen_full_lifetime - 终身局完整解盘 | Complete Lifetime Chart Interpretation
```
价格 | Price: ¥2.0 / time / 次
参数 | Parameters: question (Required) - Inquiry question / question（必填）- 求测问题
返回 | Return: BaZi & Great Fortune, webpage chart, Useful God, analysis ideas, prompt, LLM-generated interpretation / 八字大运、网页排盘、用神、分析思路、提示词、大模型解盘文案
```

## API 调用方式 | API Integration Methods
### MCP 服务对接 | MCP Server Configuration
OpenClaw / Hermes / mcporter 配置 | Configuration
```json
{
  "mcpServers": {
    "xiaoqi": {
      "type": "streamable-http",
      "url": "https://www.xiaoqizhisuan.cn/mcp",
      "headers": {
        "x-api-key": "xq_你的API密钥 / xq_Your-API-Key",
        "Accept": "application/json, text/event-stream"
      }
    }
  }
}
```

Claude Desktop / Cursor / Windsurf 配置 | Configuration
```json
{
  "mcpServers": {
    "xiaoqi": {
      "url": "https://www.xiaoqizhisuan.cn/mcp",
      "headers": {
        "x-api-key": "xq_你的API密钥 / xq_Your-API-Key",
        "Accept": "application/json, text/event-stream"
      }
    }
  }
}
```

### 直接 HTTP 调用 | Direct HTTP Request
通用 Curl 请求示例 | Universal Curl Demo

# 1. 初始化连接 | Initialize Connection
```bash
curl -X POST https://www.xiaoqizhisuan.cn/mcp \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -H "x-api-key: xq_你的API密钥" \
  -d '{"jsonrpc":"2.0","id":1,"method":"initialize","params":{"protocolVersion":"2025-03-26","capabilities":{},"clientInfo":{"name":"my-client","version":"1.0"}}}'
```
# 2. 获取工具列表 | Fetch Tool List
```bash
curl -X POST https://www.xiaoqizhisuan.cn/mcp \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -H "x-api-key: xq_你的API密钥" \
  -d '{"jsonrpc":"2.0","id":2,"method":"tools/list","params":{}}'
```
# 3. 调用指定工具 | Call Target Tool
```bash
curl -X POST https://www.xiaoqizhisuan.cn/mcp \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -H "x-api-key: xq_你的API密钥" \
  -d '{"jsonrpc":"2.0","id":3,"method":"tools/call","params":{"name":"bazi_dayun"}}'
```

## 错误码说明 | Error Code Explanation
- 401: 缺少或无效 API 密钥 | Missing or invalid API Key
- 402: 账户余额不足 | Insufficient account balance
- 403: API 密钥已封禁 | API Key disabled
- 500: 服务端内部异常 | Server internal error

## 注意事项 | Notes
1. EN: This service is driven by data analysis and cognitive science for rational decision reference.
   CN: 本服务基于数据分析与认知科学，仅作理性决策参考。
2. EN: No feudal superstitious content is involved.
   CN: 内容不含封建迷信导向。
3. EN: It is recommended to add a disclaimer when using this service.
   CN: 接入使用时建议补充免责声明。

---
EN: This service is officially provided by Xiaoqi Intelligent Calculation WeChat Official Account.
CN: 本服务由小奇智算官方服务号独家提供。详细调用示例：https://www.xiaoqizhisuan.cn/help.html

---

### 关键术语对照（统一规范）
1. 八字 — BaZi / Eight Characters
2. 奇门遁甲 — Qi Men Dun Jia
3. 大运 — Great Fortune
4. 流年 — Fleeting Year
5. 排盘 — Chart Generation
6. 解盘 — Chart Interpretation
7. 用神 — Useful God
8. 即时盘 — Immediate Chart
9. 终身盘 — Lifetime Chart
