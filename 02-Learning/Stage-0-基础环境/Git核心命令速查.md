# 📘 Git 核心命令速查

> Git 日常操作的最常用命令，即查即用

---

## 📋 元信息

| 属性 | 内容 |
|------|------|
| **学习日期** | 2026-06-08 |
| **知识分类** | Git |
| **来源** | 实践总结 |
| **关联笔记** | [Git笔记](./Git笔记.md) |

---

## 🚀 快速开始（日常 workflow）

```bash
# 1. 获取远程最新代码
git pull

# 2. 查看当前变更
git status

# 3. 添加文件到暂存区
git add 文件名          # 添加指定文件
git add -A              # 添加所有变更

# 4. 提交变更
git commit -m "描述"

# 5. 推送到远程
git push
```

---

## 📖 六大核心命令详解

### 1. `git clone` — 克隆仓库

从远程下载完整仓库到本地：

```bash
# SSH 方式（推荐，已配置密钥后）
git clone git@github.com:用户名/仓库名.git

# HTTPS 方式
git clone https://github.com/用户名/仓库名.git

# 克隆到指定目录
git clone git@github.com:用户名/仓库名.git 我的目录名
```

**场景**：第一次获取项目代码，或在新电脑上开始工作。

---

### 2. `git add` — 添加文件到暂存区

```bash
git add 文件名              # 添加单个文件
git add 文件夹/             # 添加整个文件夹
git add *.js                # 添加所有 js 文件
git add -A                  # 添加所有变更（新增、修改、删除）
git add .                   # 添加当前目录所有变更（不含删除）
```

**场景**：修改完代码后，选择要提交的文件。

💡 **技巧**：`git add -A` 最常用，一步到位。

---

### 3. `git commit` — 提交变更

```bash
# 基础提交
git commit -m "提交描述"

# 多行提交信息
git commit -m "标题" -m "详细描述"

# 添加并一起提交（跳过 git add）
git commit -am "描述"

# 修改最后一次提交
git commit --amend -m "修正后的描述"
```

**提交信息规范**：

| 前缀 | 用途 | 示例 |
|------|------|------|
| `feat:` | 新功能 | `feat: 添加用户登录页面` |
| `fix:` | 修复 Bug | `fix: 修复登录按钮点击无响应` |
| `docs:` | 文档更新 | `docs: 更新 API 接口文档` |
| `style:` | 代码格式 | `style: 统一缩进为 2 空格` |
| `refactor:` | 重构 | `refactor: 优化数据库查询逻辑` |
| `chore:` | 杂项 | `chore: 更新依赖版本` |

**场景**：确认变更内容后，保存一个版本快照。

---

### 4. `git push` — 推送到远程

```bash
git push                    # 推送到默认远程分支
git push origin main        # 推送到 origin 的 main 分支
git push -u origin main     # 首次推送并设置上游分支
```

**场景**：本地提交后，同步到 GitHub/GitLab。

---

### 5. `git pull` — 拉取远程更新

```bash
git pull                    # 拉取并合并当前分支的远程更新
```

**场景**：开始工作前，先获取同事的最新代码。

⚠️ **注意**：如果本地有未提交的修改，pull 可能会冲突。建议先 `git commit` 或 `git stash`。

---

### 6. `git branch` — 分支管理

```bash
# 查看分支
git branch                  # 查看本地分支（* 表示当前分支）
git branch -a               # 查看所有分支（含远程）

# 创建分支
git branch 新分支名          # 创建但不切换
git checkout -b 新分支名     # 创建并切换到新分支
git switch -c 新分支名       # 新版创建并切换（推荐）

# 切换分支
git checkout 分支名          # 旧版
git switch 分支名            # 新版推荐

# 删除分支
git branch -d 分支名         # 删除已合并的分支
git branch -D 分支名         # 强制删除

# 合并分支
git checkout main
git merge 功能分支           # 把功能分支合并到 main
```

**分支工作流**：

```bash
# 日常开发流程
git checkout main           # 切换到主分支
git pull                    # 拉取最新代码
git switch -c feature/xxx   # 创建功能分支
git add -A && git commit -m "feat: xxx"   # 开发和提交
git checkout main           # 切回主分支
git merge feature/xxx       # 合并功能分支
git push                    # 推送
```

---

## 📊 常用辅助命令

| 命令 | 作用 |
|------|------|
| `git status` | 查看当前文件变更状态 |
| `git log --oneline` | 简洁查看提交历史 |
| `git diff` | 查看未暂存的变更内容 |
| `git diff --staged` | 查看已暂存但未提交的变更 |
| `git stash` | 临时保存未提交的修改 |
| `git stash pop` | 恢复最近一次 stash |
| `git remote -v` | 查看远程仓库地址 |

---

## 🔗 关联笔记

- [Git笔记](./Git笔记.md) — Git 仓库初始化完整流程
- [GitHub 官方文档](https://docs.github.com/)
- [learngitbranching.js.org](https://learngitbranching.js.org/?locale=zh_CN)
