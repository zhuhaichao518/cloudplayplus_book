# 故障排除

本故障排除指南将帮助您解决 CloudPlayPlus 使用过程中遇到的常见问题。如果您遇到的问题不在本指南中，请查看获取帮助部分。

## 快速诊断

### 问题分类
- 🔴 **严重问题** - 应用无法启动或核心功能失效
- 🟡 **功能问题** - 部分功能无法正常工作
- 🟢 **性能问题** - 应用运行缓慢或响应延迟
- 🔵 **配置问题** - 设置或配置相关的问题

### 诊断步骤
1. **检查系统要求** - 确认系统满足最低要求
2. **查看错误日志** - 分析错误信息和日志文件
3. **测试基本功能** - 验证核心功能是否正常
4. **检查网络连接** - 确认网络配置和连接状态
5. **更新应用版本** - 安装最新版本和更新

## 应用启动问题

### 应用无法启动

#### 症状
- 双击图标无反应
- 启动后立即崩溃
- 显示错误对话框

#### 解决方案
```bash
# Windows
# 检查系统兼容性
sfc /scannow
dism /online /cleanup-image /restorehealth

# 重新安装应用
# 1. 卸载 CloudPlayPlus
# 2. 清理残留文件
# 3. 重新下载安装

# macOS
# 检查安全设置
系统偏好设置 → 安全性与隐私 → 通用

# 重置应用
rm -rf ~/Library/Application\ Support/CloudPlayPlus
rm -rf ~/Library/Preferences/com.cloudplayplus.app.plist

# Linux
# 检查依赖
ldd /usr/bin/cloudplayplus
sudo apt install --fix-broken

# 检查权限
chmod +x /usr/bin/cloudplayplus
```

#### 常见原因
- 系统不兼容
- 依赖库缺失
- 权限不足
- 配置文件损坏

### 启动缓慢

#### 症状
- 启动时间超过 30 秒
- 启动过程中界面卡顿
- 首次启动特别慢

#### 解决方案
```toml
# 优化启动配置
[app.startup]
check_updates = false
auto_load_plugins = false
preload_resources = false

[performance]
lazy_loading = true
background_initialization = true
```

#### 性能优化
- 关闭不必要的启动项
- 使用 SSD 存储
- 增加系统内存
- 关闭实时保护

## 网络连接问题

### 流媒体连接失败

#### 症状
- 无法连接到流媒体服务
- 连接后立即断开
- 显示网络错误

#### 解决方案
```toml
# 检查网络配置
[streaming.network]
stun_servers = [
    "stun:stun.l.google.com:19302",
    "stun:stun1.l.google.com:19302"
]
connection_timeout = 60000
reconnect_attempts = 5

# 代理设置
[network.proxy]
enabled = true
type = "http"
host = "your-proxy-server"
port = 8080
```

#### 网络诊断
```bash
# 测试网络连接
ping stun.l.google.com
telnet stun.l.google.com 19302

# 检查防火墙
netsh advfirewall firewall show rule name=all | findstr CloudPlayPlus

# 测试端口
netstat -an | findstr 8080
```

### 高延迟问题

#### 症状
- 游戏延迟超过 100ms
- 音视频不同步
- 输入响应缓慢

#### 解决方案
```toml
# 优化网络设置
[streaming.optimization]
latency_target = 30
buffer_size = 500
jitter_buffer = 100
adaptive_bitrate = true

# 选择就近服务器
[streaming.servers]
primary = "server-near-you.cloudplayplus.com"
fallback = "backup-server.cloudplayplus.com"
```

#### 网络优化
- 使用有线网络连接
- 关闭其他网络应用
- 配置 QoS 设置
- 选择就近的服务器

## 设备连接问题

### 游戏手柄无法识别

#### 症状
- 手柄连接后无反应
- 系统无法识别设备
- 按键映射错误

#### 解决方案
```toml
# 检查手柄配置
[input.gamepad]
enabled = true
auto_detect = true
force_detection = false

# 重置按键映射
[input.gamepad.mapping]
# 使用默认映射
a_button = "confirm"
b_button = "cancel"
x_button = "menu"
y_button = "function"
```

