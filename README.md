没有找到合适的lean大的OpenWrt For （我的设备）的固件，干脆自己干。
- 设备
  - OrangePi Zero 
  - OrangePi PC 
  - OrangePi r1
  - [树莓派 2B](https://mlapp.cn/369.html)

  
- 完整的编译步骤：
```
# 编译环境Ubuntu19.04
sudo apt-get install build-essential subversion git-core libncurses5-dev zlib1g-dev gawk flex quilt libssl-dev xsltproc libxml-parser-perl mercurial bzr ecj cvs unzip

sudo apt-get -y install build-essential asciidoc binutils bzip2 gawk gettext git libncurses5-dev libz-dev patch unzip zlib1g-dev lib32gcc1 libc6-dev-i386 subversion flex uglifyjs git-core gcc-multilib p7zip p7zip-full msmtp libssl-dev texinfo libglib2.0-dev xmlto qemu-utils upx libelf-dev autoconf automake libtool autopoint

git clone https://github.com/coolsnowwolf/lede
./scripts/feeds update -a
./scripts/feeds install -a
make defconfig
make menuconfig
make download V=s
make V=99 # 或者 make -j1 V=s
make  -j8 V=s
```

- 编译单个插件步骤：
```
./scripts/feeds update -a 
cd package
git clone https://github.com/maxlicheng/luci-app-unblockmusic.git
cd ..
./scripts/feeds install -a
make menuconfig
#在luci->application选中插件,编译
make package/luci-app-unblockmusic/compile V=99
```

- 参考：
  - lede(coolsnowwolf):https://github.com/coolsnowwolf/lede
  - luci-app-unblockmusic(maxlicheng):https://github.com/maxlicheng/luci-app-unblockmusic
  - https://mlapp.cn/374.html

```
LuCI - Applications 菜单即为 LuCI APP 集合，此菜单中的项目即为 LuCI 控制面板中各种各样的功能。

由于选项较多，下面仅列出一些常用的选项：

luci-app-accesscontrol # 访问时间控制
luci-app-adblock # adblock 广告过滤
luci-app-adbyby-plus # 广告屏蔽大师 Plus +
luci-app-advanced-reboot # 高级重启
luci-app-aliddns # 阿里 DDNS 客户端
luci-app-amule # aMule 下载工具
luci-app-aria2 # Aria2 下载工具
luci-app-arpbind # IP/MAC 绑定
luci-app-autoreboot # 支持计划重启
luci-app-commands # Shell 命令模块
luci-app-cshark # CloudShark 捕获工具
luci-app-ddns # 动态域名 DNS
luci-app-dnspod # DNSPod
luci-app-filetransfer # 文件传输
luci-app-firewall # 防火墙支持
luci-app-flowoffload # Turbo ACC FLOW 转发加速
luci-app-frpc # 内网穿透 Frp
luci-app-guest-wifi # WiFi 访客网络
luci-app-hd-idle # 硬盘休眠
luci-app-minidlna # minidlan 服务器
luci-app-mjpg-streamer # 兼容 Linux-UVC 的摄像头程序
luci-app-mwan # MWAN 负载均衡
luci-app-mwan3helper # MWAN3 分流助手
luci-app-n2n_v2 # N2N 内网穿透 VPN
luci-app-nlbwmon # 网络带宽监视器
luci-app-ntpc # NTP 时间同步服务器
luci-app-openvpn # OpenVPN 客户端
luci-app-openvpn-server # OpenVPN 服务器
luci-app-pptp-server # PPTP VPN 服务器
luci-app-ramfree # 释放内存
luci-app-samba # 网络共享 (Samba)
luci-app-samba4 # 网络共享 (Samba4)
luci-app-shadowsocks-libev # SS-libev 服务端
luci-app-shairplay # AirPlay 支持
luci-app-sqm # 流量智能队列管理 (QOS)

luci-app-SSR-plus # SSR/SS/V2Ray 三合一用户界面
Include Shadowsocks New Version # 选择在 SSR-Plus 中是否包含新版 SS 代理
Include V2ray # 选择是否包含 V2Ray 代理
Include Kcptun # 选择是否支持 Kcptun
Include ShadowsocksR Server # 选择是否包含 SSR 服务器
Include ShadowsocksR Socks and Tunnel #选择是否包含 SSR Tunnel

luci-app-ssrserver-python #SSR Python 服务器
luci-app-statistics # 流量监控工具
luci-app-syncdial # 多线多拨
luci-app-transmission # Transmission BT 下载工具
luci-app-ttyd # TTYD 终端命令行
luci-app-upnp # UPnP 服务
luci-app-usb-printer # USB 打印服务器
luci-app-v2ray-pro # V2Ray 代理
luci-app-vlmcsd # KMS 服务器设置
luci-app-vnstat # vnStat 网络监控 (图表)
luci-app-vsftpd # FTP 服务器
luci-app-watchcat # 断网检测与定时重启
luci-app-webadmin # Web 管理页面设置
luci-app-wifischedule # WiFi 计划
luci-app-wireguard # WireGuard 状态
luci-app-wol # Wake on Lan 网络唤醒
luci-app-wrtbwmon # 实时流量监测
luci-app-xlnetacc # 迅雷快鸟
luci-app-zerotier # ZeroTier 内网穿透

```
