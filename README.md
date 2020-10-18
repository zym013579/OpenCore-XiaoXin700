# OpenCore-XiaoXin700

自用黑苹果EFI，使用官方原版OpenCore，可以引导Windows，尽可能的减少修改，目前还在完善阶段。

## **更新日志**

2020-10-18：

1. 第一版，能够正常安装并启动，并保证鼠标键盘等基本功能可以使用（可能体验不佳）。

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
    Lilu.kext
必须

    VirtualSMC.kext
    SMCProcessor.kext
    SMCSuperIO.kext
仿冒SMC，必须

    WhateverGreen.kext
显卡，必须

    AirportBrcmFixup.kext
    BrcmBluetoothInjector.kext
    BrcmFirmwareData.kext
    BrcmPatchRAM2.kext
BCM网卡驱动

    AppleALC.kext
声卡

    NVMeFix.kext
修复NVMe（未测试）

    USBPorts.kext
USB

    VoodooPS2Controller.kext
键盘等驱动

---

## 最后
第一次写Readme，感谢什么的都暂时没写。