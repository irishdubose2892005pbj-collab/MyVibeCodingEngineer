# 📚 GitHub 仓库链接与代码推送

> 将本地 Git 仓库连接到 GitHub 远程并完成首次推送的完整流程

---

## 📋 元信息

| 属性 | 内容 |
|------|------|
| **学习日期** | 2026-06-08 |
| **知识分类** | Git |
| **来源** | 实践操作 |
| **原文链接** | [GitHub Docs - Pushing commits](https://docs.github.com/cn/get-started/using-git/pushing-commits-to-a-remote-repository) |
| **掌握程度** | 熟悉 |

---

## 🎯 核心概念

### 是什么
GitHub 是远程代码托管平台，本地仓库通过 `remote` 与其建立链接，通过 `push` 将本地提交同步到远程。

### 为什么重要
- **云端备份**：本地文件丢失也不怕
- **多端同步**：公司、家里、笔记本随时获取最新代码
- **协作基础**：多人开发、代码审查、开源贡献的前提
- **展示作品**：GitHub 是技术人的名片

### 适用场景
- 新建项目首次推送到 GitHub
- 已有项目关联新的远程仓库
- 日常开发同步代码到云端

---

## 📖 详细内容

### 1. 确认 GitHub CLI 登录状态

```bash
# 检查是否已登录 GitHub
gh auth status
```

**已登录输出示例**：
```
github.com
  ✓ Logged in to github.com as irishdubose2892005pbj-collab
```

**未登录时执行**：
```bash
gh auth login
```

按提示选择：
- `GitHub.com` → `SSH` → `Y`（生成 SSH Key）→ `Login with a web browser` → 浏览器授权

---

### 2. 一键创建仓库并推送（GitHub CLI）

```bash
gh repo create AI-OS-Learning --public --source=. --remote=origin --push
```

| 参数 | 作用 |
|------|------|
| `AI-OS-Learning` | 仓库名称，**可自定义** |
| `--public` | 公开仓库（或用 `--private`） |
| `--source=.` | 当前目录作为源码 |
| `--remote=origin` | 远程地址命名为 origin |
| `--push` | 自动推送本地提交 |

**成功输出**：
```
✓ Created repository irishdubose2892005pbj-collab/AI-OS-Learning on GitHub
✓ Added remote git@github.com:irishdubose2892005pbj-collab/AI-OS-Learning.git
✓ Pushed commits to git@github.com:irishdubose2892005pbj-collab/AI-OS-Learning.git
```

**验证**：浏览器访问 `https://github.com/irishdubose2892005pbj-collab/AI-OS-Learning`

---

### 3. 手动方式（网页创建 + git 命令）

如果不用 GitHub CLI，可以分步操作：

**步骤 A：在 GitHub 创建空仓库**

1. 浏览器打开 https://github.com/new
2. Repository name: `AI-OS-Learning`
3. 选择 **Public**
4. **不要勾选** "Initialize this repository with a README"
5. 点击 **Create repository**

**步骤 B：关联远程并推送**

```bash
# 添加远程仓库地址
git remote add origin git@github.com:irishdubose2892005pbj-collab/AI-OS-Learning.git

# 设置分支名
git branch -M main

# 首次推送（-u 设置上游分支，以后直接用 git push）
git push -u origin main
```

---

### 4. 日常推送 workflow

仓库创建完成后，后续更新只需三步：

```bash
git add -A                    # 1. 添加所有变更到暂存区
git commit -m "描述"          # 2. 提交（写好描述！）
git push                      # 3. 推送到 GitHub
```

---

### 5. 常用远程操作命令

| 命令 | 作用 |
|------|------|
| `git remote -v` | 查看已配置的远程地址 |
| `git remote remove origin` | 删除名为 origin 的远程 |
| `git remote set-url origin 新地址` | 修改远程地址 |
| `git pull` | 从远程拉取最新代码并合并 |
| `git fetch` | 下载远程更新但不合并 |

---

## 🔗 关联知识

- [Git笔记](./Git笔记.md) — Git 仓库初始化完整流程
- [Git核心命令速查](./Git核心命令速查.md) — clone/add/commit/push/pull/branch 详解
- [学习任务](学习任务.md) — Stage-0 全部任务清单

---

## 💡 个人理解

- `origin` 只是远程仓库的别名，可以叫任何名字，但 `origin` 是约定俗成的标准
- 第一次推送用 `git push -u origin main`，之后直接用 `git push` 即可
- `--public` 和 `--private` 的区别：公开仓库所有人可见（适合开源/展示），私密仓库仅自己可见（适合商业项目）
- 提交信息是未来自己的救命稻草，花 10 秒写清楚的描述，未来省 10 分钟翻代码
- 知识库也要 `git push`，Markdown 文件和代码一样需要版本管理

---

## ❓ 遗留问题

- [ ] 学习 Git 多人协作工作流（Fork → PR → Code Review → Merge）
- [ ] 了解 GitHub Actions 自动化（CI/CD）
- [ ] 学习如何处理 `git push` 时的冲突

---

## 📎 参考资源

1. [GitHub Docs - 远程仓库](https://docs.github.com/cn/get-started/getting-started-with-git/about-remote-repositories)
2. [GitHub CLI 官方文档](https://cli.github.com/manual/)
3. [learngitbranching.js.org](https://learngitbranching.js.org/?locale=zh_CN) — 交互式 Git 学习
