# OpenCore-XiaoXin700

自用黑苹果EFI，使用官方原版OpenCore，可以引导Windows，尽可能的减少修改，目前还未完善。

由于更换电脑，项目终止。

使用前请自行添加三码，可参考[corpnewt/GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)

## **存在的问题**

1. 无法获取CPU风扇转速。

## **更新日志**

2020-10-30:
1. 添加了一些kexts。

2020-10-23：

1. 去除了三码；
2. 修复了耳机声音不正常，需要调节声道的问题；
3. 更新了部分kexts，添加亮度调节快捷键的kexts。

2020-10-18：

1. 第一版，能够正常安装并启动，并保证鼠标键盘等基本功能可以使用（可能体验不佳）。

---

## **配置**

| 类型 | 参数 |
| - | - |
| CPU | Intel i5-6300HQ |
| 内存 | 8GB 三星 DDR4 2133MHz |
| 硬盘 | 三星 850 EVO 500GB SATA |
| 显卡 | Intel HD530 |
| 声卡 | Realtek ALC233 |
| 网卡 | Broadcom BCM94352Z |

---

## **部分文件用途说明**

为确保不会添加一些不必要的文件，对每项文件的用途进行说明。

### **ACPI**

    SSDT-EC-USBX.aml
    SSDT-GPI0.aml
    SSDT-PLUG.aml
    SSDT-PNLF.aml
以上为针对6代CPU，官方推荐的补丁。以上补丁通过官方给出的[Guide](https://dortania.github.io/Getting-Started-With-ACPI/)制作。

### **Drivers**

    HFSPlus.efi
    OpenRuntime.efi
此为必须Drivers

    OpenCanopy.efi
启用第三方主题（虽然放进来了，但并没有使用）

### **Kexts**

    AppleALC.kext
声卡驱动

    AirportBrcmFixup.kext
    BrcmBluetoothInjector.kext
    BrcmFirmwareData.kext
    BrcmPatchRAM3.kext
BCM网卡及蓝牙驱动

	CPUFriend.kext
	CPUFriendDataProvider.kext
定制的CPU变频驱动

	HibernationFixup.kext
修复睡眠问题

    Lilu.kext
必须

	NoTouchID.kext
关闭TouchID支持，解决登陆时卡顿的现象

    NVMeFix.kext
修复NVMe（未测试）

	RealtekRTL8111.kext
有线网卡驱动

	RTCMemoryFixup.kext
**未启用**
避免AppleRTC与BIOS之间的某些冲突，不清楚是否需要，但貌似没有负面影响。若未使用时出现卡死，突然重启等现象可尝试开启

	SATA-100-series-unsupported.kext
识别100系列主板，可以修复某些情况下搜不到硬盘的问题

    USBPorts.kext
	USBPower.kext
个人定制的USB驱动

    VirtualSMC.kext
    SMCProcessor.kext
    SMCSuperIO.kext
仿冒SMC，必须，后两项为CPU温度及风扇转速读取，但是风扇转速貌似无效。

    VoodooPS2Controller.kext
    BrightnessKeys.kext
键盘驱动，亮度调节快捷键驱动

    WhateverGreen.kext
显卡驱动，必须
