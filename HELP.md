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


## 集成`openclash`源码
src-git openclash https://github.com/vernesong/OpenClash.git


## `openclash` 依赖包
>>> 
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


## 出现问题
1. clash不能启动，提示libcap版本不一致


## 是否需要增加
```shell script
          echo "CONFIG_PACKAGE_dnsmasq-full=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_dnsmasq_full_dhcp=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_dnsmasq_full_dhcpv6=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_dnsmasq_full_dnssec=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_dnsmasq_full_auth=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_dnsmasq_full_ipset=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_dnsmasq_full_conntrack=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_dnsmasq_full_noid=y" >> configs/config_rk3328
          echo "CONFIG_PACKAGE_dnsmasq_full_tftp=y" >> configs/config_rk3328

```
