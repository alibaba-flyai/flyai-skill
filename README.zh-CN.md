<p align="center">
  <h1 align="center">✈️ FlyAI：旅行、机票与酒店搜索及预订</h1>
  <p align="center">
    <strong>由飞猪提供旅行搜索能力，直接在 Claude Code、OpenClaw 及其他支持 Skill 的智能体中使用。</strong>
  </p>
  <p align="center">
    用自然语言搜索机票、酒店、景点、演唱会等旅行服务。<br/>
    无需打开浏览器或切换应用，直接提问即可。
  </p>
  <p align="center">
    <a href="README.md">English</a> | <a href="README.zh-CN.md">中文</a>
  </p>
  <p align="center">
    <a href="https://www.npmjs.com/package/@fly-ai/flyai-cli"><img src="https://img.shields.io/npm/v/@fly-ai/flyai-cli?label=flyai-cli&color=blue" alt="npm 版本"></a>
    <a href="https://www.npmjs.com/package/@fly-ai/flyai-cli"><img src="https://img.shields.io/npm/dw/@fly-ai/flyai-cli?label=npm%20downloads&color=blue" alt="npm 下载量"></a>
    <a href="https://www.skills.sh/alibaba-flyai/flyai-skill/flyai"><img src="https://skills.sh/b/alibaba-flyai/flyai-skill" alt="Skills 安装量"></a>
    <a href="https://clawhub.ai/yealexchen/skills/flyai"><img src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fclawhub.ai%2Fapi%2Fv1%2Fskills%2Fflyai&amp;query=%24.skill.stats.downloads&amp;label=ClawHub%20downloads&amp;color=purple" alt="ClawHub 下载量"></a>
    <a href="https://github.com/alibaba-flyai/flyai-skill/stargazers"><img src="https://img.shields.io/github/stars/alibaba-flyai/flyai-skill?style=social" alt="GitHub Stars"></a>
    <a href="https://github.com/alibaba-flyai/flyai-skill/forks"><img src="https://img.shields.io/github/forks/alibaba-flyai/flyai-skill?style=social" alt="GitHub Forks"></a>
    <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-green" alt="MIT 许可证"></a>
    <a href="https://github.com/alibaba-flyai/flyai-skill"><img src="https://img.shields.io/badge/version-1.0.14-orange" alt="Skill 版本"></a>
  </p>
  <p align="center">
    <a href="https://open.fly.ai/">主页</a> ·
    <a href="#快速开始">快速开始</a> ·
    <a href="#命令">命令</a> ·
    <a href="#典型使用场景">使用场景</a> ·
    <a href="#使用示例">使用示例</a> ·
    <a href="#联系我们">联系我们</a>
  </p>
</p>

<p align="center">
  <img src="assets/demo.gif" alt="FlyAI 演示" width="700">
</p>

---

## FlyAI 的优势

