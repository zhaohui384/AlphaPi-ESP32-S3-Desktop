# AlphaPi Desktop

AlphaPi One 多功能桌面：电子吧唧、小智语音助手、网络收音机、时钟天气与手机配置。

## 硬件
AlphaPi One，ESP32-S3，8MB Flash、2MB Quad PSRAM、160×128横屏。
本项目使用 UART N32 音频/按键协处理器，不适用于 One S、STEM 或 Zero。

## 操作
L/R左右选择，A确认，B返回；长按L加音量，长按R减音量。
设置和吧唧页面可开启 AlphaPi-Desk 热点（密码alphapi88），手机访问192.168.4.1配置Wi-Fi、裁切上传图片、设置天气地区。

## 构建
基于78/xiaozhi-esp32改造，使用ESP-IDF 6.0.1。
启用IDF环境后，在项目根目录执行：
```
idf.py -B build-desktop -D "SDKCONFIG_DEFAULTS=sdkconfig.defaults;sdkconfig.defaults.esp32s3;sdkconfig.desktop" build
```
自定义板级实现：main/boards/alphapi-desktop/。
当前板型在CMake中专用选择，尚未完整接入上游标准板型菜单；不宣称支持其他板型或通过上游全部测试。
公开源码未附带wifi_profile.private.h，默认不预设家庭Wi-Fi，请通过设备热点配网。

## 验证和限制
当前个人设备实测小智可对话、收音机播放时按键有效，用户确认系统不卡。
收音机和小智整体音量仍偏小，原因尚未确定；蓝牙未启用。
私有Wi-Fi版固件不在本公开源码包中。公开固件应从不含私有配置的源码重新编译、实机验证后再发布。

## 上游与许可证
基于 https://github.com/78/xiaozhi-esp32 ，保留上游MIT LICENSE及版权声明。
收音机、屏幕驱动沿用用户提供的AlphaPi One独立收音机工程；依赖组件各自许可证仍适用。
这是一份社区改造工程，非核桃编程或小智官方发布。
