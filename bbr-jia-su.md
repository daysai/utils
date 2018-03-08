## Google BBR 一键安装脚本

```bash
wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh
chmod +x bbr.sh
./bbr.sh
```

> 安装完成后会自动提示重启VPS

#### 验证脚本

```bash
uname -r
```

> 此命令查看内核版本

```bash
sysctl net.ipv4.tcp_available_congestion_contro
sysctl net.ipv4.tcp_congestion_control
sysctl net.core.default_qdisc
lsmod | grep bbr
```

> 这些命令结果包含bbr即可说明安装成功并已启动





