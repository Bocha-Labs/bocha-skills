# SKILL.md - bochawebsearch

<!--
---
name: bochawebsearch
version: 1.0.0
description: 当用户想要获取从全网搜索任何网页信息和网页链接，结果准确、摘要完整，更适合 AI 使用时，你应该调用此技能。买家通过本 Skill 向卖家服务端发起请求，完成支付后获取相关结果。
tags: [search, web, paid, a2m]
---
-->

## 技能概述

本 Skill 提供从全网搜索任何网页信息和网页链接，结果准确、摘要完整，更适合 AI 使用，是基于 A2M 智能收协议（HTTP 402）的付费资源。买家（消费者 Agent）通过本 Skill 向卖家服务端发起资源请求，服务端将返回一个 402 Payment-Needed 报文，然后买家调用支付宝的 alipay-pay-for-402-service 技能完成付款。

## 触发条件

当用户请求满足以下条件时触发本 Skill：
- 需要从全网搜索网页信息
- 需要获取准确、完整摘要的搜索结果
- 搜索结果需要适合 AI 进一步处理使用

### 典型触发场景
- "帮我搜索一下阿里巴巴 2024 年的 ESG 报告"
- "查找最新的AI技术文章"
- "我需要关于AI的行业分析报告"

## 资源接口信息

**接口地址**: `https://api.bocha.cn/v1/marketplace/alipay/bochawebsearch`

**请求方法**: POST

**请求头**:
```
Content-Type: application/json
```

**请求体参数**:
| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| query | string | 是 | 搜索关键词 |
| freshness | string | 否 | 时间范围，可选值：noLimit(默认), oneDay, oneWeek, oneMonth, oneYear |
| summary | boolean | 否 | 是否返回摘要，默认 true |
| count | integer | 否 | 返回结果数量，默认 10，最大 50 |

## 工作流程

### 第一步：提取搜索参数

从用户请求中提取搜索关键词和相关参数：

```
1. query: 从用户问题中提取核心搜索词，需要保留“最近”、“今年”、“今年1月”等时间范围描述
2. freshness: 根据用户描述的时间范围确定，默认选择 noLimit，以便 web-search 结合 query 中的时间范围描述自动改写最合适的 freshness 值。
3. summary: 默认 true
4. count: 默认 10，如用户明确要求更多结果则调整
```

### 第二步：发起资源请求

向博查 API 发起 POST 请求：

```bash
curl -X POST "https://api.bocha.cn/v1/marketplace/alipay/bochawebsearch" \
  -H "Content-Type: application/json" \
  -d '{
    "query": "<用户搜索词>",
    "freshness": "<时间范围>",
    "summary": true,
    "count": <结果数量>
  }'
```

### 第三步：处理 402 响应

服务端将返回**状态码为 402 的响应报文**，其中包含 `Payment-Needed` 响应头。

**402 响应示例**:
```json
{
  "error": {
    "code": "PAYMENT_REQUIRED",
    "message": "该资源需要支付后才能访问",
    "paymentInfo": {
      "serviceId": "bochawebsearch-service",
      "amount": 0.50,
      "currency": "CNY",
      "description": "博查 Web 搜索服务"
    }
  }
}
```

### 第四步：调用支付技能

将**整个 402 响应报文**传递给支付宝的 **alipay-pay-for-402-service** 技能，引导用户完成付款。

**调用示例**:
```
调用 alipay-pay-for-402-service，传入 402 响应内容，等待用户完成支付
```

### 第五步：支付完成后处理

支付成功后，重新发起原始请求获取搜索结果，然后将结果呈现给用户。

## 异常情况处理

| 异常类型 | 处理方式 |
|----------|----------|
| 用户拒绝付款 | 尊重用户选择，告知用户该内容为付费资源，如需获取请完成支付 |
| 请求返回非 402 状态码（200） | 直接展示搜索结果内容 |
| 请求返回 400 错误 | 告知用户请求参数有误，请检查搜索词后重试 |
| 请求返回 401 错误 | 告知用户未授权访问该资源，请检查账户余额或资源包后重试 |
| 请求返回 429 错误 | 告知用户请求频率过高，请稍后重试 |
| 请求返回 5xx 错误 | 告知用户服务暂时不可用，建议稍后重试 |
| 网络超时 | 告知用户网络连接超时，建议检查网络后重试 |
| 支付失败 | 由 alipay-pay-for-402-service 技能处理，引导用户重新支付 |
| 支付超时 | 由 alipay-pay-for-402-service 技能处理，提示支付已超时 |

## 输出格式规范

成功获取搜索结果后，按以下格式呈现：

```markdown
## 搜索结果：<搜索关键词>

共找到 <count> 条结果

### <结果标题 1>
- **来源**: <来源网站>
- **链接**: <URL>
- **摘要**: <结果摘要>
- **时间**: <发布时间>

### <结果标题 2>
...
```

## 示例对话

**用户**: 帮我搜索一下阿里巴巴 2024 年的 ESG 报告

**Skill 执行**:
1. 提取参数：query="阿里巴巴 2024 年的 ESG 报告", freshness="noLimit", summary=true, count=10
2. 发起 POST 请求到博查 API
3. 收到 402 响应
4. 调用 alipay-pay-for-402-service 引导支付
5. 支付成功后获取结果并展示

## 注意事项

1. **付费资源提示**: 在发起请求前，应告知用户这是付费服务，需要完成支付后才能获取结果
2. **参数校验**: 确保 query 不为空，count 不超过 50
3. **支付跳转**: 严格遵循 A2M 协议，收到 402 后必须调用 alipay-pay-for-402-service，不可自行处理支付
4. **结果展示**: 保持结果格式清晰，链接完整可点击
5. **错误处理**: 友好地向用户解释错误原因，并提供可操作的建议

## 依赖技能

- `alipay-pay-for-402-service`: 处理 HTTP 402 支付流程

## 版本历史

| 版本 | 日期 | 变更说明 |
|------|------|----------|
| 1.0.0 | 2026-04-17 | 初始版本，支持博查 Web 搜索 API |