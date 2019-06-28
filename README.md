没有找到合适的lean大的OpenWrt For （我的设备）的固件，干脆自己干。
- 设备
  - lenovo Y1 （老毛子）
  - Xiaomi WiFi nano （OpenWrt官方原版）
  - K2 (老毛子）
  - 树莓派 2B （lean op）
  - OrangePi PC （lean op）
  
- 完整的编译步骤：
```
# 编译环境Ubuntu19.04
sudo apt-get build-essential subversion git-core libncurses5-dev zlib1g-dev gawk flex quilt libssl-dev xsltproc libxml-parser-perl mercurial bzr ecj cvs unzip
git clone https://github.com/coolsnowwolf/lede.git
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
  - https://blog.csdn.net/ypbsyy/article/details/81218361
  - https://www.right.com.cn/forum/thread-344012-1-1.html
  - https://www.right.com.cn/forum/forum.php?mod=viewthread&tid=344825&page=1
  - https://mlapp.cn/374.html
