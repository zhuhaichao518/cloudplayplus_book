# 贡献指南

感谢您对 CloudPlayPlus 项目的关注！我们欢迎所有形式的贡献，无论是代码、文档、测试、问题报告还是功能建议。

## 贡献方式

### 🐛 问题报告
- 报告 bug 和错误
- 提出改进建议
- 反馈用户体验问题

### 💻 代码贡献
- 修复 bug
- 实现新功能
- 改进现有代码
- 优化性能

### 📚 文档贡献
- 改进用户文档
- 添加代码注释
- 编写教程和示例
- 翻译文档

### 🧪 测试贡献
- 编写测试用例
- 进行手动测试
- 报告测试结果
- 改进测试覆盖

### 🎨 设计贡献
- 改进用户界面
- 设计图标和图形
- 优化用户体验
- 提供设计建议

## 开始贡献

### 1. 设置开发环境

#### 系统要求
- **操作系统**: Windows 10+, macOS 10.14+, Ubuntu 18.04+
- **内存**: 8GB RAM (推荐 16GB+)
- **存储**: 10GB 可用空间
- **网络**: 稳定的互联网连接

#### 必需工具
```bash
# Flutter SDK
flutter --version  # 3.0.0 或更高

# Dart SDK
dart --version     # 3.0.0 或更高

# Git
git --version      # 2.20.0 或更高

# IDE (推荐)
# - Visual Studio Code + Flutter 插件
# - Android Studio + Flutter 插件
# - IntelliJ IDEA + Flutter 插件
```

#### 环境配置
```bash
# 克隆项目
git clone https://github.com/your-org/cloudplayplus.git
cd cloudplayplus

# 获取依赖
flutter pub get

# 检查环境
flutter doctor

# 运行测试
flutter test
```

### 2. 选择贡献类型

#### 新手贡献者
- **问题报告** - 报告使用中遇到的问题
- **文档改进** - 修正错别字和改进说明
- **简单 bug 修复** - 修复明显的错误

#### 有经验的贡献者
- **功能实现** - 实现新功能
- **性能优化** - 改进代码性能
- **测试编写** - 添加测试用例

#### 高级贡献者
- **架构改进** - 改进系统架构
- **插件开发** - 开发新插件
- **核心功能** - 改进核心功能

## 贡献流程

### 1. 查找问题或功能

#### 查看现有问题
- **GitHub Issues** - 查看待解决的问题
- **Good First Issue** - 适合新手的简单问题
- **Help Wanted** - 需要帮助的问题
- **Enhancement** - 功能改进建议

#### 创建新问题
如果发现新问题或功能建议，请创建新的 issue：

```markdown
## 问题描述
简要描述问题或功能需求

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

## 附加信息
其他相关信息、截图或日志
```

### 2. 分配问题
- 在 issue 中留言表示要处理
- 等待维护者分配
- 开始开发工作

### 3. 开发工作

#### 创建分支
```bash
# 创建功能分支
git checkout -b feature/your-feature-name

# 或修复分支
git checkout -b fix/your-bug-fix
```

#### 开发规范
- **代码风格** - 遵循 Dart 和 Flutter 代码规范
- **测试覆盖** - 为新功能编写测试用例
- **文档更新** - 更新相关文档和注释
- **提交信息** - 使用清晰的提交信息

#### 代码审查
- 提交前进行自我审查
- 确保代码质量和测试通过
- 准备详细的说明文档

### 4. 提交 Pull Request

#### PR 模板
```markdown
## 描述
简要描述所做的更改

## 类型
- [ ] Bug 修复
- [ ] 新功能
- [ ] 文档更新
- [ ] 性能改进
- [ ] 重构
- [ ] 测试

## 相关问题
修复 #123 或 相关 #456

## 测试
- [ ] 本地测试通过
- [ ] 单元测试通过
- [ ] 集成测试通过
- [ ] 手动测试通过

## 检查清单
- [ ] 代码遵循项目规范
- [ ] 添加了必要的测试
- [ ] 更新了相关文档
- [ ] 提交信息清晰明确

## 截图 (如适用)
添加相关截图或 GIF

## 附加信息
其他需要说明的信息
```

