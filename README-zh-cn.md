# ZeroNet-kivy
[English](./README.md)

ZeroNet的图形界面控制面板和APP打包，使用Kivy框架
[Kivy](https://kivy.org) 是一个基于Python的跨平台的开源GUI框架。它可以部署到Android和iOS，甚至是桌面平台 (Win, Linux, Mac )。

目前本项目的代码只能在Android上运行，欢迎对iOS开发感兴趣的同学加入。
目前本项目处于Alpha阶段，其GUI缺乏功能和美工设计，代码里保留了很多用于测试的代码。请贡献你的创意，无论是美工还是代码！

### 屏幕截图:

#### 启动界面
![Startup](/screenshots/startup.png)
#### UI
![UI](/screenshots/ui.png)

### ZeroNet:

#### 加载界面
![Loading](/screenshots/loading.png)
#### ZeroHello
![ZeroHello](/screenshots/zerohello.png)
#### ZeroMe
![ZeroMe](http://i.imgur.com/nog7YPG.png)


## 目标：

* 易于安装
 - 去掉无用文件，减小安装包体积
 - 在Google Play, Apple App Store上发布，另外还有其他平台的官方APP市场或软件包仓库
* 易于使用
 - 仅仅一触即可启动或停止ZeroNet服务
 - 稳定运行，防止被系统杀掉
   + 在Android上，使ZeroNet运行为前台服务，降低被杀几率。如果还是被杀，可以创建一两个守护进程，用来重启ZeroNet服务。
 - 在移动设备上，降低电池、流量、存储的消耗量。自动调节ZeroNet在不同情景下的运行模式：是Wifi还是流量，是充着电还是低电量。当然，用户也能自行调节。
 - 使users.json和其他敏感数据保存在APP的内部私有目录，避免让其他APP接触到
 - 通过GUI导入主密钥或users.json，让用户能够跨设备使用同一ID
 - 通过GUI设置ZeroNet，而不是手动编辑zeronet.conf
 - 提供一个瘦客户端供用户选择。就像比特币瘦客户端一样，用户无需等待同步大量数据、消耗大量电量和存储，即可使用ZeroNet。瘦客户端向随机的代理 ( gateway ) 服务器接收和发送数据（发送前用私钥签名），私钥并不会泄露。

以上的目标，有一部分不是本项目单干就能搞定的，需要向ZeroNet贡献代码，提交更改。

## ZeroNet的APK打包教程

打包过程不是很难，因为Kivy的Buildozer自动化了很多工作。
[打包教程在这，很详细的](./Tutorial-of-packaging-APK-zh-cn.md)

## APK下载

[ » 点击下载](https://github.com/HelloZeroNet/ZeroNet-kivy/releases)

[ » 老版本](https://github.com/mkg20001/ZeroNet-kivy/releases)

## 如何使用APK

* 注意你手机上的防火墙和权限控制的设置，请让本APK通过
* 如果你浏览网站时遇到问题，请尝试其他浏览器
* 如果你想关闭ZeroNet，请点击ZeroHello首页的左上角的⋮ 按钮，在菜单中选择关闭
* 你可以升级ZeroNet本身的代码，方法跟在电脑上一样：点击ZeroHello首页的左上角的⋮ 按钮，在菜单中选择版本 x.x.x( rev xxxx)，不要管它是不是显示最新，就点它，就会升级到最新的开发版
* 遇到bug或其他问题到外部存储/Android/data/包名如android.test.myapp17/files/zero/log里的log看看有什么异常报错

## 项目结构一览
  * src
    - zeronet.kv - Gui 布局
    - main.py - 主文件
    - service.py - 服务文件
    - platform_*.py - 平台具体代码
    * zero -  ZeroNet本身的全部代码 (if content is missing run `git submodule init --recursive`)
      - zeronet.py - ZeroNet 启动器
  * buildozer.spec - Buildozer的配置，你可以定义APK的包名、标题、版本号、android权限、服务等等.
