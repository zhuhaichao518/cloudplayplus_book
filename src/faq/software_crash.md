# 软件无法打开/闪退

## Windows 打开 app 报错，报缺少 MSVCP140.dll、VCRuntime140_1.dll

常见于新安装系统，尚未安装 Visual C++ 2015-2022 Redistributable。可在[此链接](https://answers.microsoft.com/en-us/windows/forum/all/looking-for-visual-c2015-2022-redistributable/9d6c7974-4063-46ee-8429-c649b3c7f1e6)下载。

## Windows 服务已启动，但是不显示云玩加界面。

缓解方式(该方案无法抓取或操作UAC窗口以及windows登录界面):
- 打开用户账户控制，将通知改为”从不通知“以外的任意级别。
- 以管理员权限运行和登录”云玩加“（如果不用管理员权限 将无法控制以管理员权限运行的应用）。打开软件时，在弹出的UAC窗口中点击“否”。
- 点击”允许被控“，在弹出窗口点”否“。
目前还需要额外的资料解决该类问题。如果你有足够的时间和作者一起调试请联系作者。

## 鸿蒙闪退

请在官网下载适合华为设备的版本(skia), 或者使用Edge浏览器做控制端。

## ios闪退
ios最低支持版本为ios13。
