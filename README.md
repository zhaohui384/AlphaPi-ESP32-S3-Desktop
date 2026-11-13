# AlphaPi One ESP32-S3 Desktop

电子吧唧 · 小智语音助手 · 网络收音机 · 手机设置

## 下载

[下载最新 2 倍增益测试刷机包](AlphaPi-One-S3-2x-audio-test.zip)

本仓库当前提供刷机测试包，不是完整源码仓库。解压后查看 README.txt，firmware 目录包含固件和 flash.cmd。

## 适用设备

- AlphaPi One，ESP32-S3，实测 revision 0.2、8 MB Flash。
- A/B/L/R 四键，160×128 横屏。
- **不适用于 AlphaPi One S（ESP32-S2）。** One S 项目请查看 https://github.com/zhaohui384/AlphaPi-OneS-Desktop 。

## 本次变更与验证状态

- 小智与收音机共用 2 倍软件增益，保留输出限幅及削顶统计。
- 修正音频逐帧等待过长的问题，改为收音机播放任务定期让出 CPU。
- 暂停时由播放任务停止音频，减少界面等待 UART 锁。
- 3 倍增益满音量已反馈破音，本包未采用。

**最新发送节奏修正版已在设备写入并通过哈希校验，但声音恢复、按键和长期稳定性尚未得到实机确认。此包属于测试版。** 去除预置 Wi-Fi 后重新编译通过，未重新刷入验证首次配网。

## 刷机和使用

1. 安装 Python 和 esptool 4.5.1：`python -m pip install esptool==4.5.1`。
2. 解压整个包，运行 firmware/flash.cmd，输入实际串口，如 COM16。
3. 保持 USB 稳定，等待写入和校验完成；如无法自动进入下载模式，手动进入后重试。
4. 完成后正常拔插 USB，不按 BOOT。

首次配网：进入设置，手机连接 AlphaPi-Desk，默认密码 alphapi88，打开 http://192.168.4.1 ，配置 2.4 GHz Wi-Fi。固件不含个人 Wi-Fi 预设或设备 NVS；重刷不主动清除设备已有配置。

L/R 左右选择或切台，A 确认/播放暂停，B 返回。长按 L 加音量，长按 R 减音量，建议先从 50% 试听。

## 来源

基于 https://github.com/78/xiaozhi-esp32 和用户提供的 AlphaPi 适配资料。根目录 LICENSE 保留小智上游 MIT 版权；部分参考适配代码的独立再分发授权尚未确认，不能据此将所有第三方内容统一声明为 MIT。

