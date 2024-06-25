# 在Win11上给Android刷机的简单过程
## Pixel官方刷机工具
https://flash.android.com/welcome (谷歌的所有Android系统）
## 配置Android开发者选项
[官方文档参考](https://source.android.com/source/running?hl=zh-cn#flash-unlock)
如果您无法启用 OEM 解锁功能，请确保：
1. 您的设备是无锁机。
2. 您的设备已连接到互联网。
3. 您的设备已签入 Google（如果您的设备刚刚才连接到互联网，就可能还没有签入 Google）。如需强制签入，请在拨号器中输入 *#*#CHECKIN#*#* (*#*#2432546#*#*)（不需要插入 SIM 卡）。输入此号码（不需要按“通话”）后，相应文字即会消失，并且系统会显示成功通知。
## 配置电脑环境
  ### 安装[Google USB Driver](https://developer.android.com/studio/run/win-usb)
  在文件夹中找到"android_winusb.inf"并右键安装
  ### 部署软件开发工具包平台工具
  1. [下载SDK Platform Tools](https://developer.android.com/tools/releases/platform-tools)
  2. 设置>系统>系统信息>**高级系统设置**>环境变量>系统变量>Path，添加platform tools文件路径
  3. 启动cmd/Powershell，输入`adb version`,若出现版本信息则成功
## 解锁bootloader
解锁之后，系统会清空设备上的所有数据。若手机中有重要数据，请提前备份手机！
1. [手机冷启动进入fastboot模式（Pixel:关机状态下长按电源键和音量下键），连接电脑，在cmd/Powershell中输入`fastboot devices`，若出现设备信息则连接成功]或者手机连接电脑后，启动cmd/Powershell,输入`adb reboot bootloader`进如flashboot模式
2. 启动CMD/Powershell，输入 Bootloader 解锁指令，并按下回车执行:`fastboot oem unlock`(Android 5.0 及以下)；`fastboot flashing unlock`(Android 6.0 及以上)
4. 在设备端此时会弹出 Bootloader 解锁的确认界面，使用音量键移动关标选择确认，按下电源键开始解锁
5. 解锁后设备会被清除数据并重新启动，待设备开机后检查「USB 调试」选项；重新进入 Bootloader 界面等候
6. 若此时卡在启动界面，可强制关机并冷启动进入fastboot模式（反正要刷机的嘛）
## 刷机
1. 下载系统镜像并解压，将"platform-tool"文件夹中的文件复制入系统镜像文件夹中
2. 双击运行"flash-all.bat"，等待即可
