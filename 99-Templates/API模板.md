# 🔌 API 名称

> 一句话描述这个 API 的作用

---

## 📋 基本信息

| 属性 | 内容 |
|------|------|
| **请求方法** | GET / POST / PUT / DELETE |
| **请求路径** | `/api/v1/...` |
| **认证方式** | Bearer Token / Cookie / None |
| **Content-Type** | application/json |

---

## 📥 请求参数

### Path 参数
| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| `id` | string | 是 | 资源 ID |

### Query 参数
| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|------|--------|------|
| `page` | number | 否 | 1 | 页码 |
| `limit` | number | 否 | 20 | 每页数量 |

### Body 参数
```json
{
  "field1": "string",  // 说明
  "field2": 123        // 说明
}
```

---

## 📤 响应格式

### 成功响应 (200)
```json
{
  "code": 0,
  "data": {
    "id": "xxx",
    "name": "xxx"
  },
  "message": "success"
}
```

### 错误响应
```json
{
  "code": 400,
  "data": null,
  "message": "错误描述"
}
```

---

## 📝 错误码

| 状态码 | 说明 |
|--------|------|
| 200 | 成功 |
| 400 | 参数错误 |
| 401 | 未认证 |
| 403 | 无权限 |
| 404 | 资源不存在 |
| 500 | 服务器错误 |

---

## 💡 示例

### cURL
```bash
curl -X POST 'https://api.example.com/v1/...' \
  -H 'Authorization: Bearer <token>' \
  -H 'Content-Type: application/json' \
  -d '{
    "field1": "value1"
  }'
```

### JavaScript
```javascript
const response = await fetch('/api/v1/...', {
  method: 'POST',
  headers: {
    'Authorization': `Bearer ${token}`,
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({ field1: 'value1' })
});
```
