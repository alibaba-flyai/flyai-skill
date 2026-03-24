# search-poi ref

## 景点搜索 (search-poi)

### 参数说明

- **--city-name** (必填): 景点所在城市名称，用于缩小景点范围
- **--poi-level** (可选): 景点等级
  - 取值范围：1-5
- **--keyword** (可选): 景点名称关键词
  - 例子：`西湖`、`故宫`、`长城`
- **--category** (可选): 景点类型
  - 可选值：`自然风光`、`山湖田园`、`森林丛林`、`峡谷瀑布`、`沙滩海岛`、`沙漠草原`、`人文古迹`、`古镇古村`、`历史古迹`、`园林花园`、`宗教场所`、`公园乐园`、`主题乐园`、`水上乐园`、`影视基地`、`动物园`、`植物园`、`海洋馆`、`体育场馆`、`演出赛事`、`剧院剧场`、`博物馆`、`纪念馆`、`展览馆`、`地标建筑`、`市集`、`文创街区`、`城市观光`、`户外活动`、`滑雪`、`漂流`、`冲浪`、`潜水`、`露营`、`温泉`
  - 仅支持单选

### 调用示例

```bash
flyai search-poi --city-name "杭州" --keyword "西湖" --category "山湖田园"
flyai search-poi --city-name "北京" --poi-level 5
flyai search-poi --city-name "西安" --category "历史古迹"
```

### 输出示例

```json
{
    "data": {
      "itemList": [
        {
          "address": "陕西省西安市莲湖区北院门...", // 详细地址
          "id": "177224", // 景点唯一标识
          "mainPic": "https://img.alicdn.com/tfscom/...", // 主图
          "jumpUrl": "...", // 详情/下单跳转链接
          "name": "西安钟鼓楼", // 景点名称
          "freePoiStatus": "...", // 景点收费状态：，例如："FREE"，枚举值如下："FREE"：免费景点，"NOT_FREE"：收费景点，"UNKNOWN"：未知，不确定是否收费
          "ticketInfo": // 门票信息
          {
              "price": null, // 价格
              "priceDate": "2026-03-19", // 价格适用日期
              "ticketName": "西安鼓楼门票 成人票" // 票种名称
          }
        }
      ]
    },
    "message": "success",
    "status": 0
}
```