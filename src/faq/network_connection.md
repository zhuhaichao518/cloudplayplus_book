# 网络无法连接

## 为什么一直无法连接？

请在被控端打开云玩家图形界面。在app被连接时，
如果被控端 app 有闪退重启现象：
- 你的设备可能是笔记本+n卡。请查看你的笔记本是否支持[独显输出模式](https://zhuanlan.zhihu.com/p/670871362),打开后可能解决该问题。
- 你的设备是n卡，但是设置了编码器。请确认编码器为默认或h264。
如果被控端 app 没有闪退重启现象：
- 你的网络类型不支持直连。请尝试在设置页面打开Turn服务器。官方的Turn服务器使用的人较多，可能比较卡(分时间)。你可以参考[该教程](https://www.bilibili.com/video/BV1Rv7MzGE89)搭建Turn服务器。

## 什么情况下需要使用 TURN 服务器？

可以在[这个网站](https://mao.fan/mynat)查看你的网络类型。NAT4（Symmetric NAT，对称形）类型的网络只能连 NAT1（Full Cone，全锥形），非NAT4的网络之间均可以相互直连而不需要Turn服务器。
根据运营商的情况，你的网络类型会动态变化。

## 我开启了官方 TURN 服务器，特别卡

如果你在局域网使用非常流畅，可以考虑自建TURN服务器。如果局域网也非常卡，一般是设备性能不够

## 我的被控端分辨率很高，非常卡，怎么降低码率？

直接降低被控端的分辨率即可。如果你进了全屏游戏，也需要调低游戏内设置的分辨率。

## 如何搭建 TURN 服务器？

可以使用开源项目 coturn 搭建 TURN 服务器。你可以参考作者B站的[教学视频](https://www.bilibili.com/video/BV1Rv7MzGE89)。

** Turn服务器一键搭建脚本下载**
- 官方脚本地址: [https://www.cloudplayplus.com/downloads/install_coturn.sh](https://www.cloudplayplus.com/downloads/install_coturn.sh)。其中用户名和密码是你想要设置的turn服务器用户名和密码，和云玩家的用户名/密码无关。
- 非 Ubuntu 请自行询问大模型如何搭建，可把官方脚本发去询问如何修改。

