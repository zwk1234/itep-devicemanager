## 外设管理后台程序

##### 1、外设管理配置文件

默认配置为`/etc/itep-devicemanager-daemon/devicemanager.conf`，生效的配置为`/opt/config/devicemanager/devicemanager.conf`。

通过修改配置`devicemanager.conf`控制外设，配置内容如下：

```
[USB]
;Use class information in the Interface Descriptors种类信息定义在接口描述符中
00h=1

......

[Serial]
level=1

[Parallel]
level=1

[Special]
.....
```

其中0为禁用外设，1为启用外设。Group名是USB为USB设备，键为USB设备类代码。Serial与 Parallel分别为串口、并口。Special暂定为例外设备。

##### 2、外设控制

根据需求修改保存配置文件（`/opt/config/devicemanager/devicemanager.conf`），修改完成后使用`systemctl restart devicemanager.service`重启服务即可完成设置。

##### 3、打包方法

使用git克隆，进入项目目录，输入`dpkg-buildpackage -b -tc -uc -us`即可完成deb制作

### 附录：USB设备类代码表

| Base Class | Descriptor Usage | Description                                                  |
| ---------- | ---------------- | ------------------------------------------------------------ |
| 00h        | Device           | Use class information in the Interface Descriptors种类信息定义在接口描述符中 |
| 01h        | Interface        | Audio音频设备                                                |
| 02h        | Both             | Communications&CDC通信设备                                   |
| 03h        | Interface        | HID(Human Interface Device)人机接口设备                      |
| 05h        | Interface        | Physical物理设备                                             |
| 06h        | Interface        | Image图像设备                                                |
| 07h        | Interface        | Printer打印机                                                |
| 08h        | Interface        | Mass Storage 大容量存储                                      |
| 09h        | Device           | Hub集线器                                                    |
| 0Ah        | Interface        | CDC-Data通信设备                                             |
| 0Bh        | Interface        | Smart Card智能卡                                             |
| 0Dh        | Interface        | Content Security内容安全设备                                 |
| 0Eh        | Interface        | Video视频设备                                                |
| 0Fh        | Interface        | Personal Healthcare个人健康设备                              |
| 10h        | Interface        | Audio/Video Devices声音/视频设备                             |
| 11h        | Device           | Billboard Device Class广播牌设备                             |
| 12h        | Interface        | USB Type-C Bridge Class                                      |
| DCh        | Both             | Diagnostic Device诊断装置                                    |
| E0h        | Interface        | Wireless Controller无线控制器                                |
| EFh        | Both             | Miscellaneous其他                                            |
| FEh        | Interface        | Application Specific特定于应用程序                           |
| FFh        | Both             | Vendor Specific特定于供应商                                  |