#### 系统检查
```bash
# Windows
# 检查设备管理器
devmgmt.msc

# 更新手柄驱动
# 下载最新驱动并安装

# macOS
# 检查系统偏好设置
系统偏好设置 → 游戏控制器

# Linux
# 检查设备文件
ls -la /dev/input/
cat /proc/bus/input/devices

# 安装 SDL2
sudo apt install libsdl2-dev
```

### 键盘输入问题

#### 症状
- 按键无响应
- 重复输入
- 快捷键失效

#### 解决方案
```toml
# 键盘设置
[input.keyboard]
layout = "qwerty"
repeat_delay = 500
repeat_rate = 30
caps_lock_behavior = "normal"

# 重置快捷键
[input.keyboard.shortcuts]
fullscreen = "F11"
screenshot = "F12"
settings = "Ctrl+,"
help = "F1"
```

## 性能问题

### 帧率下降

#### 症状
- 游戏帧率低于 30fps
- 界面卡顿
- 动画不流畅

#### 解决方案
```toml
# 性能优化
[performance]
cpu_priority = "high"
gpu_acceleration = true
hardware_decoding = true

[video.renderer]
vsync = true
triple_buffering = true
frame_limit = 60

# 降低质量设置
[video.quality]
antialiasing = "msaa_2x"
shadow_quality = "medium"
particle_quality = "medium"
```

#### 系统优化
- 关闭后台程序
- 更新显卡驱动
- 增加系统内存
- 使用性能模式

### 内存占用过高

#### 症状
- 应用占用内存超过 2GB
- 系统响应缓慢
- 频繁内存不足警告

#### 解决方案
```toml
# 内存管理
[performance.memory]
limit = 2048
cleanup_interval = 300
garbage_collection = true

# 缓存设置
[performance.caching]
enabled = true
max_size = 512
ttl = 1800
compression = true
```

#### 内存优化
- 重启应用释放内存
- 关闭不必要的标签页
- 减少同时运行的游戏
- 检查内存泄漏

## 音频问题

### 音频无声音

#### 症状
- 游戏没有声音
- 麦克风无法录音
- 音频设备切换失败

#### 解决方案
```toml
# 音频设置
[audio]
enabled = true
sample_rate = 48000
channels = 2

[audio.input]
device = "default"
volume = 100
muted = false

[audio.output]
device = "default"
volume = 80
muted = false
```

#### 音频检查
```bash
# Windows
# 检查音频设备
mmsys.cpl

# 测试音频
# 使用系统音频测试工具

# macOS
# 检查音频设置
系统偏好设置 → 声音

# Linux
# 检查音频设备
pactl list short sinks
pactl list short sources
```

### 音频延迟

#### 症状
- 音视频不同步
- 音频延迟超过 100ms
- 回声或噪音

#### 解决方案
```toml
# 音频优化
[audio.optimization]
buffer_size = 256
latency_target = 20
echo_cancellation = true
noise_reduction = true

[audio.codec]
encoder = "opus"
bitrate = 128
complexity = 3
frame_duration = 10
```

## 视频问题

### 画面模糊

#### 症状
- 游戏画面不清晰
- 文字模糊难读
- 视频质量下降

#### 解决方案
```toml
# 视频质量
[video.quality]
resolution = "1080p"
frame_rate = 60
bitrate = "auto"

[video.encoding]
codec = "h264"
preset = "fast"
crf = 18
max_bitrate = 8000

# 渲染设置
[video.renderer]
backend = "auto"
vsync = true
triple_buffering = true
```

### 画面撕裂

#### 症状
- 画面出现水平撕裂线
- 动画不流畅
- 帧率不稳定

#### 解决方案
```toml
# 渲染优化
[video.renderer]
vsync = true
triple_buffering = true
frame_limit = 60

[performance]
gpu_acceleration = true
hardware_sync = true
```

## 配置问题

### 配置无法保存

#### 症状
- 设置修改后不生效
- 配置重置为默认值
- 配置文件损坏

#### 解决方案
```bash
# 检查配置文件权限
# Windows
icacls "%APPDATA%\CloudPlayPlus" /grant "%USERNAME%":(OI)(CI)F

# macOS/Linux
chmod 755 ~/.config/cloudplayplus
chown $USER:$USER ~/.config/cloudplayplus

# 备份和重置配置
cp config.toml config.toml.backup
rm config.toml
# 重启应用生成新配置
```

### 插件加载失败

#### 症状
- 插件无法启用
- 插件功能异常
- 插件冲突错误

