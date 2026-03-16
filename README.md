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

## 新机器恢复

```bash
# 1. 安装 chezmoi
brew install chezmoi

# 2. 拉取并预览差异
chezmoi init Gleaming0528
chezmoi diff

# 3. 确认无误后应用
chezmoi apply
```

一步到位：

```bash
brew install chezmoi && chezmoi init --apply Gleaming0528
```

## 日常使用

```bash
# 查看哪些文件被管理
chezmoi managed

# 修改配置后，同步到仓库
chezmoi re-add

# 预览差异
chezmoi diff

# 一键同步并推送到 GitHub
dotpush
```

## 别名

已在 `.zshrc` 中配置：

```bash
dot        # chezmoi 的缩写
dotpush    # 一键 re-add + commit + push
```
