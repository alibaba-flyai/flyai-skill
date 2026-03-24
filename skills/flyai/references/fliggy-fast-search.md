# fliggy-fast-search ref

## 极速搜索 (fliggy-fast-search)

### 参数说明

- **--query** (必填): 搜索关键词，支持自然语言查询酒店、机票等
   - 从以下 QueryPattern 中选择最匹配的一种：  
   - **位置/附近类**：如“附近景点”“poi附近餐厅”  
   - **POI综合类**：如“poi自由行”“poi线路”  
   - **景点/景玩类**：如“景点门票”“景玩poi旅拍”  
   - **目的地类**：如“目的地攻略”“目的地酒店”  
   - **玩乐体验类**：如“温泉SPA”“滑雪”  
   - **线路/跟团/定制类**：如“跟团游”“定制游”  
   - **美食类**：如“美食攻略”“自助餐”  
   - **签证/证件类**：如“签证”“旅游保险”  
   - **通讯/网络类**：如“wifi租赁”“电话卡”  
   - **邮轮类**：如“邮轮”“出海观光”  
   - **其他类**：如“时间泛词”“商圈poi”  

### 调用示例

```bash
flyai fliggy-fast-search --query "法国签证"
flyai fliggy-fast-search --query "杭州跟团游"
flyai fliggy-fast-search --query "杭州三日游"
flyai fliggy-fast-search --query "邮轮上海"
flyai fliggy-fast-search --query "香港电话卡"
```

### 输出示例

```json
{
    "data": {
      "itemList": [
        {
          "info": {
              "jumpUrl": "...", // 详情/下单跳转链接
              "picUrl": "...", // 主图
              "price": "...", // 价格
              "scoreDesc": "", // 评分描述
              "star": "...", // 星级
              "tags": ["..."], // 标签
              "title": "..." // 产品标题
          }
        }
      ]
    },
    "message": "success",
    "status": 0
}
```
