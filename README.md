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

### BBR

```
wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh

chmod +x bbr.sh

./bbr.sh
```

> 接着按任意键，开始安装，坐等一会。安装完成一会之后它会提示我们是否重新启动vps，我们输入 y 确定重启服务器。重新启动之后。输入

```
lsmod | grep bbr
```

> 如果看到 tcp\_bbr 就说明 BBR 已经启动了

#### 启动脚本及配置文件

Shadowsocks-Python 版：

```bash
/etc/init.d/shadowsocks-python start | stop | restart | status
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

多个rsa认证配置

```
cd .ssh
ssh-keygen -t rsa -C "你的邮箱地址"
```

已有rsa会弹出

```
Enter file in which to save the key (/Users/admin/.ssh/id_rsa):
```

输入不同名字进行区分

修改`.ssh/config`配置

```
Host github.com
User admin
IdentityFile ~/.ssh/github_rsa

Host code.csdn.net
User admin
IdentityFile ~/.ssh/id_rsa
```

版本变更等具体信息可见: [https://teddysun.com/486.html](https://teddysun.com/486.html)

