# 构建文档
mdbook build

# 运行服务器

## macOS / Linux
```bash
mdbook serve --open
```

## Windows
```bash
.\mdbook.exe serve --open
```

## 安装 mdBook

**重要**：本项目使用支持中文搜索的 mdBook 版本（[Sunshine40/mdBook](https://github.com/Sunshine40/mdBook)）。

### 安装支持中文搜索的版本（推荐）

```bash
# 确保 Rust 和 Cargo 已安装并更新到最新版本
rustup update stable

# 安装支持非英语搜索的 mdBook 版本
cargo install --git https://github.com/Sunshine40/mdBook --branch search-non-english mdbook

# 验证安装
mdbook --version
```

### 其他安装方式

#### macOS
```bash
# 如果之前通过 Homebrew 安装，需要先卸载
brew uninstall mdbook

# 然后使用 cargo 安装支持中文搜索的版本
cargo install --git https://github.com/Sunshine40/mdBook --branch search-non-english mdbook
```

#### Linux
```bash
# 使用 cargo 安装
cargo install --git https://github.com/Sunshine40/mdBook --branch search-non-english mdbook
```

#### Windows
```bash
# 使用 cargo 安装
cargo install --git https://github.com/Sunshine40/mdBook --branch search-non-english mdbook
```

### 注意事项

- 如果编译失败，请确保 Rust 版本 >= 1.82.0（推荐使用最新稳定版）
- 安装后，mdbook 可执行文件位于 `~/.cargo/bin/mdbook`
- 确保 `~/.cargo/bin` 在您的 PATH 环境变量中