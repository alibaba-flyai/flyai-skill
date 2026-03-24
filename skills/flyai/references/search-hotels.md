# search-hotels ref

## 酒店搜索 (search-hotels)

### 参数说明

- **--dest-name** (必填): 目的地，只能是 `国家/省/市/区县`
- **--key-words** (可选): 关键词
- **--poi-name** (可选): 景点名称，用于按周边景点筛选
- **--hotel-types** (可选): 酒店类型
  - 可选值：`酒店`、`民宿`、`客栈`
- **--sort** (可选): 排序方式
  - 可选值：`distance_asc`、`rate_desc`、`price_asc`、`price_desc`、`no_rank`
- **--check-in-date** (可选): 入住日期，格式 YYYY-MM-DD
- **--check-out-date** (可选): 退房日期，格式 YYYY-MM-DD
- **--hotel-stars** (可选): 星级，逗号分隔
  - 取值范围：1-5
- **--hotel-bed-types** (可选): 酒店床型，多选时用英文逗号分隔
  - 可选值：`大床房`、`双床房`、`多床房`
- **--max-price** (可选): 最高价（元）

### 调用示例

```bash
flyai search-hotels --dest-name "杭州" --poi-name "西湖" --check-in-date 2026-03-10 --check-out-date 2026-03-12
flyai search-hotels --dest-name "三亚" --hotel-stars "4,5" --sort rate_desc --max-price 800
```

### 输出示例

```json
{
  "status": 0,
  "message": "success",
  "data": {
    "itemList": [
        {
          "address": "环城西路2号", // 地址
          "brandName": "雷迪森", // 品牌名称
          "decorationTime": "2014", // 装修年份
          "interestsPoi": "近杭州西湖风景名胜区", // 周边兴趣点描述
          "latitude": "30.259204", // 纬度
          "longitude": "120.159246", // 经度
          "mainPic": "https://img.alicdn.com/...", // 主图
          "detailUrl": "...", // 详情/下单跳转链接
          "name": "杭州望湖宾馆", // 酒店名称
          "price": "¥618", // 价格
          "review": "西湖边的位置，家庭出游首选", // 点评摘要
          "score": "5.0", // 评分，最高5.0分
          "scoreDesc": "超棒", // 评分描述
          "shId": "10021423", // 酒店 ID
          "star": "豪华型" // 星级/档次
        }
    ]
  }
}
```
