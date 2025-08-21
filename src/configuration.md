# 配置参考

本配置参考文档详细介绍了 CloudPlayPlus 的所有配置选项，帮助您根据需求进行个性化设置。

## 配置文件结构

CloudPlayPlus 使用 TOML 格式的配置文件，支持多级配置和继承。

### 配置文件位置
- **Windows**: `%APPDATA%\CloudPlayPlus\config.toml`
- **macOS**: `~/Library/Application Support/CloudPlayPlus/config.toml`
- **Linux**: `~/.config/cloudplayplus/config.toml`
- **Android**: `/data/data/com.cloudplayplus.app/files/config.toml`
- **iOS**: `~/Documents/CloudPlayPlus/config.toml`

### 配置文件层次
```
config.toml          # 主配置文件
├── user.toml        # 用户特定配置
├── device.toml      # 设备特定配置
└── profiles/        # 配置配置文件
    ├── gaming.toml  # 游戏配置
    ├── streaming.toml # 流媒体配置
    └── work.toml    # 工作配置
```

## 基础配置

### 应用设置
```toml
[app]
name = "CloudPlayPlus"
version = "1.0.0"
language = "zh-CN"
theme = "dark"
debug = false
log_level = "info"

[app.window]
width = 1280
height = 720
min_width = 800
min_height = 600
resizable = true
fullscreen = false
always_on_top = false

[app.startup]
auto_start = false
minimize_to_tray = true
check_updates = true
```

### 用户设置
```toml
[user]
name = "用户名"
email = "user@example.com"
avatar = "path/to/avatar.png"
timezone = "Asia/Shanghai"
date_format = "YYYY-MM-DD"
time_format = "HH:mm:ss"

[user.preferences]
notifications = true
sound_effects = true
auto_save = true
backup_config = true
```

## 网络配置

### 流媒体设置
```toml
[streaming]
protocol = "webrtc"
quality = "auto"
resolution = "1080p"
frame_rate = 60
bitrate = "auto"
codec = "h264"

[streaming.network]
stun_servers = [
    "stun:stun.l.google.com:19302",
    "stun:stun1.l.google.com:19302"
]
turn_servers = [
    "turn:turn.example.com:3478"
]
ice_candidate_pool_size = 10
connection_timeout = 30000
reconnect_attempts = 3

[streaming.optimization]
adaptive_bitrate = true
buffer_size = 1000
latency_target = 50
jitter_buffer = 200
```

### 代理设置
```toml
[network.proxy]
enabled = false
type = "http"  # http, https, socks5
host = "proxy.example.com"
port = 8080
username = ""
password = ""
bypass_local = true
bypass_addresses = ["127.0.0.1", "localhost"]
```

### 防火墙配置
```toml
[network.firewall]
allow_incoming = true
allow_outgoing = true
restricted_ports = [22, 23, 3389]
allowed_applications = ["cloudplayplus.exe"]
```

## 输入设备配置

### 游戏手柄设置
```toml
[input.gamepad]
enabled = true
deadzone = 0.1
sensitivity = 1.0
rumble_enabled = true
rumble_intensity = 0.8
auto_calibrate = true

[input.gamepad.mapping]
# Xbox 控制器映射
a_button = "confirm"
b_button = "cancel"
x_button = "menu"
y_button = "function"
left_bumper = "l1"
right_bumper = "r1"
left_trigger = "l2"
right_trigger = "r2"
left_stick = "left_stick"
right_stick = "right_stick"
dpad_up = "up"
dpad_down = "down"
dpad_left = "left"
dpad_right = "right"

[input.gamepad.profiles]
default = "xbox"
profiles = [
    "xbox",
    "playstation",
    "nintendo",
    "custom"
]
```

### 键盘设置
```toml
[input.keyboard]
layout = "qwerty"
repeat_delay = 500
repeat_rate = 30
caps_lock_behavior = "normal"
num_lock_behavior = "normal"

[input.keyboard.shortcuts]
fullscreen = "F11"
screenshot = "F12"
record = "Ctrl+R"
stream = "Ctrl+S"
settings = "Ctrl+,"
help = "F1"

[input.keyboard.mapping]
# 自定义按键映射
w = "forward"
s = "backward"
a = "left"
d = "right"
space = "jump"
shift = "run"
ctrl = "crouch"
```

### 鼠标设置
```toml
[input.mouse]
sensitivity = 1.0
acceleration = false
invert_y = false
dpi = 800
polling_rate = 1000

[input.mouse.buttons]
left = "primary"
right = "secondary"
middle = "middle"
side1 = "back"
side2 = "forward"

[input.mouse.scroll]
direction = "normal"
speed = 1.0
smooth = true
```

## 音频配置

### 音频设备
```toml
[audio]
enabled = true
sample_rate = 48000
channels = 2
bit_depth = 16

[audio.input]
device = "default"
volume = 100
muted = false
noise_reduction = true
echo_cancellation = true

[audio.output]
device = "default"
volume = 80
muted = false
spatial_audio = false
virtual_surround = false

[audio.codec]
encoder = "opus"
bitrate = 128
complexity = 5
frame_duration = 20
```

## 视频配置

### 渲染设置
```toml
[video.renderer]
backend = "auto"  # auto, opengl, vulkan, software
vsync = true
triple_buffering = true
frame_limit = 60

[video.quality]
texture_filtering = "anisotropic"
antialiasing = "msaa_4x"
shadow_quality = "high"
reflection_quality = "medium"
particle_quality = "high"

[video.post_processing]
bloom = true
ssao = true
motion_blur = false
depth_of_field = false
color_grading = true
```