#### 解决方案
```toml
# 插件设置
[plugins]
auto_load = false
sandboxed = true
permissions = ["network", "filesystem"]

# 禁用问题插件
[plugins.disabled]
problematic_plugin = true
```

## 平台特定问题

### Windows 问题

#### 常见问题
- DirectX 错误
- .NET Framework 缺失
- 权限不足

#### 解决方案
```bash
# 安装 DirectX
# 下载 DirectX End-User Runtime

# 安装 .NET Framework
# 下载并安装最新版本

# 以管理员身份运行
# 右键点击图标 → 以管理员身份运行
```

### macOS 问题

#### 常见问题
- 安全设置阻止
- 权限请求失败
- 兼容性问题

#### 解决方案
```bash
# 检查安全设置
系统偏好设置 → 安全性与隐私 → 通用

# 重置权限
tccutil reset All com.cloudplayplus.app

# 检查兼容性
# 确认 macOS 版本支持
```

### Linux 问题

#### 常见问题
- 依赖库缺失
- 权限问题
- 显示服务器兼容性

#### 解决方案
```bash
# 安装依赖
sudo apt install libsdl2-dev libwebrtc-dev

# 检查权限
sudo usermod -a -G input $USER
sudo usermod -a -G video $USER

# 显示服务器
export DISPLAY=:0
export XDG_SESSION_TYPE=x11
```

## 高级故障排除

### 日志分析

#### 启用详细日志
```toml
[logging]
level = "debug"
format = "json"
output = "file"
max_size = 100

[logging.categories]
app = "debug"
network = "debug"
input = "debug"
video = "debug"
audio = "debug"
```

#### 日志位置
- **Windows**: `%APPDATA%\CloudPlayPlus\logs\`
- **macOS**: `~/Library/Logs/CloudPlayPlus/`
- **Linux**: `~/.local/share/cloudplayplus/logs/`

### 性能分析

#### 内置工具
```bash
# 性能监控
cloudplayplus --monitor

# 性能测试
cloudplayplus --benchmark

# 系统信息
cloudplayplus --system-info
```

#### 外部工具
- **Flutter Inspector** - UI 性能分析
- **Dart DevTools** - 内存和性能监控
- **系统监控工具** - 任务管理器、活动监视器等

### 网络诊断

#### 连接测试
```bash
# 测试 STUN 服务器
stunclient stun.l.google.com 19302

# 测试 TURN 服务器
turnclient turn.example.com 3478 username password

# 网络延迟测试
ping -c 10 your-server.com
traceroute your-server.com
```

## 预防措施

### 定期维护
- 定期更新应用和插件
- 清理缓存和临时文件
- 备份重要配置
- 监控系统性能

### 最佳实践
- 使用稳定的网络连接
- 保持系统更新
- 定期重启应用
- 避免同时运行过多程序

### 监控设置
```toml
[monitoring]
enabled = true
interval = 5000
alert_thresholds = {
    cpu_usage = 80,
    memory_usage = 75,
    network_latency = 80,
    frame_drops = 3
}
```

## 获取帮助

### 自助资源
- **在线文档** - 完整的用户手册
- **FAQ 页面** - 常见问题解答
- **视频教程** - 操作演示视频
- **社区论坛** - 用户交流平台

### 技术支持
- **GitHub Issues** - 提交 bug 报告
- **Discord 社区** - 实时技术支持
- **邮件支持** - 技术支持邮箱
- **在线聊天** - 实时客服支持

### 问题报告模板
```markdown
## 问题描述
简要描述遇到的问题

## 环境信息
- 操作系统: [Windows 10/11, macOS, Linux]
- CloudPlayPlus 版本: [版本号]
- 硬件配置: [CPU, 内存, 显卡]

## 重现步骤
1. 步骤 1
2. 步骤 2
3. 步骤 3

## 预期行为
描述期望的正常行为

## 实际行为
描述实际发生的异常行为

## 错误日志
粘贴相关的错误日志

## 附加信息
其他相关信息或截图
```

## 下一步

如果问题仍未解决，请：

1. **收集信息** - 记录错误信息和系统状态
2. **搜索解决方案** - 在文档和社区中搜索
3. **提交问题报告** - 使用模板提交详细报告
4. **联系支持** - 获取专业技术支持

祝您使用愉快！🎮
