<p align="center">
  <h1 align="center">✈️ FlyAI — Travel, Flight & Hotel Search and Booking</h1>
  <p align="center">
    <strong>Travel search, powered by Fliggy — right inside Claude Code, OpenClaw, and other skill-compatible agents.</strong>
  </p>
  <p align="center">
    Search flights, hotels, attractions, concerts, and more with natural language.<br/>
    No browser tabs. No app switching. Just ask.
  </p>
  <p align="center">
    <a href="https://www.npmjs.com/package/@fly-ai/flyai-cli"><img src="https://img.shields.io/npm/v/@fly-ai/flyai-cli?label=flyai-cli&color=blue" alt="npm version"></a>
    <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-green" alt="MIT License"></a>
    <a href="https://github.com/alibaba-flyai/flyai-skill/stargazers"><img src="https://img.shields.io/github/stars/alibaba-flyai/flyai-skill?style=social" alt="GitHub Stars"></a>
    <a href="https://github.com/alibaba-flyai/flyai-skill"><img src="https://img.shields.io/badge/version-1.0.13-orange" alt="Skill Version"></a>
  </p>
  <p align="center">
    <a href="https://open.fly.ai/">Homepage</a> ·
    <a href="#quick-start">Quick Start</a> ·
    <a href="#commands">Commands</a> ·
    <a href="#featured-use-cases">Use Cases</a> ·
    <a href="#examples">Examples</a>
  </p>
</p>

<p align="center">
  <img src="assets/demo.gif" alt="FlyAI Demo" width="700">
</p>

---

## Why FlyAI?

You're deep in a conversation with your AI coding agent — planning a trip, researching venues, comparing options. FlyAI lets you **search real-time travel inventory without leaving your terminal**. It connects [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [OpenClaw](https://github.com/nicepkg/openclaw), and other skill-compatible agents to [Fliggy](https://www.fliggy.com/)'s massive travel platform (part of Alibaba Group), giving you structured, bookable results in seconds.

- **Natural language in, structured data out** — ask in plain English or Chinese, get JSON you can pipe, filter, or render
- **Four specialized search commands** — broad discovery or deep comparison, your call
- **Bookable results** — every result includes direct booking links
- **Zero config to start** — works out of the box, optional API key for enhanced results

## Quick Start

### Step 1 — Install the Skill

**OpenClaw:**

```bash
# via clawhub (Recommended)
clawhub install flyai

# or via npx
npx skills add alibaba-flyai/flyai-skill
```

**Claude Code:**

```bash
cp -r /path/to/flyai-skill/skills/flyai ~/.claude/skills/flyai
```

### Step 2 — Install the CLI

```bash
npm i -g @fly-ai/flyai-cli
```

### Step 3 — Verify

```bash
flyai keyword-search --query "things to do in Tokyo"
```

You should see structured JSON output. You're good to go.

### Step 4 — Configure (optional)

The skill works without any API keys. For enhanced results, set one up:

```bash
flyai config set FLYAI_API_KEY "your-key"
```

## Commands

FlyAI provides four commands, each tailored to a different search pattern:

| Command | Purpose | Required Params |
|---------|---------|-----------------|
| `keyword-search` | Natural-language keyword search across all travel categories | `--query` |
| `search-flight` | Structured flight search with deep filtering | `--origin` |
| `search-hotel` | Structured hotel search by destination | `--dest-name` |
| `search-poi` | Attraction & POI search by city | `--city-name` |

### `keyword-search` — Broad Discovery

One query, all categories. Hotels, flights, tickets, tours, cruises, visas, SIM cards — it searches everything.

**OpenClaw:**

```
/flyai keyword-search --query "Hangzhou 3-day trip"
/flyai keyword-search --query "France visa"
/flyai keyword-search --query "Shanghai cruise"
```

**Claude Code:**

```
/flyai keyword-search --query "Hangzhou 3-day trip"
/flyai keyword-search --query "France visa"
/flyai keyword-search --query "Shanghai cruise"
```

**CLI:**

```bash
flyai keyword-search --query "Hangzhou 3-day trip"
```