### 流媒体编码
```toml
[video.encoding]
codec = "h264"
preset = "fast"
profile = "high"
level = "4.1"
bitrate_mode = "vbr"
crf = 23
max_bitrate = 10000
buffer_size = 2000

[video.encoding.h264]
keyframe_interval = 2
b_frames = 3
ref_frames = 4
entropy_coding = "cabac"
deblocking = true
```

## 性能配置

### 系统优化
```toml
[performance]
cpu_priority = "normal"  # low, normal, high, realtime
memory_limit = 4096
gpu_acceleration = true
hardware_decoding = true

[performance.threading]
main_thread_priority = "normal"
worker_threads = 4
io_threads = 2
render_threads = 1

[performance.caching]
enabled = true
max_size = 1024
ttl = 3600
compression = true
```

### 监控设置
```toml
[monitoring]
enabled = true
interval = 1000
log_metrics = true
alert_thresholds = {
    cpu_usage = 90,
    memory_usage = 85,
    network_latency = 100,
    frame_drops = 5
}

[monitoring.graphs]
show_fps = true
show_latency = true
show_bandwidth = true
show_cpu_usage = true
show_memory_usage = true
```

## 安全配置

### 认证设置
```toml
[security.auth]
enabled = true
method = "password"  # password, oauth, sso
session_timeout = 3600
max_login_attempts = 5
lockout_duration = 900

[security.auth.oauth]
providers = ["google", "github", "discord"]
client_id = ""
client_secret = ""
redirect_uri = ""
```

### 加密设置
```toml
[security.encryption]
transport = "tls_1_3"
cipher_suites = ["TLS_AES_256_GCM_SHA384", "TLS_CHACHA20_POLY1305_SHA256"]
certificate_verification = true
pin_certificates = false

[security.encryption.storage]
algorithm = "aes_256_gcm"
key_derivation = "pbkdf2"
iterations = 100000
```

## 插件配置

### 插件管理
```toml
[plugins]
auto_load = true
auto_update = false
sandboxed = true
permissions = ["network", "filesystem", "input"]

[plugins.repository]
url = "https://plugins.cloudplayplus.com"
update_interval = 86400
signature_verification = true

[plugins.installed]
# 已安装插件列表
flutter_gamecontroller = {
    version = "1.0.0",
    enabled = true,
    config = {}
}
flutter_webrtc = {
    version = "1.0.0",
    enabled = true,
    config = {}
}
```

## 日志配置

### 日志设置
```toml
[logging]
level = "info"  # trace, debug, info, warning, error, fatal
format = "json"  # text, json, xml
output = "file"  # console, file, syslog
max_size = 100
max_files = 10
compression = true

[logging.categories]
app = "info"
network = "debug"
input = "info"
video = "warning"
audio = "info"
```

## 备份和恢复

### 备份设置
```toml
[backup]
enabled = true
auto_backup = true
backup_interval = 86400  # 24小时
max_backups = 10
compression = true
encryption = true

[backup.location]
type = "local"  # local, cloud, network
path = "./backups"
cloud_provider = "dropbox"
network_path = "//server/backups"
```

## 环境变量

CloudPlayPlus 支持通过环境变量覆盖配置：

```bash
# 应用配置
export CLOUDPLAYPLUS_DEBUG=true
export CLOUDPLAYPLUS_LOG_LEVEL=debug
export CLOUDPLAYPLUS_CONFIG_PATH=/custom/config.toml

# 网络配置
export CLOUDPLAYPLUS_PROXY_HOST=proxy.example.com
export CLOUDPLAYPLUS_PROXY_PORT=8080

# 性能配置
export CLOUDPLAYPLUS_CPU_PRIORITY=high
export CLOUDPLAYPLUS_MEMORY_LIMIT=8192
```

## 配置验证

### 配置检查
```bash
# 验证配置文件语法
cloudplayplus --validate-config config.toml

# 检查配置完整性
cloudplayplus --check-config config.toml

# 生成默认配置
cloudplayplus --generate-config > default.toml
```

### 配置测试
```bash
# 测试网络连接
cloudplayplus --test-network

# 测试设备连接
cloudplayplus --test-devices

# 测试性能
cloudplayplus --benchmark
```

## 配置最佳实践

### 性能优化
1. **启用硬件加速** - 使用 GPU 渲染和编码
2. **优化网络设置** - 配置合适的 STUN/TURN 服务器
3. **调整缓存大小** - 根据可用内存设置缓存
4. **使用合适的编码预设** - 平衡质量和性能

### 安全建议
1. **定期更新** - 保持应用和插件最新
2. **限制权限** - 只授予必要的系统权限
3. **加密存储** - 保护敏感配置信息
4. **网络隔离** - 使用防火墙限制网络访问

### 故障排除
1. **备份配置** - 修改前备份当前配置
2. **逐步测试** - 一次只修改一个设置
3. **查看日志** - 使用日志诊断问题
4. **重置配置** - 遇到问题时恢复默认设置

## 下一步

配置完成后，您可以：

- [用户指南](./user_guide.md) - 学习如何使用各项功能
- [故障排除](./troubleshooting.md) - 解决配置问题
- [API 参考](./api_reference.md) - 了解编程接口
- [开发者指南](./developer_guide.md) - 学习开发技巧

如果您需要帮助，请查看：
- 在线配置工具
- 配置模板库
- 社区配置分享
- 技术支持文档
