# FlyAI Skill - 飞猪旅行技能

[![Version](https://img.shields.io/badge/version-1.1.0-blue.svg)](https://github.com/alibaba-flyai/flyai-skill)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

> 🌍 基于飞猪 MCP 的旅行助手技能，提供酒店预订、机票查询、景点推荐等一站式旅行服务

## ✨ 核心功能

- **🏨 酒店搜索**: 支持按目的地、星级、价格、床型等多维度筛选
- **✈️ 机票查询**: 实时航班搜索，支持往返程、舱位选择、时段筛选
- **🎯 景点推荐**: 覆盖全国主要城市景点，支持等级、类型筛选
- **🔍 智能搜索**: 自然语言查询，一键获取酒店、机票、景点综合结果
- **📅 时间感知**: 支持入住/退房日期、出发/返程日期等时间参数
- **💰 价格比较**: 支持价格区间筛选和排序，帮你找到最优价格

## 🚀 快速开始

### 方式一：通过 ClawHub 安装

```bash
clawhub install flyai
```

### 方式二：通过 NPX 安装

```bash
npx skills add alibaba-flyai/flyai-skill
```

### 验证安装

```bash
flyai --help
```

## 📖 使用示例

### 1. 自然语言搜索 (推荐)

```bash
# 搜索三亚的酒店
flyai fliggy-fast-search --query "三亚亚龙湾五星级酒店"

# 查询北京到上海的机票
flyai fliggy-fast-search --query "明天北京飞上海的航班"

# 查找杭州西湖周边景点
flyai fliggy-fast-search --query "杭州西湖有什么好玩的"

# 搜索日本签证服务
flyai fliggy-fast-search --query "日本个人旅游签证"
```

### 2. 结构化酒店搜索

```bash
# 基础搜索
flyai search-hotels --dest-name "杭州"

# 带日期和景点筛选
flyai search-hotels --dest-name "杭州" --poi-name "西湖" \
  --check-in-date 2026-03-25 --check-out-date 2026-03-27

# 高端酒店筛选
flyai search-hotels --dest-name "三亚" --hotel-stars "4,5" \
  --sort rate_desc --max-price 1000
```

### 3. 机票查询

```bash
# 单程航班
flyai search-flight --origin "北京" --destination "上海" \
  --dep-date 2026-03-28

# 往返航班
flyai search-flight --origin "上海" --destination "东京" \
  --dep-date 2026-04-01 --back-date 2026-04-07

# 低价优先排序
flyai search-flight --origin "北京" --destination "广州" \
  --dep-date 2026-03-30 --sort-type 3
```

### 4. 景点搜索

```bash
# 搜索指定城市的景点
flyai search-poi --city-name "西安" --category "历史古迹"

# 搜索特定等级的景点
flyai search-poi --city-name "北京" --poi-level 5

# 关键词搜索
flyai search-poi --city-name "杭州" --keyword "西湖" \
  --category "山湖田园"
```

## 🛠️ 配置说明

该工具无需 API Key 即可试用。如需增强结果质量，可配置可选的 API:

```bash
flyai config set FLYAI_API_KEY "your-api-key"
```

## 📚 详细文档

| 命令 | 说明 | 文档 |
|------|------|------|
| `fliggy-fast-search` | 自然语言极速搜索 | [查看文档](skills/flyai/references/fliggy-fast-search.md) |
| `search-hotels` | 结构化酒店搜索 | [查看文档](skills/flyai/references/search-hotels.md) |
| `search-flight` | 航班查询 | [查看文档](skills/flyai/references/search-flight.md) |
| `search-poi` | 景点搜索 | [查看文档](skills/flyai/references/search-poi.md) |

## 📋 输出格式

所有命令输出**单行 JSON**到 `stdout`,错误和提示信息输出到 `stderr`,便于与 `jq` 或 Python 等工具配合使用。

### 友好展示要求

- ✅ **图片展示**: 使用 `![]({imageUrl})` 格式单独一行
- ✅ **预订链接**: 使用 `[Click to book]({url})` 格式单独一行
- ✅ **层级结构**: 使用 Markdown 标题 (#, ##, ###) 和列表
- ✅ **表格对比**: 多选项比较使用 Markdown 表格
- ✅ **时间顺序**: 行程项目按时间先后排列
- ✅ **重点强调**: 日期、地点、价格、限制条件等关键信息加粗

## 🤝 贡献指南

欢迎提交 Issue 和 Pull Request!

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情

## 🔗 相关链接

- [FlyAI 开放平台](https://open.fly.ai/)
- [飞猪旅行](https://www.fliggy.com/)
- [ClawHub 技能市场](https://github.com/claw-lang/clawhub)

---

<div align="center">
  <sub>Built with ❤️ by Alibaba Fliggy Team</sub>
</div>
