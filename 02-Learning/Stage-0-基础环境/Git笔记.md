# 📚 Git 基础与仓库初始化

> 记录 AI-OS 知识库的 Git 初始化全过程

---

## 📋 元信息

| 属性 | 内容 |
|------|------|
| **学习日期** | 2026-06-08 |
| **知识分类** | Git |
| **来源** | 实践操作 |
| **掌握程度** | 熟悉 |

---

## 🎯 核心概念

### 是什么
Git 是一个分布式版本控制系统，用于跟踪代码变更、协作开发和版本管理。

### 为什么重要
- 代码备份：防止丢失
- 版本回溯：随时回到任意历史版本
- 协作开发：多人同时工作不冲突
- 知识库同步：本地 ↔ GitHub 双向备份

### 适用场景
- 个人项目备份
- 多人协作开发
- 开源项目贡献（Fork → PR 工作流）

---

## 📖 详细内容

### 1. Git 环境检查

```bash
# 查看 Git 版本
git --version

# 查看当前配置
git config --global user.name
git config --global user.email
```

### 2. 配置 Git 身份

```bash
# 设置全局用户名和邮箱（会出现在每次提交记录中）
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱"

# 设置默认分支名为 main（推荐）
git config --global init.defaultBranch main
```

### 3. 初始化仓库

```bash
# 在当前目录初始化 Git 仓库
git init

# 重命名分支为 main
git branch -m main
```

### 4. 配置 .gitignore

忽略不需要跟踪的文件：

```gitignore
# Obsidian
.obsidian/workspace.json
.obsidian/graph.json

# OS
.DS_Store

# Temp files
09-Assets/Temp/*

# IDE
.vscode/
.idea/

# Logs
*.log
```

### 5. 添加文件并提交

```bash
# 添加所有变更到暂存区
git add -A

# 提交（写好提交信息很重要）
git commit -m "feat: 初始化 AI-OS 全栈学习知识库骨架

- 创建完整的 10 大模块目录结构
- 添加 4 阶段学习路径"
```

**提交信息规范**：
- `feat:` 新功能
- `fix:` 修复 Bug
- `docs:` 文档更新
- `refactor:` 重构

### 6. 推送到 GitHub

**方式一：GitHub CLI（推荐）**

```bash
# 一键创建仓库并推送
gh repo create AI-OS-Learning --public --source=. --remote=origin --push
```

参数说明：
| 参数 | 含义 |
|------|------|
| `--public` | 公开仓库 |
| `--source=.` | 当前目录作为源码 |
| `--remote=origin` | 远程地址命名为 origin |
| `--push` | 自动推送 |

**方式二：网页创建 + git 命令**

```bash
# 1. 在 github.com/new 创建空仓库
# 2. 添加远程地址
git remote add origin git@github.com:用户名/仓库名.git

# 3. 推送
git push -u origin main
```

---

## 🔗 关联知识

- [环境配置清单](./环境配置清单.md)
- [GitHub SSH 配置](https://docs.github.com/cn/authentication/connecting-to-github-with-ssh)

---

## 💡 个人理解

- Git 对知识库同样重要：Markdown 文件也是代码，需要版本管理
- 好的提交信息 = 未来的自己感谢现在的自己
- `.gitignore` 是安全防线：防止敏感文件意外上传
- 每次学习完一个知识点就 `git commit`，养成小步提交的习惯

---

## ❓ 遗留问题

- [ ] 学习 Git 分支管理（branch、merge、rebase）
- [ ] 了解 GitHub Pull Request 工作流
- [ ] 学习如何处理合并冲突

---

## 📎 参考资源

1. [Git 官方文档](https://git-scm.com/doc)
2. [GitHub Docs](https://docs.github.com/)
3. [learngitbranching.js.org](https://learngitbranching.js.org/?locale=zh_CN)（交互式学习）
