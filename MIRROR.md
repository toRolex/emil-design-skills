# 镜像维护

本仓库是独立的个人镜像，不是 GitHub fork。上游为 [emilkowalski/skills](https://github.com/emilkowalski/skills)。

## 分支与远端

- `upstream` 分支：完整保留上游默认分支历史与文件，不加入镜像改动。
- `main` 分支：基于 `upstream`，增加中文导读、README 译文及本维护说明。
- `origin`：`https://github.com/toRolex/emil-design-skills.git`
- `upstream`：`https://github.com/emilkowalski/skills.git`（当前默认分支为 `main`）。

`skills/`、`.pl`、`performance-cheatsheet.md` 等上游文件保持原样。英文 README 完整存于 `README.en.md`。

## 同步方法

始终**先更新并推送 `upstream` 分支，再合并进 `main`**。以下命令用于普通 Git 工作流；若本地已接入 jj，则用对应的 fetch、bookmark 与 merge 操作，避免混用修改历史的工具。

```bash
git fetch upstream
git switch upstream
git merge --ff-only upstream/main
git push origin upstream

git switch main
git merge upstream
```

合并时，`README.md` 冲突必须手动处理：

1. 保留顶部中文导读，按实际新增或变更的技能修订。
2. 将最新上游 README 原文完整写入 `README.en.md`。
3. 更新下半部分中文译文，保留上游结构、链接与作者归属。
4. 不修改 `skills/` 或其他上游文件；确认它们与更新后的 `upstream` 分支一致。

解决冲突后再提交与推送：

```bash
git add README.md README.en.md MIRROR.md
git commit -m "docs: sync upstream README translation"
git push origin main
```

若合并无需产生额外翻译提交，不必重复创建空提交。上游默认分支改名时，先确认新分支名，再调整同步命令。

## 发布前检查

```bash
git diff --name-status upstream main
git show upstream:README.md | cmp - README.en.md
git ls-remote origin refs/heads/main refs/heads/upstream
```

与 `upstream` 的文件差异应仅包含 `README.md`、`README.en.md` 和 `MIRROR.md`。首次安装验证或同步后复验：

```bash
npx skills@latest add toRolex/emil-design-skills
```
