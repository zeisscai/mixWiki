# VPS  维护手册

[TOC]

## 登录VPS

```
ssh -p ?? root@??
```

*输入password时输入的信息不会有任何显示*

更改换VPS密码

```
passwd root
```

*如果重新安装了系统，需要使用下面的命令重置本地存储的密钥。*
ssh-keygen -R ??

## 脚本安装SSR

### 四合一脚本的三个命令

搬瓦工最佳操作系统：centos-6-x86_64-bbr，使用系统原生的BBR就可以有比较好的速度。

```
wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh
```

```
chmod +x shadowsocks-all.sh
```

```
./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
```

### wget

如果提示找不到wget,则说明系统中没有安装wget，运行下面的命令安装*

CentOS

```
yum -y install wget
```

Ubuntu/Debian

```
apt-get -y install wget
```

### 配置

依次配置版本，SSR密码，服务器端口，加密方式，协议，混淆方式，最后任意键安装。

### SSR常用命令

```
启动SSR：
/etc/init.d/shadowsocks-r start
退出SSR：
/etc/init.d/shadowsocks-r stop
重启SSR：
/etc/init.d/shadowsocks-r restart
SSR状态：
/etc/init.d/shadowsocks-r status
卸载SSR：
./shadowsocks-all.sh uninstall
修改SSR配置文件：
nano /etc/shadowsocks.json
```

## BBR命令

检查BBR是否开启

```
sysctl net.ipv4.tcp_congestion_control
```

net.ipv4.tcp_congestion_control = bbr
说明启动

一键安装脚本

```
wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh && chmod +x bbr.sh && ./bbr.sh
```

## V2RAY

```
wget -N --no-check-certificate https://raw.githubusercontent.com/FunctionClub/V2ray.Fun/master/install.sh && bash install.sh
```

