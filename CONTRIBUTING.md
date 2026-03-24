# 贡献指南

感谢你考虑为 FlyAI Skill 项目做出贡献！🎉

## 📝 如何贡献

### 报告 Bug

如果你发现了 Bug，请创建一个 Issue 并包含以下信息:

1. **清晰的标题**: 简要描述问题
2. **复现步骤**: 详细说明如何复现问题
3. **期望行为**: 描述你认为应该发生什么
4. **实际行为**: 描述实际发生了什么
5. **环境信息**: 
   - Node.js 版本
   - flyai-cli 版本
   - 操作系统

示例:

```markdown
### 描述
搜索酒店时，价格筛选参数不生效

### 复现步骤
1. 运行 `flyai search-hotels --dest-name "杭州" --max-price 500`
2. 返回结果中包含价格超过 500 的酒店

### 期望行为
只返回价格在 500 元以下的酒店

### 实际行为
返回了价格为 618 元的酒店

### 环境
- Node.js: v18.16.0
- flyai-cli: v1.0.10
- macOS: 13.4
```

### 提出新功能建议

欢迎提出新功能建议！请创建 Issue 并说明:

1. **功能描述**: 清晰描述你想要的功能
2. **使用场景**: 说明这个功能的使用场景
3. **实现建议**: 如果有实现思路，可以分享
4. **替代方案**: 是否考虑过其他解决方案

### 提交代码

#### 1. Fork 仓库

点击 GitHub 页面右上角的 "Fork" 按钮

#### 2. 克隆仓库

```bash
git clone https://github.com/YOUR_USERNAME/flyai-skill.git
cd flyai-skill
```

#### 3. 创建分支

```bash
# 特性开发
git checkout -b feature/your-feature-name

# Bug 修复
git checkout -b fix/bug-fix-description

# 文档改进
git checkout -b docs/documentation-improvement
```

分支命名规范:
- `feature/*`: 新功能
- `fix/*`: Bug 修复
- `docs/*`: 文档更新
- `refactor/*`: 代码重构
- `test/*`: 测试相关
- `chore/*`: 构建/工具相关

#### 4. 进行修改

确保你的修改:
- ✅ 遵循现有代码风格
- ✅ 添加必要的注释
- ✅ 更新相关文档
- ✅ 通过所有测试 (如有)

#### 5. 提交更改

```bash
git add .
git commit -m "feat: add new hotel filter option"
```

Commit message 规范 ([Conventional Commits](https://www.conventionalcommits.org/)):

- `feat`: 新功能
- `fix`: Bug 修复
- `docs`: 文档更新
- `style`: 代码格式调整 (不影响功能)
- `refactor`: 代码重构 (不新增功能也不修复 Bug)
- `test`: 测试相关
- `chore`: 构建过程或辅助工具变动

#### 6. 推送分支

```bash
git push origin feature/your-feature-name
```

#### 7. 创建 Pull Request

1. 访问你的 fork 仓库
2. 点击 "Compare & pull request"
3. 填写 PR 描述:
   - **标题**: 简洁明了
   - **描述**: 说明改动内容、原因、影响范围
   - **关联 Issue**: 如 `Closes #123`
4. 等待 Code Review

## 🔍 Code Review 标准

PR 需要满足以下要求才能被合并:

- [ ] 代码符合项目风格规范
- [ ] 添加了必要的单元测试 (如适用)
- [ ] 更新了相关文档
- [ ] Commit message 规范
- [ ] 没有引入新的警告或错误
- [ ] 通过了 CI 检查 (如配置)

## 📚 开发环境搭建

### 前置要求

- Node.js >= 16.0.0
- npm >= 8.0.0
- Git

### 安装依赖

```bash
npm install
```

### 本地测试

```bash
# 测试 CLI 命令
npm run test

# 构建项目
npm run build

# 链接到全局 (可选)
npm link
```

## 🙏 感谢

感谢所有为这个项目做出贡献的人!

---

如有疑问，欢迎在 Issue 中提问或联系维护者。
