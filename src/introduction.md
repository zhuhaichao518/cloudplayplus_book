# CloudPlayPlus Book

## 快速开始
[用户指南](./user_guide.md)

[常见问题解答](./faq.md)

## 什么是 CloudPlayPlus？

[CloudPlayPlus](https://cloudplayplus.com) 是一款功能强大的跨平台串流应用，它支持你从你能想象到的绝大部分设备查看和操作安装了CloudPlayPlus桌面端的个人电脑。

- 作为远程控制软件，你可以将它用来作为远程桌面(如向日葵，rustdesk)软件的替代品。

- 作为串流软件，你可以将它用来替代作为parsec,moonlight的替代品，减少网络问题带来的不便。

CloudPlayPlus的核心在于其易用性。安装软件后，你无需进行任何麻烦的配置，也无需搭建虚拟网络即可随时随地连接到自己的设备。你可以使用[网页](https://cloudplayplus.com/web1/)作为控制端。

CloudPlayPlus的性能优于大部分市面上的远程软件。在适配的设备上，CloudPlayPlus充分调用了设备的显卡性能，旨在以最小的资源消耗达到最优的串流体验。在不适配的设备上，CloudPlayPlus会调用CPU进行编码。[适配情况](TODO)

客观来讲，CloudPlayPlus在未适配的设备上性能上与优化到极限的串流软件(如moonlight)尚有差距，特别是在未优化的设备上。在优化过的设备上，CloudPlayPlus的性能已经逼近理论极限。在局域网+有线的情况下，两台PC之间可以做到16ms以内的2k串流延迟，效果见[该视频](https://www.bilibili.com/video/BV1WBVjzBEKo/)。

## 主要特性

### 🖥️ 多平台兼容性
- **桌面平台**: Windows、macOS、Linux(待发布，可自行编译)
- **移动平台**: iOS、Android、Android TV
- **Web 平台**: 支持Chrome、Edge等主流浏览器作为控制端

### 🎮 游戏控制器支持
- CloudPlayPlus会自动检测连接到控制端的手柄，在控制端手柄的按钮被按下后，CloudPlayPlus会在被控端初始化一个对应的Xbox手柄。你也可以创建屏幕虚拟手柄来使用。

- 如果虚拟化手柄未生效，请确认ViGEm Bus已安装。他被打包在CloudPlayPlus主安装文件中，你也可在安装好的文件夹中找到它的安装包。如果你使用很旧版本的[Sunshine](https://github.com/LizardByte/Sunshine)，也可能因为ViGEm Bus版本的兼容性导致无法初始化虚拟手柄。

### ⚡️ 低延迟，高性能

## 目标用户/场景

### 办公
- 提供二级密码认证
- 自建中继服务器
- 将闲置设备作为扩展屏

### 娱乐
- 在任何设备上串流到自己/好友的高性能PC
- 自建中继服务器
- 需要低延迟游戏流媒体的玩家
- 支持多种输入设备

### 企业服务
- 云游戏平台
- 云服务与云软件
- 新式便携设备办公/娱乐

## 技术架构

CloudPlayPlus 使用Flutter进行开发，旨在减少平台之间的差异。
对于远程桌面送显的性能瓶颈，未来考虑使用Native进行渲染。
CloudPlayPlus 的所有功能均通过Flutter及其插件进行实现。
核心插件
- **flutter-webrtc**: 将Webrtc集成到flutter的插件。CloudPlayPlus通过修改其API以及WebRTC中抓取编码逻辑实现抓取音频，视频硬件加速等功能。
- **hardware_simulator**: CloudPlayPlus团队实现的硬件模拟器。支持监听和模拟键盘/鼠标/手柄/虚拟显示器等硬件行为。

## 许可证

CloudPlayPlus 采用[GNU GPL3许可证](./license.md)。对于任何遵从许可证的行为, CloudPlayPlus团队保有法律追诉的权利。

## 下一步

- [快速开始](./getting_started.md) - 了解如何快速上手 CloudPlayPlus
- [安装指南](./installation.md) - 详细的安装说明
- [用户指南](./user_guide.md) - 完整的使用教程
