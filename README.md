lede(coolsnowwolf):https://github.com/coolsnowwolf/lede

luci-app-unblockmusic(maxlicheng):https://github.com/maxlicheng/luci-app-unblockmusic


由于原作者提供的IPK并未包含我设备，所以自己编译了。
- 设备
  - lenovo Y1
  - Xiaomi WiFi nano
  - K2

步骤：
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