### `search-flight` — Flight Comparison

Structured flight search with sorting, cabin class, price caps, and time filters.

**OpenClaw / Claude Code:**

```
/flyai search-flight --origin "Beijing" --destination "Shanghai" --dep-date 2026-04-15
```

**CLI:**

```bash
# Basic one-way search
flyai search-flight --origin "Beijing" --destination "Shanghai" --dep-date 2026-04-15

# Round trip, direct flights only, sorted by price (low → high)
flyai search-flight \
  --origin "Shanghai" --destination "Tokyo" \
  --dep-date 2026-04-20 --back-date 2026-04-25 \
  --journey-type 1 --sort-type 3
```

<details>
<summary><strong>All flight search options</strong></summary>

| Flag | Description |
|------|-------------|
| `--origin` | Departure city or airport **(required)** |
| `--destination` | Arrival city or airport |
| `--dep-date` | Departure date (`YYYY-MM-DD`) |
| `--dep-date-start` / `--dep-date-end` | Departure date range |
| `--back-date` | Return date |
| `--back-date-start` / `--back-date-end` | Return date range |
| `--journey-type` | `1` = direct, `2` = connecting |
| `--seat-class-name` | Cabin class name |
| `--transport-no` | Flight number |
| `--transfer-city` | Layover city |
| `--dep-hour-start` / `--dep-hour-end` | Departure hour range |
| `--arr-hour-start` / `--arr-hour-end` | Arrival hour range |
| `--total-duration-hour` | Max flight duration (hours) |
| `--max-price` | Price ceiling |
| `--sort-type` | `1` price desc · `2` recommended · `3` price asc · `4` duration asc · `5` duration desc · `6` depart early · `7` depart late · `8` direct first |

</details>

### `search-hotel` — Hotel Comparison

Search by destination with filters for star rating, bed type, price range, and nearby POIs.

**OpenClaw / Claude Code:**

```
/flyai search-hotel --dest-name "Hangzhou" --poi-name "West Lake" --check-in-date 2026-04-10 --check-out-date 2026-04-12
```

**CLI:**

```bash
# Hotels near West Lake, Hangzhou
flyai search-hotel \
  --dest-name "Hangzhou" --poi-name "West Lake" \
  --check-in-date 2026-04-10 --check-out-date 2026-04-12

# 4-5 star hotels in Sanya under ¥800, sorted by rating
flyai search-hotel \
  --dest-name "Sanya" --hotel-stars "4,5" \
  --sort rate_desc --max-price 800
```

<details>
<summary><strong>All hotel search options</strong></summary>

| Flag | Description |
|------|-------------|
| `--dest-name` | Destination (country/province/city/district) **(required)** |
| `--key-words` | Search keywords |
| `--poi-name` | Nearby attraction name |
| `--hotel-types` | `酒店` (hotel) · `民宿` (homestay) · `客栈` (inn) |
| `--sort` | `distance_asc` · `rate_desc` · `price_asc` · `price_desc` · `no_rank` |
| `--check-in-date` | Check-in date (`YYYY-MM-DD`) |
| `--check-out-date` | Check-out date (`YYYY-MM-DD`) |
| `--hotel-stars` | Star rating, comma-separated (`1`–`5`) |
| `--hotel-bed-types` | `大床房` (king) · `双床房` (twin) · `多床房` (multi) |
| `--max-price` | Max price per night (CNY) |

</details>

### `search-poi` — Attractions & Activities

Find attractions by city, category, or level — from AAAAA scenic spots to local surf schools.

**OpenClaw / Claude Code:**

```
/flyai search-poi --city-name "Xi'an" --category "历史古迹"
```

**CLI:**

```bash
# Historical sites in Xi'an
flyai search-poi --city-name "Xi'an" --category "历史古迹"

# Top-rated attractions in Beijing
flyai search-poi --city-name "Beijing" --poi-level 5

# Lakes and gardens in Hangzhou
flyai search-poi --city-name "Hangzhou" --keyword "West Lake" --category "山湖田园"
```