#### PR 要求
- **标题清晰** - 简洁描述更改内容
- **描述详细** - 说明更改原因和影响
- **测试完整** - 包含必要的测试用例
- **文档更新** - 更新相关文档
- **代码质量** - 通过代码审查

### 5. 代码审查

#### 审查流程
1. **自动检查** - CI/CD 自动运行测试
2. **代码审查** - 维护者审查代码
3. **反馈处理** - 根据反馈修改代码
4. **最终审查** - 通过后合并代码

#### 审查重点
- **功能正确性** - 代码逻辑是否正确
- **代码质量** - 是否遵循最佳实践
- **测试覆盖** - 是否有足够的测试
- **文档完整性** - 文档是否更新
- **性能影响** - 是否影响性能

## 代码规范

### Dart 代码规范
```dart
// 遵循官方 Dart 风格指南
// https://dart.dev/guides/language/effective-dart/style

// 命名规范
class GamepadController extends BaseController {
  static const int maxPlayers = 4;
  final String deviceId;
  
  // 私有变量使用下划线
  bool _isConnected = false;
  
  // 方法名使用动词
  void connect() {
    // 实现
  }
  
  // 布尔属性使用 is/has/can 前缀
  bool get isConnected => _isConnected;
}

// 注释规范
/// 游戏手柄控制器类
/// 
/// 负责处理游戏手柄的输入事件和状态管理
class GamepadController {
  /// 连接游戏手柄
  /// 
  /// [deviceId] 设备标识符
  /// 返回连接是否成功
  Future<bool> connect(String deviceId) async {
    // 实现
  }
}
```

### Flutter 最佳实践
```dart
// Widget 构建
class DevicePage extends StatelessWidget {
  const DevicePage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('设备管理'),
      ),
      body: const DeviceList(),
    );
  }
}

// 状态管理
class DeviceController extends ChangeNotifier {
  final List<Device> _devices = [];
  
  List<Device> get devices => List.unmodifiable(_devices);
  
  void addDevice(Device device) {
    _devices.add(device);
    notifyListeners();
  }
}
```

### 测试规范
```dart
// 单元测试
group('GamepadController', () {
  late GamepadController controller;
  
  setUp(() {
    controller = GamepadController();
  });
  
  tearDown(() {
    controller.dispose();
  });
  
  test('should connect successfully', () async {
    final result = await controller.connect('test-device');
    expect(result, isTrue);
    expect(controller.isConnected, isTrue);
  });
  
  test('should handle input correctly', () {
    final input = GamepadInput(button: 'A', pressed: true);
    controller.handleInput(input);
    expect(controller.lastInput, equals(input));
  });
});

// Widget 测试
testWidgets('DevicePage should display devices', (tester) async {
  await tester.pumpWidget(
    MaterialApp(
      home: DevicePage(),
    ),
  );
  
  expect(find.text('设备管理'), findsOneWidget);
  expect(find.byType(DeviceList), findsOneWidget);
});
```

## 文档贡献

### 文档类型
- **用户文档** - 使用说明和教程
- **API 文档** - 编程接口说明
- **开发者文档** - 开发指南和示例
- **配置文档** - 配置选项说明

### 文档规范
- **语言** - 主要使用中文，重要内容提供英文版本
- **格式** - 使用 Markdown 格式
- **结构** - 清晰的标题层次和导航
- **示例** - 提供实际的代码示例
- **图片** - 使用清晰的截图和图表

### 文档更新
```markdown
# 更新现有文档
- 修正错误信息
- 添加缺失内容
- 改进说明清晰度
- 更新过时信息

# 添加新文档
- 新功能说明
- 使用教程
- 最佳实践
- 故障排除
```

## 测试贡献

### 测试类型
- **单元测试** - 测试单个函数和类
- **集成测试** - 测试组件间交互
- **Widget 测试** - 测试 UI 组件
- **端到端测试** - 测试完整功能流程

