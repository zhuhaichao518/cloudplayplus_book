# 安装指南

本指南将详细介绍如何在各种平台上安装和配置 CloudPlayPlus。

## 桌面平台安装

### Windows 安装

#### 方法 1: 安装程序（推荐）
1. 下载 Windows 安装程序 (.exe)
2. 以管理员身份运行安装程序
3. 选择安装目录和组件
4. 完成安装并重启系统

#### 方法 2: 便携版本
1. 下载便携版本 (.zip)
2. 解压到任意目录
3. 运行 `cloudplayplus.exe`

#### 系统要求
- Windows 10 版本 1903 或更高
- .NET Framework 4.7.2+
- DirectX 11 兼容显卡

### macOS 安装

#### 方法 1: DMG 安装包
1. 下载 .dmg 文件
2. 双击挂载 DMG 镜像
3. 将 CloudPlayPlus 拖拽到 Applications 文件夹
4. 从启动台或 Applications 文件夹启动

#### 方法 2: Homebrew 安装
```bash
brew install --cask cloudplayplus
```

#### 系统要求
- macOS 10.14 (Mojave) 或更高
- 支持 Metal 的显卡
- 至少 4GB 可用内存

### Linux 安装

#### Ubuntu/Debian
```bash
# 添加 PPA 仓库
sudo add-apt-repository ppa:cloudplayplus/stable
sudo apt update

# 安装 CloudPlayPlus
sudo apt install cloudplayplus
```

#### Fedora/RHEL/CentOS
```bash
# 启用 COPR 仓库
sudo dnf copr enable cloudplayplus/stable

# 安装 CloudPlayPlus
sudo dnf install cloudplayplus
```

#### Arch Linux
```bash
# 从 AUR 安装
yay -S cloudplayplus
```

#### 系统要求
- Linux 内核 4.18+
- GTK 3.20+ 或 Qt 5.12+
- OpenGL 3.3 兼容显卡

## 移动平台安装

### Android 安装

#### Google Play Store
1. 在 Google Play Store 中搜索 "CloudPlayPlus"
2. 点击安装
3. 等待下载和安装完成

#### APK 文件安装
1. 下载 APK 文件
2. 启用"未知来源"应用安装
3. 使用文件管理器打开 APK 文件
4. 按照提示完成安装

#### 系统要求
- Android 6.0 (API 23) 或更高
- 至少 2GB RAM
- 支持 OpenGL ES 3.0 的 GPU

### iOS 安装

#### App Store
1. 在 App Store 中搜索 "CloudPlayPlus"
2. 点击获取并安装
3. 使用 Apple ID 验证下载

#### 系统要求
- iOS 12.0 或更高
- iPhone 6s 或更新机型
- iPad Air 2 或更新机型

## Web 版本

### 浏览器要求
- **Chrome**: 版本 80+
- **Firefox**: 版本 75+
- **Safari**: 版本 13+
- **Edge**: 版本 80+

### 访问方式
直接在浏览器中访问：`https://cloudplayplus.com`

## 依赖项安装

### Flutter 环境
```bash
# 安装 Flutter SDK
git clone https://github.com/flutter/flutter.git
export PATH="$PATH:`pwd`/flutter/bin"

# 验证安装
flutter doctor
```

### WebRTC 依赖
```bash
# Ubuntu/Debian
sudo apt install libwebrtc-dev

# macOS
brew install webrtc

# Windows
# 使用预编译的二进制文件
```

### 游戏控制器支持
```bash
# Linux
sudo apt install libsdl2-dev libsdl2-2.0-0

# macOS
brew install sdl2

# Windows
# 包含在安装包中
```

## 初始配置

### 首次启动设置
1. **语言选择**: 选择界面语言
2. **主题设置**: 选择深色或浅色主题
3. **权限授予**: 授予必要的系统权限
4. **账户设置**: 配置用户账户和偏好

### 网络配置
```yaml
# 配置文件示例
network:
  streaming:
    port: 8080
    protocol: "webrtc"
    stun_servers:
      - "stun:stun.l.google.com:19302"
      - "stun:stun1.l.google.com:19302"
```

### 输入设备配置
```yaml
# 游戏手柄配置
gamepad:
  deadzone: 0.1
  sensitivity: 1.0
  rumble_enabled: true
  
# 键盘配置
keyboard:
  repeat_delay: 500
  repeat_rate: 30
```

## 验证安装

### 功能测试
1. **应用启动**: 确认应用正常启动
2. **设备检测**: 测试输入设备识别
3. **网络连接**: 验证网络连接和流媒体
4. **性能测试**: 检查帧率和延迟

### 诊断命令
```bash
# 检查系统信息
flutter doctor -v

# 检查 WebRTC 支持
flutter run --web-renderer html

# 检查设备连接
flutter devices
```

## 故障排除

### 常见安装问题

#### 权限错误
```bash
# Linux 解决方案
sudo chmod +x /usr/local/bin/cloudplayplus
sudo chown $USER:$USER ~/.config/cloudplayplus
```

#### 依赖缺失
```bash
# 安装缺失的依赖
sudo apt install --fix-broken
flutter doctor --android-licenses
```

#### 网络问题
- 检查防火墙设置
- 验证代理配置
- 测试网络连接

### 获取帮助
- 查看 [故障排除](./troubleshooting.md) 章节
- 在 GitHub 上提交 issue
- 联系技术支持团队

## 下一步

安装完成后，您可以：
- [快速开始](./getting_started.md) - 了解基本使用方法
- [用户指南](./user_guide.md) - 深入学习各项功能
- [配置参考](./configuration.md) - 详细配置选项说明
