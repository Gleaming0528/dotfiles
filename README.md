# dotfiles

使用 [chezmoi](https://www.chezmoi.io/) 管理的个人配置文件。

## 管理的文件

| 文件 | 说明 |
|------|------|
| `~/.zshrc` | Zsh 配置（oh-my-zsh + starship） |
| `~/.vimrc` | Vim 基础配置 |
| `~/.config/starship.toml` | Starship 提示符配置 |
| `~/.config/ghostty/config` | Ghostty 终端配置 |
| `~/.ssh/config` | SSH 连接配置 |

> `.gitconfig` 不纳入管理，新机器手动执行：
> ```bash
> git config --global user.name "gleaming"
> git config --global user.email "xxx@xxx.com"
> ```

## 新机器恢复

```bash
# 1. 安装 chezmoi
brew install chezmoi

# 2. 拉取并预览差异
chezmoi init git@github.com:Gleaming0528/dotfiles.git
chezmoi diff

# 3. 确认无误后应用
chezmoi apply
```

一步到位：

```bash
brew install chezmoi && chezmoi init --apply git@github.com:Gleaming0528/dotfiles.git
```

## 日常使用

```bash
# 修改配置后，同步到 chezmoi 仓库
dot re-add

# 预览仓库与本地的差异
dot diff

# 一键同步并推送到 GitHub
dotpush

# 从 GitHub 拉取最新配置并应用
dot update

# 只拉取不应用
dot git pull
dot diff
dot apply
```

## 多机器冲突处理

```bash
# pull 遇到分歧时，用 rebase 合并
dot git -- pull --rebase

# 确定要用远端覆盖本地仓库
dot git -- reset --hard origin/main

# 确定要用本地覆盖远端
dot re-add
dotpush
```

## 别名

已在 `.zshrc` 中配置：

```bash
dot        # chezmoi 的缩写
dotpush    # 一键 re-add + commit + push
```
