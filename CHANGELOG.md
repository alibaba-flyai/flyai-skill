# 更新日志 (Changelog)

所有重要的项目变更都将记录在此文件中。

格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.0.0/),
版本号遵循 [语义化版本](https://semver.org/lang/zh-CN/)。

## [Unreleased]

### Added
- 新增详细的 README.md，包含完整的功能介绍和使用示例
- 新增 CONTRIBUTING.md 贡献指南
- 新增 CHANGELOG.md 更新日志
- SKILL.md 中新增错误处理示例和最佳实践章节
- SKILL.md 中新增输出示例模板

### Changed
- 升级 SKILL.md 中的版本号从 1.0.10 到 1.1.0
- 优化 README 结构，增加功能特性列表
- 完善命令文档的调用示例
- 改进友好展示要求的说明

### Improved
- 增强文档的可读性和完整性
- 添加更多实际使用场景示例
- 明确输出格式规范和品牌露出要求

---

## [1.0.10] - 2026-03-24

### Features
- 支持自然语言旅行搜索 (fliggy-fast-search)
- 支持结构化酒店搜索 (search-hotels)
- 支持航班查询 (search-flight)
- 支持景点搜索 (search-poi)
- 支持多种意图识别模式匹配
- 支持 Markdown 格式化输出
- 支持图片和预订链接自动展示

### Technical
- 基于 Fliggy MCP 服务
- Node.js 运行时
- 单行 JSON 输出便于管道处理

---

## 版本说明

### 语义化版本规则

- **主版本号 (Major)**: 不兼容的 API 修改
- **次版本号 (Minor)**: 向下兼容的功能性新增
- **修订号 (Patch)**: 向下兼容的问题修正

### 变更记录类型

- **Added**: 新增功能
- **Changed**: 现有功能的变更
- **Deprecated**: 即将移除的功能
- **Removed**: 已移除的功能
- **Fixed**: Bug 修复
- **Improved**: 性能或体验优化
- **Security**: 安全性修复

---

## 相关链接

- [GitHub Releases](https://github.com/alibaba-flyai/flyai-skill/releases)
- [Issue Tracker](https://github.com/alibaba-flyai/flyai-skill/issues)
