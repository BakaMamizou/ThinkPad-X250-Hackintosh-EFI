# ThinkPadX250-Hackintosh-EFI
ThinkPad X250\T450\T450s\X1 Carbon 3rd Hackintosh EFI  
![image](https://github.com/BakaMamizou/ThinkPad-X250-Hackintosh-EFI/IMG/IMG01.png)


2023.11.20 项目建立，本人测试X250 运行MacOS 14 Sonoma成功，目前OC版本0.9.6

### 机器配置
| 型号 | ThinkPad X250 |
| :----: | :----: |
| CPU | i5-5300U |
| GPU | HD5500 |
| 内存 | Samsung DDR3L 1600 8G |
| 存储 | Samsung EVO 870 500G |
| WIFI | Intel Wi-Fi 6E AX210 |
| WWAN | Sierra Wireless AirPrime EM7345 |

### 支持的MacOS版本:
* macOS 12.00 Monterey (需更替Ventura支持的itlwm，否则无线网卡不驱动)
* macOS 13.00 Ventura (需更替Ventura支持的itlwm，否则无线网卡不驱动)
* macOS 14.00 Sonoma
### 在开始之前
* 一台ThinkPad X250\T450\T450s\X1 Carbon 3rd
* 一台电脑来制作安装媒介
* 一个16G或更大的U盘 (推荐3.0的盘 更快)
* 这个项目里的EFI文件

### 正常工作的部件
* 电源管理
* 休眠与唤醒
* Intel核显
* 音频
* 触摸板(手势支持，不支持压感)
* USB 3.0
* Sata硬盘
* 双电池电量显示
* Fn快捷键及亮度调节
* 内建摄像头
* 内建麦克风 
* 蓝牙
* 读卡器
* 有线网卡

### 半完美的部件
* Intel无线网卡(半完美HandOff 隔空传送半残废 网卡更新参见[OpenIntelWireless/itlwm](https://github.com/OpenIntelWireless/itlwm)项目
* WWAN有驱动，但未测试
* 添加了触摸屏驱动，因设备无此选项，故无法测试
* 添加了拓展坞支持，因无拓展坞，故无法测试
* 支持 Sidecar (开启Sidecar会导致系统随机冻结，请酌情开启)

### 不工作的部件:
* VGA输出

### 安装过程
制作安装媒介:
* 在您的U盘上创建安装媒介
(MacOS下制作启动盘https://support.apple.com/zh-cn/HT201372)
(Windows下制作启动盘使用TransMac，右键选取U盘及镜像烧录启动盘)
* 挂载U盘上的ESP(EFI)分区 : (注意在终端挂载分区时的磁碟号，一定要挂载U盘上的！！！)
* 终端输入示例
```
diskutil list
sudo diskutil mount /dev/disk3s1(注意！是U盘的EFI分区！)
```

* 将EFI文件夹复制到U盘的EFI分区上.
* 弹出U盘，插入到笔记本上

开始安装黑苹果:
* 开机 F12选择U盘引导
* 打开磁盘工具，将要安装MacOS的分区格式化成APFS格式(注意！此操作会删除您该磁盘分区内所有文件!!!)
* 关闭磁盘工具，选择安装MacOS
* 选择要安装的分区，等待
* 安装进度条走完后,自动重启
* F12选择U盘引导，OC启动界面选择从磁盘启动MacOS以完成接下来的安装
* 等待，跑码(期间有多次重启，请务必选择MacOS Installer选项，不要选成U盘启动的)
* 进入设定界面，按照屏幕上的指示完成开机配置
* 挂载磁盘上的ESP (EFI)分区(注意！挂载时的磁盘序号)
```
diskutil list
sudo diskutil mount /dev/disk0s1
```

* 复制此项目的EFI文件夹到黑苹果的EFI分区
* 将U盘从电脑弹出，重启，开机选择从硬盘引导
* 开始你的黑苹果之旅

### 建议的BIOS设定
Security -> Security Chip`: Disabled;

Memory Protection -> Execution Prevention: Enabled;

Virtualization -> Intel Virtualization Technology: Enabled;

Internal Device Access -> Bottom Cover Tamper Detection: must be Disabled;

Anti-Theft -> Current Setting: Disabled;

Anti-Theft -> Computrace -> Current Setting: Disabled;

Secure Boot -> Secure Boot: Disabled;

UEFI/Legacy Boot: Both&UEFI First;

CSM Support: Yes.