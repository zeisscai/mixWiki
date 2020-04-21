# VPS  维护手册


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

定时重启的命令，使用定时重启可以一定程度上回复速度，但是在拥挤时用处并不太大。

crontab -e 指令进入编辑页面

在编辑的文件的最后加入


```
0 0 6,18 * * /sbin/reboot
```

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

依次配置版本，SSR密码，服务器端口，加密方式，协议，混淆方式，最后任意键安装。需要注意的是各个客户端对各种协议的支持情况。

市场化的 piecloud 常用的配置：
ip使用域名的形式
加密使用chacha20-ietf
协议使用auth_aes128_md5
协议参数：（混淆参数要使用域名的情况下才能有）
混淆：tls1.2_ticket_auth
混淆参数：support.apple.com

我使用的参数：
加密：chacha20
协议：auth_aes128_md5
混淆：tls1.2_ticket_auth
混淆参数：www.chinadailyasia.com


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

检查BBR是否开启：centos-6-x86_64-bbr，使用系统原生的BBR就可以有比较好的速度。

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
## 相关链接
有的需要配合梯子

[SSR一键安装脚本 (ShadowsocksR一键安装教程)](https://ssr.tools/31)

[搬瓦工方案库存监控页面](https://stock.bwg.net/)

[什么是 CN2 路线？怎么区分搬瓦工 VPS 是否走 CN2 路线](https://www.bandwagonhost.net/2522.html)

[搬瓦工 CN2 GT 方案和 CN2 GIA 方案的区别以及购买选择建议](https://www.bandwagonhost.net/1716.html)

[搬瓦工官网](http://bandwagonhost.com/) 这个和上面几篇文章推荐的网址不一样，这个网址需要梯子。

[Vultr，另外一家VPS商家](vultr.com)