<details>
<summary><strong>All POI search options</strong></summary>

| Flag | Description |
|------|-------------|
| `--city-name` | City name **(required)** |
| `--keyword` | Attraction name keyword |
| `--poi-level` | Attraction level (`1`–`5`) |
| `--category` | Single category from: 自然风光 · 山湖田园 · 森林丛林 · 峡谷瀑布 · 沙滩海岛 · 沙漠草原 · 人文古迹 · 古镇古村 · 历史古迹 · 园林花园 · 宗教场所 · 主题乐园 · 水上乐园 · 影视基地 · 动物园 · 植物园 · 海洋馆 · 体育场馆 · 演出赛事 · 剧院剧场 · 博物馆 · 纪念馆 · 展览馆 · 地标建筑 · 市集 · 文创街区 · 城市观光 · 滑雪 · 漂流 · 冲浪 · 潜水 · 露营 · 温泉 |

</details>

## Featured Use Cases

### Weekend Getaway Planning

> "Find me a weekend trip from Shanghai — cheap flights, a nice hotel near the beach, and some fun things to do"

FlyAI chains `search-flight`, `search-hotel`, and `search-poi` to give you a complete trip plan with prices and booking links.

### Budget Flight Hunting

> "What's the cheapest direct flight from Beijing to Bangkok in May?"

```
/flyai search-flight --origin "Beijing" --destination "Bangkok" --dep-date-start 2026-05-01 --dep-date-end 2026-05-31 --journey-type 1 --sort-type 3
```

### Group Trip Coordination

> "Compare 4-star hotels in Sanya with twin beds for under ¥500/night, sorted by rating"

```
/flyai search-hotel --dest-name "Sanya" --hotel-stars 4 --hotel-bed-types "双床房" --max-price 500 --sort rate_desc
```

### Local Exploration

> "What are the top nature attractions in Guilin?"

```
/flyai search-poi --city-name "Guilin" --category "自然风光" --poi-level 5
```

## Examples

### OpenClaw

Just type naturally in OpenClaw — FlyAI activates automatically on travel queries:

> Find me direct flights from Beijing to Shanghai next Friday under ¥600

> Compare 5-star hotels near the Bund in Shanghai for this weekend

> What are the top attractions in Chengdu? I'm interested in nature and history

Or use the slash command directly:

```
/flyai search-flight --origin "Beijing" --destination "Shanghai" --dep-date 2026-04-25 --max-price 600
```

### Claude Code

Ask naturally or use the `/flyai` slash command inside Claude Code:

> I'm planning a 5-day trip to Japan — search for visa info, flights from Shanghai, and hotels in Tokyo

> Find concerts and live events happening in Hangzhou

```
/flyai keyword-search --query "5-day Japan trip from Shanghai"
/flyai search-hotel --dest-name "Tokyo" --check-in-date 2026-05-01 --check-out-date 2026-05-06
```

## How It Works

```
You ask your agent ──→ FlyAI Skill activates ──→ flyai-cli runs ──→ Fliggy MCP API
                                                                         │
You see rich results ←── Agent formats markdown ←── JSON response ←──────┘
```

- **Runtime**: Node.js
- **Output**: Single-line JSON to `stdout`, errors/hints to `stderr`
- **Context isolation**: Each command runs in its own execution context
- **Pattern matching**: Intent-based activation at priority 90 — the agent automatically routes travel queries to FlyAI

## Travel Scenarios Covered

FlyAI isn't just for flights and hotels. It spans the full travel lifecycle:

| Category | Examples |
|----------|---------|
| **Transport** | Flights, airport transfers, car rentals, chartered cars |
| **Accommodation** | Hotels, homestays, inns, hotel+flight bundles |
| **Experiences** | Attraction tickets, day tours, guided tours, curated trips |
| **Events** | Concerts, sports events, performing arts, anime events |
| **Services** | Visas, travel insurance, SIM cards, WiFi rental |
| **Trips** | Cruises, weekend getaways, honeymoons, family vacations, study tours |

## License

[MIT](LICENSE) — Copyright (c) 2026 alibaba-flyai
