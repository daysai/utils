## 一键脚本安装Shadowsocks

* 系统支持：CentOS 6+，Debian 7+，Ubuntu 12+

* 内存要求：≥128M

## 使用方法

确保VPS能正常`ping ip`，然后`root`登陆VPS

```bash
ssh root@ip
```

一键安装脚本如下：

```bash
wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh
chmod +x shadowsocks-all.sh
./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
```

#### 卸载方法

```bash
./shadowsocks-all.sh uninstall
```

#### 启动脚本及配置文件

Shadowsocks-Python 版：

```bash
/etc/init.d/shadowsocks-python start | stop | restart | statu
/etc/shadowsocks-python/config.json
```

ShadowsocksR 版：

```bash
/etc/init.d/shadowsocks-r start | stop | restart | status
/etc/shadowsocks-r/config.json
```

Shadowsocks-Go 版：

```bash
/etc/init.d/shadowsocks-go start | stop | restart | status
/etc/shadowsocks-go/config.json
```

Shadowsocks-libev 版：

```bash
/etc/init.d/shadowsocks-libev start | stop | restart | status
/etc/shadowsocks-libev/config.json
```

> 对应 启动，停止，重启，查看状态。

版本变更等具体信息可见：\[[https://teddysun.com/486.html\]\(https://teddysun.com/486.html\](https://teddysun.com/486.html]%28https://teddysun.com/486.html\)\)