当你与 AI 编程智能体讨论旅行计划、查询场地或比较方案时，FlyAI 可以让你**直接在终端中搜索实时旅行商品**。它将 [Claude Code](https://docs.anthropic.com/en/docs/claude-code)、[OpenClaw](https://github.com/nicepkg/openclaw) 及其他支持 Skill 的智能体连接到阿里巴巴集团旗下的[飞猪](https://www.fliggy.com/)旅行平台，快速返回结构化结果和预订链接。

- **自然语言输入，结构化数据输出**：支持中文或英文提问，返回的 JSON 可用于管道处理、筛选或渲染。
- **八个专用搜索命令**：支持广泛搜索、AI 语义搜索及深度比较。
- **结果可预订**：每条结果都包含直达预订链接。
- **零配置起步**：开箱即用，也可配置 API Key 获取增强结果。

## 快速开始

### 第一步：安装 Skill

**OpenClaw：**

```bash
# 通过 clawhub 安装（推荐）
clawhub install flyai

# 或通过 npx 安装
npx skills add alibaba-flyai/flyai-skill
```

**Claude Code：**

```bash
cp -r /path/to/flyai-skill/skills/flyai ~/.claude/skills/flyai
```

### 第二步：安装 CLI

```bash
npm i -g @fly-ai/flyai-cli
```

### 第三步：验证

```bash
flyai keyword-search --query "things to do in Tokyo"
```

看到结构化 JSON 输出后，即可开始使用。

### 第四步：配置（可选）

无需 API Key 即可使用此 Skill。如需增强结果，可进行以下配置：

```bash
flyai config set FLYAI_API_KEY "your-key"
```

## 命令

FlyAI 提供八个命令，分别适用于不同的搜索场景：

| 命令 | 用途 | 必填参数 |
|------|------|----------|
| `keyword-search` | 通过自然语言关键词搜索所有旅行品类 | `--query` |
| `ai-search` | 语义搜索，理解复杂意图以获取精准结果 | `--query` |
| `search-flight` | 支持深度筛选的结构化机票搜索 | `--origin` |
| `search-train` | 支持深度筛选的结构化火车票搜索 | `--origin` |
| `search-hotel` | 按目的地搜索酒店 | `--dest-name` |
| `search-poi` | 按城市搜索景点与兴趣点 | `--city-name` |
| `search-marriott-hotel` | 按目的地搜索万豪集团酒店 | `--dest-name` |
| `search-marriott-package` | 搜索万豪集团酒店套餐 | `--keyword` |

### `keyword-search`：全品类搜索

一次查询覆盖酒店、机票、门票、线路游、邮轮、签证、电话卡等旅行品类。

**OpenClaw：**

```
/flyai keyword-search --query "Hangzhou 3-day trip"
/flyai keyword-search --query "France visa"
/flyai keyword-search --query "Shanghai cruise"
```

**Claude Code：**

```
/flyai keyword-search --query "Hangzhou 3-day trip"
/flyai keyword-search --query "France visa"
/flyai keyword-search --query "Shanghai cruise"
```

**CLI：**

```bash
flyai keyword-search --query "Hangzhou 3-day trip"
```

### `ai-search`：语义搜索

通过 AI 理解自然语言和复杂旅行意图，支持酒店、景点、机票、火车票及混合查询。

**OpenClaw / Claude Code：**

```
/flyai ai-search --query "3-day trip to Hangzhou for Labor Day, budget 2000 per person, want to stay near West Lake"
/flyai ai-search --query "Direct flight from Shanghai to Tokyo next week, find good value flights and hotels"
```

**CLI：**

```bash
flyai ai-search --query "3-day trip to Hangzhou for Labor Day, budget 2000 per person"
```

### `search-flight`：机票比较

结构化搜索机票，支持排序、舱位、价格上限和时间筛选。

**OpenClaw / Claude Code：**

```
/flyai search-flight --origin "Beijing" --destination "Shanghai" --dep-date 2026-04-15
```

**CLI：**

```bash
# 基础单程搜索
flyai search-flight --origin "Beijing" --destination "Shanghai" --dep-date 2026-04-15

# 往返行程，仅直飞，按价格从低到高排序
flyai search-flight \
  --origin "Shanghai" --destination "Tokyo" \
  --dep-date 2026-04-20 --back-date 2026-04-25 \
  --journey-type 1 --sort-type 3
```

<details>
<summary><strong>全部机票搜索参数</strong></summary>

| 参数 | 说明 |
|------|------|
| `--origin` | 出发城市或机场，**必填** |
| `--destination` | 到达城市或机场 |
| `--dep-date` | 出发日期（`YYYY-MM-DD`） |
| `--dep-date-start` / `--dep-date-end` | 出发日期范围 |
| `--back-date` | 返回日期 |
| `--back-date-start` / `--back-date-end` | 返回日期范围 |
| `--journey-type` | `1` = 直飞，`2` = 中转 |
| `--seat-class-name` | 舱位名称 |
| `--transport-no` | 航班号 |
| `--transfer-city` | 中转城市 |
| `--dep-hour-start` / `--dep-hour-end` | 出发时段 |
| `--arr-hour-start` / `--arr-hour-end` | 到达时段 |
| `--total-duration-hour` | 总时长上限（小时） |
| `--max-price` | 价格上限 |
| `--sort-type` | `1` 价格降序 · `2` 推荐 · `3` 价格升序 · `4` 时长升序 · `5` 时长降序 · `6` 出发早优先 · `7` 出发晚优先 · `8` 直飞优先 |

</details>

### `search-train`：火车票比较

结构化搜索火车票，支持排序、席别、价格上限和时间筛选。

**OpenClaw / Claude Code：**

```
/flyai search-train --origin "Beijing" --destination "Shanghai" --dep-date 2026-04-15
```

**CLI：**

```bash
# 基础单程搜索
flyai search-train --origin "Beijing" --destination "Shanghai" --dep-date 2026-04-15

# 仅直达、二等座，按价格从低到高排序
flyai search-train \
  --origin "Shanghai" --destination "Hangzhou" \
  --dep-date 2026-04-20 --journey-type 1 \
  --seat-class-name "second class" --sort-type 3
```

<details>
<summary><strong>全部火车票搜索参数</strong></summary>

| 参数 | 说明 |
|------|------|
| `--origin` | 出发城市或车站，**必填** |
| `--destination` | 到达城市或车站 |
| `--dep-date` | 出发日期（`YYYY-MM-DD`） |
| `--dep-date-start` / `--dep-date-end` | 出发日期范围 |
| `--back-date` | 返回日期 |
| `--back-date-start` / `--back-date-end` | 返回日期范围 |
| `--journey-type` | `1` = 直达，`2` = 中转 |
| `--seat-class-name` | 席别：`second class`（二等座）· `first class`（一等座）· `business class`（商务座）· `hard sleeper`（硬卧）· `soft sleeper`（软卧） |
| `--transport-no` | 车次，多个值用逗号分隔 |
| `--transfer-city` | 中转城市，多个值用逗号分隔 |
| `--dep-hour-start` / `--dep-hour-end` | 出发时段（24 小时制） |
| `--arr-hour-start` / `--arr-hour-end` | 到达时段（24 小时制） |
| `--total-duration-hour` | 总时长上限（小时） |
| `--max-price` | 价格上限（人民币） |
| `--sort-type` | `1` 价格降序 · `2` 推荐 · `3` 价格升序 · `4` 时长升序 · `5` 时长降序 · `6` 出发早优先 · `7` 出发晚优先 · `8` 直达优先 |

</details>

### `search-hotel`：酒店比较

按目的地搜索酒店，支持星级、床型、价格范围和附近兴趣点筛选。

**OpenClaw / Claude Code：**

```
/flyai search-hotel --dest-name "Hangzhou" --poi-name "West Lake" --check-in-date 2026-04-10 --check-out-date 2026-04-12
```

**CLI：**

```bash
# 杭州西湖附近的酒店
flyai search-hotel \
  --dest-name "Hangzhou" --poi-name "West Lake" \
  --check-in-date 2026-04-10 --check-out-date 2026-04-12

# 三亚每晚 800 元以下的四至五星级酒店，按评分排序
flyai search-hotel \
  --dest-name "Sanya" --hotel-stars "4,5" \
  --sort rate_desc --max-price 800
```

<details>
<summary><strong>全部酒店搜索参数</strong></summary>

| 参数 | 说明 |
|------|------|
| `--dest-name` | 目的地（国家、省、市、区），**必填** |
| `--key-words` | 搜索关键词 |
| `--poi-name` | 附近景点名称 |
| `--hotel-types` | `酒店` · `民宿` · `客栈` |
| `--sort` | `distance_asc`（距离升序）· `rate_desc`（评分降序）· `price_asc`（价格升序）· `price_desc`（价格降序）· `no_rank`（不排序） |
| `--check-in-date` | 入住日期（`YYYY-MM-DD`） |
| `--check-out-date` | 离店日期（`YYYY-MM-DD`） |
| `--hotel-stars` | 星级，多个值用逗号分隔（`1`-`5`） |
| `--hotel-bed-types` | `大床房` · `双床房` · `多床房` |
| `--max-price` | 每晚价格上限（人民币） |

</details>

### `search-poi`：景点与活动

按城市、类别或等级查找景点，覆盖 AAAAA 级景区到当地冲浪学校等兴趣点。

**OpenClaw / Claude Code：**

```
/flyai search-poi --city-name "Xi'an" --category "历史古迹"
```

**CLI：**

```bash
# 西安历史古迹
flyai search-poi --city-name "Xi'an" --category "历史古迹"

# 北京高等级景点
flyai search-poi --city-name "Beijing" --poi-level 5

# 杭州湖泊与园林
flyai search-poi --city-name "Hangzhou" --keyword "West Lake" --category "山湖田园"
```

<details>
<summary><strong>全部景点搜索参数</strong></summary>

| 参数 | 说明 |
|------|------|
| `--city-name` | 城市名称，**必填** |
| `--keyword` | 景点名称关键词 |
| `--poi-level` | 景点等级（`1`-`5`） |
| `--category` | 单个类别，可选：自然风光 · 山湖田园 · 森林丛林 · 峡谷瀑布 · 沙滩海岛 · 沙漠草原 · 人文古迹 · 古镇古村 · 历史古迹 · 园林花园 · 宗教场所 · 公园乐园 · 主题乐园 · 水上乐园 · 影视基地 · 动物园 · 植物园 · 海洋馆 · 体育场馆 · 演出赛事 · 剧院剧场 · 博物馆 · 纪念馆 · 展览馆 · 地标建筑 · 市集 · 文创街区 · 城市观光 · 户外活动 · 滑雪 · 漂流 · 冲浪 · 潜水 · 露营 · 温泉 |

</details>

### `search-marriott-hotel`：万豪酒店搜索

按目的地搜索万豪集团酒店，支持品牌、床型、价格及附近兴趣点筛选。

**OpenClaw / Claude Code：**

```
/flyai search-marriott-hotel --dest-name "Shanghai" --hotel-brands "JW Marriott,Sheraton" --check-in-date 2026-04-10 --check-out-date 2026-04-12
```

**CLI：**

```bash
# 上海的万豪集团酒店
flyai search-marriott-hotel \
  --dest-name "Shanghai" --hotel-brands "JW Marriott,Sheraton" \
  --check-in-date 2026-04-10 --check-out-date 2026-04-12

# 杭州每晚 1200 元以下的万豪集团酒店，按价格排序
flyai search-marriott-hotel \
  --dest-name "Hangzhou" --sort price_asc --max-price 1200
```

<details>
<summary><strong>全部万豪酒店搜索参数</strong></summary>

| 参数 | 说明 |
|------|------|
| `--dest-name` | 目的地（国家、省、市、区），**必填** |
| `--key-words` | 搜索关键词 |
| `--poi-name` | 附近景点名称 |
| `--hotel-brands` | 万豪旗下品牌，多个值用逗号分隔 |
| `--hotel-name` | 酒店名称，支持精确或模糊匹配 |
| `--hotel-bed-types` | `大床房` · `双床房` · `多床房` |
| `--max-price` | 每晚价格上限（人民币） |
| `--sort` | `distance_asc`（距离升序）· `rate_desc`（评分降序）· `price_asc`（价格升序）· `price_desc`（价格降序）· `no_rank`（不排序） |
| `--check-in-date` | 入住日期（`YYYY-MM-DD`） |
| `--check-out-date` | 离店日期（`YYYY-MM-DD`） |

</details>

### `search-marriott-package`：万豪套餐搜索

按城市、品牌或酒店名称搜索万豪集团酒店套餐及组合产品，例如下午茶和 SPA 套餐。

**OpenClaw / Claude Code：**

```
/flyai search-marriott-package --keyword "Shanghai"
/flyai search-marriott-package --keyword "JW Marriott" --sort-type price_asc
```

**CLI：**

```bash
# 上海万豪套餐
flyai search-marriott-package --keyword "Shanghai"

# JW 万豪套餐，按价格排序
flyai search-marriott-package --keyword "JW Marriott" --sort-type price_asc
```

<details>
<summary><strong>全部万豪套餐搜索参数</strong></summary>

| 参数 | 说明 |
|------|------|
| `--keyword` | 搜索关键词，可填写省、市、品牌、酒店名称或卖点，**必填** |
| `--sort-type` | `price_asc`（价格升序）· `price_desc`（价格降序） |

</details>

## 典型使用场景

### 周末短途游

> “帮我找个从上海出发的周末旅行，机票便宜，住海边不错的酒店，再推荐一些好玩的地方。”

FlyAI 串联 `search-flight`、`search-hotel` 和 `search-poi`，提供包含价格及预订链接的完整旅行方案。

### 低价机票搜索

> “五月北京直飞曼谷，哪天最便宜？”

```
/flyai search-flight --origin "Beijing" --destination "Bangkok" --dep-date-start 2026-05-01 --dep-date-end 2026-05-31 --journey-type 1 --sort-type 3
```

### 多人出游住宿比较

> “比较三亚每晚 500 元以下、有双床房的四星级酒店，按评分排序。”

```
/flyai search-hotel --dest-name "Sanya" --hotel-stars 4 --hotel-bed-types "双床房" --max-price 500 --sort rate_desc
```

### 火车出行规划

> “找下周二北京到上海的直达高铁，二等座。”

```
/flyai search-train --origin "Beijing" --destination "Shanghai" --dep-date 2026-04-07 --journey-type 1 --seat-class-name "second class" --sort-type 3
```

### AI 智能行程规划

> “五一去杭州玩三天，人均预算 2000 元，想住西湖附近。”

```
/flyai ai-search --query "3-day Hangzhou trip for Labor Day, budget 2000 per person, stay near West Lake"
```

### 万豪酒店优惠

> “找上海万豪酒店的下午茶套餐。”

```
/flyai search-marriott-package --keyword "Shanghai" --sort-type price_asc
```

### 本地探索

> “桂林有哪些值得去的自然景点？”

```
/flyai search-poi --city-name "Guilin" --category "自然风光" --poi-level 5
```

## 使用示例

### OpenClaw

在 OpenClaw 中直接用自然语言提问，FlyAI 会在旅行查询时自动启用：

> 找下周五北京直飞上海、600 元以下的机票。

> 比较这周末上海外滩附近的五星级酒店。

> 成都有哪些热门景点？我对自然风光和历史感兴趣。

也可以直接使用斜杠命令：

```
/flyai search-flight --origin "Beijing" --destination "Shanghai" --dep-date 2026-04-25 --max-price 600
```

### Claude Code

在 Claude Code 中用自然语言提问，或使用 `/flyai` 斜杠命令：

> 我计划去日本玩五天，帮我查签证信息、上海出发的航班和东京酒店。

> 找杭州的演唱会和现场演出。

```
/flyai keyword-search --query "5-day Japan trip from Shanghai"
/flyai ai-search --query "Best direct flights and hotels for a week in Tokyo"
/flyai search-flight --origin "Shanghai" --destination "Tokyo" --dep-date 2026-05-01 --sort-type 3
/flyai search-train --origin "Shanghai" --destination "Hangzhou" --dep-date 2026-05-01
/flyai search-hotel --dest-name "Tokyo" --check-in-date 2026-05-01 --check-out-date 2026-05-06
/flyai search-poi --city-name "Tokyo" --category "地标建筑"
/flyai search-marriott-hotel --dest-name "Tokyo" --check-in-date 2026-05-01 --check-out-date 2026-05-06
/flyai search-marriott-package --keyword "Shanghai"
```

## 工作原理

```
向智能体提问 → 启用 FlyAI Skill → 运行 flyai-cli → 调用飞猪 MCP API
                                                        ↓
展示结果 ← 智能体格式化 Markdown ← 返回 JSON 响应 ←────────┘
```

- **运行环境**：Node.js。
- **输出**：单行 JSON 写入 `stdout`，错误和提示写入 `stderr`。
- **上下文隔离**：每个命令在独立的执行上下文中运行。
- **意图匹配**：按意图自动将旅行查询路由到 FlyAI，启用优先级为 90。

## 覆盖的旅行场景

FlyAI 覆盖从出行准备到旅行体验的多个环节：

| 类别 | 示例 |
|------|------|
| **交通** | 机票、火车票、接送机、租车、包车 |
| **住宿** | 酒店、民宿、客栈、机酒套餐 |
| **体验** | 景点门票、一日游、导览、精选旅行线路 |
| **活动** | 演唱会、体育赛事、演出、动漫活动 |
| **服务** | 签证、旅行保险、电话卡、WiFi 租赁 |
| **旅行** | 邮轮、周末游、蜜月游、亲子游、研学游 |

## 联系我们

扫描下方二维码加入钉钉群，获取支持和最新消息。

<img width="508" height="484" alt="FlyAI 钉钉群二维码" src="https://github.com/user-attachments/assets/0c7f15e6-1648-45a5-b383-d1101809a964" />

## 许可证

[MIT](LICENSE)，Copyright (c) 2026 alibaba-flyai
