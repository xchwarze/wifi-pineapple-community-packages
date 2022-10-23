# WiFi Pineapple Community Packages

This repository contains the OpenWrt packages for the WiFi Pineapple cloner community repository. Packages found inside this repository will be available to download via opkg.

To contribute, please submit a pull request.

## Build steps

```bash
# download openwrt
git clone https://git.openwrt.org/openwrt/openwrt.git
cd openwrt
git checkout v19.07.7

# config
#curl -L https://downloads.openwrt.org/releases/19.07.7/targets/ar71xx/generic/config.buildinfo > .config
curl -L https://downloads.openwrt.org/releases/19.07.7/targets/ramips/mt7620/config.buildinfo > .config
cp feeds.conf.default feeds.conf

# add openwrt-useful-tools feed
echo "src-git wpcpackages https://github.com/xchwarze/wifi-pineapple-community-packages.git" >> feeds.conf

# build and install tools and toolchain
make tools/install -j12
make toolchain/install -j12

# download and index feeds
./scripts/feeds update -a
./scripts/feeds update -i

# generate make for package
./scripts/feeds install -p wpcpackages hcxtools-custom

# add packages to build
make menuconfig

# build package
make package/hcxtools-custom/download
make package/hcxtools-custom/compile -j12
```
