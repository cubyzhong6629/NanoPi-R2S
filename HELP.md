# 编译心得

## 源码来源
1. https://github.com/friendlyarm/friendlywrt_scripts
2. https://github.com/friendlyarm/uboot-rockchi
3. https://github.com/friendlyarm/friendlywrt_configs
4. https://github.com/friendlyarm/prebuilts
5. https://github.com/friendlyarm/sd-fuse_rk3328
6. https://github.com/friendlyarm/friendlywrt_device_rk3328
7. https://github.com/friendlyarm/kernel-rockchip
8. https://github.com/friendlyarm/friendlywrt


## `openwrt`官方依赖包

>>>
[https://downloads.openwrt.org/](https://downloads.openwrt.org/)

## 集成`openclash`源码
src-git openclash https://github.com/vernesong/OpenClash.git


## `openclash` 依赖包
``` properties
CONFIG_PACKAGE_iptables-mod-tproxy=y
CONFIG_FEED_openclash=y
CONFIG_PACKAGE_iptables=y
CONFIG_PACKAGE_dnsmasq-full=y
CONFIG_PACKAGE_coreutils=y
CONFIG_PACKAGE_coreutils-nohup=y
CONFIG_PACKAGE_bash=y
CONFIG_PACKAGE_libcurl=y
CONFIG_PACKAGE_jsonfilter=y
CONFIG_PACKAGE_ca-certificates=y
CONFIG_PACKAGE_ipset=y
CONFIG_PACKAGE_ip-full=y
CONFIG_PACKAGE_iptables-mod-extra=y
```



## 增加`OpenClash`

```yaml
      - name: Install OpenClash
        run: |
          cd friendlywrt-rk3328/friendlywrt/
          echo "src-git openclash https://github.com/vernesong/OpenClash.git" >> feeds.conf.default

      - name: Update Target.mk
        run: |
          cd friendlywrt-rk3328/friendlywrt/include
          sed -i 's/dnsmasq /dnsmasq-full default-settings luci /' target.mk
```


## 增加依赖包
```shell script
          echo "CONFIG_FEED_openclash=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_luci-app-openclash=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_iptables-mod-tproxy=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_iptables=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_dnsmasq-full=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_coreutils=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_coreutils-nohup=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_bash=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_libcurl=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_jsonfilter=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_ca-certificates=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_ipset=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_ip-full=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_iptables-mod-extra=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_libcap-bin=y" >> configs/config_rk3328
```



## `.config`配置

1. 来自[fanck0605](https://github.com/fanck0605/openwrt-nanopi-r2s)

```properties

CONFIG_TARGET_rockchip=y
CONFIG_TARGET_rockchip_armv8=y
CONFIG_TARGET_rockchip_armv8_DEVICE_friendlyarm_nanopi-r2s=y
CONFIG_TARGET_ROOTFS_PARTSIZE=256

CONFIG_LUCI_LANG_en=y
CONFIG_LUCI_LANG_zh_Hans=y
CONFIG_LUCI_LANG_zh_Hant=y

CONFIG_OPENSSL_OPTIMIZE_SPEED=y

CONFIG_PACKAGE_kmod-fs-ext4=y
CONFIG_PACKAGE_kmod-fs-f2fs=y
CONFIG_PACKAGE_kmod-fs-ntfs=y
CONFIG_PACKAGE_kmod-fs-vfat=y
CONFIG_PACKAGE_kmod-tcp-bbr=y
CONFIG_PACKAGE_kmod-tun=y
CONFIG_PACKAGE_kmod-usb-net-rndis=y
CONFIG_PACKAGE_kmod-usb-net-rtl8150=y
CONFIG_PACKAGE_kmod-usb-ohci-pci=y
CONFIG_PACKAGE_kmod-usb-storage-extras=y
CONFIG_PACKAGE_kmod-usb-storage-uas=y
CONFIG_PACKAGE_kmod-usb-uhci=y
CONFIG_PACKAGE_kmod-usb2-pci=y
CONFIG_PACKAGE_kmod-usb3=y

CONFIG_PACKAGE_bash=y
CONFIG_PACKAGE_bc=y
CONFIG_PACKAGE_bind-dig=y
CONFIG_PACKAGE_bind-host=y
CONFIG_PACKAGE_block-mount=y
CONFIG_PACKAGE_coremark=y
CONFIG_PACKAGE_coreutils-nohup=y
CONFIG_PACKAGE_ddns-scripts=y
CONFIG_PACKAGE_ddns-scripts_aliyun=y
CONFIG_PACKAGE_ddns-scripts_cloudflare.com-v4=y
CONFIG_PACKAGE_ddns-scripts_dnspod=y
CONFIG_PACKAGE_ddns-scripts_no-ip_com=y
# CONFIG_PACKAGE_dnsmasq is not set
CONFIG_PACKAGE_dnsmasq-full=y
CONFIG_PACKAGE_ethtool=y
CONFIG_PACKAGE_f2fs-tools=y
CONFIG_PACKAGE_fdisk=y
CONFIG_PACKAGE_gzip=y
CONFIG_PACKAGE_htop=y
CONFIG_PACKAGE_iftop=y
CONFIG_PACKAGE_losetup=y
CONFIG_PACKAGE_nano=y
CONFIG_PACKAGE_openssh-sftp-server=y
CONFIG_PACKAGE_pv=y
CONFIG_PACKAGE_python3=y
CONFIG_PACKAGE_stress=y
CONFIG_PACKAGE_triggerhappy=y
CONFIG_PACKAGE_unzip=y
CONFIG_PACKAGE_usb-modeswitch=y
CONFIG_PACKAGE_usbutils=y
CONFIG_PACKAGE_vim-fuller=y
CONFIG_PACKAGE_wpad-openssl=y
CONFIG_PACKAGE_wget=y
CONFIG_PACKAGE_zstd=y

CONFIG_PACKAGE_luci=y
CONFIG_PACKAGE_luci-app-arpbind=y
CONFIG_PACKAGE_luci-app-autoreboot=y
CONFIG_PACKAGE_luci-app-ddns=y
CONFIG_PACKAGE_luci-app-filebrowser=y
CONFIG_PACKAGE_luci-app-frpc=y
CONFIG_PACKAGE_luci-app-netdata=y
CONFIG_PACKAGE_luci-app-oled=y
CONFIG_PACKAGE_luci-app-samba4=y
CONFIG_PACKAGE_luci-app-ssr-plus=y
CONFIG_PACKAGE_luci-app-ttyd=y
CONFIG_PACKAGE_luci-app-unblockmusic=y
CONFIG_PACKAGE_luci-app-upnp=y
CONFIG_PACKAGE_luci-app-vsftpd=y
CONFIG_PACKAGE_luci-app-wol=y
CONFIG_PACKAGE_luci-app-xlnetacc=y
CONFIG_PACKAGE_luci-compat=y

```