### 测试要求
- **覆盖率** - 新功能至少 80% 测试覆盖
- **质量** - 测试用例清晰有效
- **维护性** - 测试代码易于维护
- **性能** - 测试运行时间合理

### 测试工具
```bash
# 运行测试
flutter test

# 生成覆盖率报告
flutter test --coverage
genhtml coverage/lcov.info -o coverage/html

# 运行特定测试
flutter test test/controller_test.dart
flutter test --name="GamepadController"
```

## 插件开发

### 插件类型
- **输入插件** - 自定义输入设备支持
- **渲染插件** - 自定义渲染效果
- **网络插件** - 自定义网络协议
- **工具插件** - 辅助功能和工具

### 插件结构
```
my_plugin/
├── lib/
│   ├── my_plugin.dart     # 插件主类
│   ├── models/            # 数据模型
│   └── services/          # 服务实现
├── test/                  # 测试代码
├── pubspec.yaml           # 依赖配置
├── README.md              # 插件说明
└── CHANGELOG.md           # 更新日志
```

### 插件开发流程
1. **需求分析** - 确定插件功能和接口
2. **架构设计** - 设计插件架构和数据结构
3. **代码实现** - 实现核心功能
4. **测试验证** - 编写测试用例并验证
5. **文档编写** - 编写使用说明和 API 文档
6. **发布部署** - 发布插件并集成到主应用

## 贡献者权益

### 认可和感谢
- **贡献者名单** - 在项目文档中列出贡献者
- **代码署名** - 在代码中保留贡献者信息
- **社区认可** - 在社区中认可贡献者工作

### 学习机会
- **技术交流** - 与项目维护者交流技术
- **代码审查** - 获得专业的代码审查反馈
- **技能提升** - 提升编程和开发技能

### 社区参与
- **决策参与** - 参与项目发展方向讨论
- **功能建议** - 提出新功能和改进建议
- **问题讨论** - 参与技术问题讨论

## 行为准则

### 基本原则
- **尊重他人** - 尊重所有贡献者
- **包容性** - 欢迎不同背景的贡献者
- **专业性** - 保持专业和礼貌的交流
- **建设性** - 提供建设性的反馈和建议

### 禁止行为
- **骚扰行为** - 任何形式的骚扰或歧视
- **恶意行为** - 故意破坏或恶意攻击
- **不当言论** - 使用不当或冒犯性语言
- **垃圾信息** - 发送垃圾信息或广告

### 冲突解决
- **私下沟通** - 首先尝试私下解决问题
- **寻求帮助** - 向项目维护者寻求帮助
- **社区调解** - 通过社区讨论解决问题
- **最终决定** - 维护者有最终决定权

## 获取帮助

### 学习资源
- **项目文档** - 查看完整的项目文档
- **代码示例** - 学习现有代码示例
- **最佳实践** - 了解开发最佳实践
- **社区讨论** - 参与社区讨论

### 技术支持
- **GitHub Issues** - 在 issue 中提问
- **Discord 社区** - 加入开发者社区
- **邮件支持** - 联系技术支持团队
- **代码审查** - 通过 PR 获得反馈

### 贡献指导
- **新手指南** - 专门的新手贡献指南
- **贡献模板** - 使用标准的贡献模板
- **代码规范** - 遵循项目的代码规范
- **审查流程** - 了解代码审查流程

## 下一步

准备好开始贡献了吗？

1. **设置环境** - 配置开发环境
2. **选择问题** - 找到适合的问题
3. **开始开发** - 创建分支并开始编码
4. **提交 PR** - 提交 Pull Request
5. **获得反馈** - 通过代码审查获得反馈

### 推荐的第一步
- 查看 [Good First Issue](https://github.com/your-org/cloudplayplus/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22)
- 阅读 [快速开始指南](./getting_started.md)
- 加入 [Discord 社区](https://discord.gg/cloudplayplus)
- 查看 [贡献者指南](https://github.com/your-org/cloudplayplus/blob/main/CONTRIBUTING.md)

感谢您的贡献！🚀
