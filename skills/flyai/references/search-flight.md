# search-flight ref

## 机票搜索 (search-flight)

### 参数说明

- **--origin** (必填): 出发地城市或机场
- **--destination** (可选): 目的地城市或机场
- **--dep-date** (可选): 出发日期
- **--dep-date-start** / **--dep-date-end** (可选): 出发日期范围
- **--back-date** (可选): 返程日期
- **--back-date-start** / **--back-date-end** (可选): 返程日期范围
- **--journey-type** (可选): 行程类型
  - 取值：`1` = 直达，`2` = 中转
- **--seat-class-name** (可选): 舱位名称
- **--transport-no** (可选): 航班号
- **--transfer-city** (可选): 中转城市
- **--dep-hour-start** / **--dep-hour-end** (可选): 出发时段（小时）
- **--arr-hour-start** / **--arr-hour-end** (可选): 到达时段（小时）
- **--total-duration-hour** (可选): 总飞行时长（小时）
- **--max-price** (可选): 最高价格
- **--sort-type** (可选): 排序方式
  - `1`：价格高 → 低
  - `2`：推荐排序
  - `3`：价格低 → 高
  - `4`：耗时短 → 长
  - `5`：耗时长 → 短
  - `6`：出发早 → 晚
  - `7`：出发晚 → 早
  - `8`：直达优先

### 调用示例

```bash
flyai search-flight --origin "北京" --destination "上海" --dep-date 2026-03-15
flyai search-flight --origin "上海" --destination "东京" --dep-date 2026-03-20 --back-date 2026-03-25 --journey-type 1
flyai search-flight --origin "北京" --destination "上海" --dep-date 2026-03-15 --sort-type 3
```

### 输出示例

```json
{
  "data": {
    "itemList": [
      {
        "adultPrice": "¥400.0", // 成人单价
        "journeys": // 行程列表，每项为一条行程
        [
            {
              "journeyType": "直达",
                "segments": // 航段列表
                [
                  {
                    "depCityCode": "BJS", // 出发城市代码
                    "depCityName": "北京", // 出发城市名
                    "depStationCode": "PEK", // 出发场站代码
                    "depStationName": "首都国际机场", // 出发场站名
                    "depStationShortName": "首都", // 出发场站简称
                    "depTerm": "T3", // 出发航站楼
                    "depDateTime": "2026-03-28 21:00:00", // 出发日期时间
                    "depWeekAbbrName": "周六", // 出发日星期缩写
                    "arrCityCode": "SHA", // 到达城市代码
                    "arrCityName": "上海", // 到达城市名
                    "arrStationCode": "PVG", // 到达场站代码
                    "arrStationName": "浦东国际机场", // 到达场站名
                    "arrStationShortName": "浦东", // 到达场站简称
                    "arrTerm": "T2", // 到达航站楼
                    "arrDateTime": "2026-03-28 23:20:00", // 到达日期时间
                    "arrWeekAbbrName": "周六", // 到达日星期缩写
                    "duration": "140分钟", // 本段时长
                    "transportType": "飞机", // 交通类型
                    "marketingTransportName": "国航", // 承运人名称
                    "marketingTransportNo": "CA1883", // 航班号
                    "seatClassName": "经济舱" // 舱位名称
                  }
              ],
              "totalDuration": "140分钟" // 该行程总时长
            }
        ],
        "jumpUrl": "...", // 详情/下单跳转链接
        "totalDuration": "140分钟" // 总时长
      }
    ]
  },
  "message": "success",
  "status": 0
}
```
