## debian 11 + linux 5.14-rc4 redmi2 刷机包

### 包在release里面

By HandsomeHacker <handsomeyingyan@gmail.com>

仅适用于高通msm8916方案的红米2手机（代号wt88047 & wt86047）

注意：这会破坏手机上用户分区里的所有数据，如果这是你的主力机，请做好备份。

运行主线内核造成任何程度的机器硬件损害，后果自负。

刷机步骤：

1. 进入手机原厂的fastboot模式(音量下+电源键)，然后刷入lk2nd
``` shell
   fastboot flash:raw boot lk2nd.img
   fastboot reboot
```
2. 在lk2nd界面中刷入debian的内核和文件系统
  ```  shell
   fastboot flash boot boot.img
   fastboot erase userdata
   fastboot flash userdata userdata.img
   fastboot reboot
  ```
3. Enjoy~

默认用户名 mobian 默认密码 1234

## 感谢：
   msm8916-mainline项目 https://github.com/msm8916-mainline

   postmarketos 项目 https://postmarketos.org/

   mobian 项目 https://mobian-project.org/
   
## 注意事项
   如果你的手机在插卡之后检测到卡但是没有信号，则你的手机型号是wt86047。
   
   使用和wt88047不一样的modem固件。
   
   可以通过adb来切换modem固件解决。
``` shell 
   adb shell
   cp lib/firmware-wt86047/* lib/firmware/
```

## 更新日志

- 2021/8/28

   * 加入支持anbox和lxc的相关内核选项
   * 加入adb支持
   * 支持modem，流量和通话正常

## DEMO

![demo](demo.jpg)
