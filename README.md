# ClawHub Stats Tracker — 查看 Skill 运营数据

> 一句话查看已发布 Skill 的 Stars、Downloads、Installs、版本号和发布时间。

[![ClawHub](https://img.shields.io/badge/ClawHub-clawhub--stats--tracker-blue)](https://clawhub.ai/fangshan101-coder/clawhub-stats-tracker)
[![Version](https://img.shields.io/badge/version-1.0.0-green)](https://clawhub.ai/fangshan101-coder/clawhub-stats-tracker)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## Why

发布了多个 ClawHub Skill 后，想看数据得一个个去网页查。

**Stats Tracker 让你在 Claude Code 里一句话查看所有 Skill 的运营数据。**

- 单个查询、批量查询、按系列筛选
- 无需登录 ClawHub，inspect 接口公开可用
- 自带采集脚本，支持终端直接运行

## 安装

```bash
npx clawhub@latest install fangshan101-coder/clawhub-stats-tracker
```

## 快速开始

```
"查看我的 clawhub skill 数据"
"horoscope-daily 的安装量是多少"
"所有 fortune-telling 系列的数据"
```

## 输出示例

**批量表格：**

```
SLUG                         STARS  DOWNLOADS  INSTALLS  VERSION  PUBLISHED
horoscope-daily                  0         42         0    2.2.0  2026-03-22
life-query                       1        116         0    2.0.0  2026-03-21
art-of-questioning               0          0         0    1.1.0  2026-03-26
```

**单 Skill 详情：**

```
📊 horoscope-daily (v2.2.0)
├── ⭐ Stars: 0
├── 📥 Downloads: 42
├── 📦 Installs: 0
├── 📅 First Published: 2026-03-18
├── 📅 Latest Version: 2026-03-22
└── 📝 Changelog: v2.2.0: Add Language & Localization...
```

## 配置

跟踪列表存放在 `~/.clawhub/tracked-skills.json`：

```json
{
  "skills": [
    { "slug": "horoscope-daily", "note": "星座运势" },
    { "slug": "life-query", "note": "生活查询助手" }
  ]
}
```

发布新 Skill 后，在 `skills` 数组中追加一条即可。

## 采集脚本

也可以在终端直接运行批量采集：

```bash
bash scripts/fetch-stats.sh
```

脚本读取 `~/.clawhub/tracked-skills.json`，逐个调用 `npx clawhub@latest inspect --json`，输出格式化表格。

## 已知限制

- ClawHub CLI 不支持按用户查询所有 Skill，需手动维护跟踪列表
- Downloads/Installs 指标有已知 bug（[openclaw/clawhub#156](https://github.com/openclaw/clawhub/issues/156)）

## 不适用场景

- 发布 Skill（使用 `clawhub publish`）
- 搜索新 Skill（使用 `clawhub search`）
- 安装 Skill（使用 `clawhub install`）

## 兼容性

- Claude Code (CLI)

## License

MIT
