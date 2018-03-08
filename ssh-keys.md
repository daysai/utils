## 暴力破解查看命令

```bash
grep "Failed password for invalid user" /var/log/secure | awk '{print $13}' | sort | uniq -c | sort -nr | more
```

## 本地安装ssh-key

```bash
ssh-keygen -t rsa
```

或者安全性更高的

```bash
ssh-keygen -t rsa -b 4096
```

> 确保`~/.ssh/id_rsa`文件备份，一旦丢失不可恢复！！！

可以通过\[[https://my.vultr.com/sshkeys](https://my.vultr.com/sshkeys/)\]\([https://my.vultr.com/sshkeys](https://my.vultr.com/sshkeys/)\)地址复制密钥内容，方便后续VPS实例的初始化

复制内容，可以通过命令

```bash
cat ~/.ssh/id_rsa.pub
```

> 复制内容到VPS的"Add SSH Key"中

#### 新实例安装

```bash
scp ~/.ssh/id_rsa.pub root@ip:
mkdir ~/.ssh
touch ~/.ssh/authorized_keys
cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

> 移动公钥文件到VPS的`~/.ssh/authorized_keys`路径下，更改文件权限

#### 修改sshd\_config配置文件

```bash
RSAAuthentication yes #RSA认证
PubkeyAuthentication yes #开启公钥验证
AuthorizedKeysFile .ssh/authorized_keys #验证文件路径
PasswordAuthentication no #禁止密码认证
PermitEmptyPasswords no #禁止空密码
```

> 主要是禁止密码认证`PasswordAuthentication`

#### 重启SSH服务

centos7

```bash
systemctl restart sshd
```

centos6

```bash
/etc/init.d/sshd restart
```

#### 多台电脑共用SSH

主要是复制密钥文件，文件路径`~/.ssh`

mac下查看系统权限命令

```bash
ls -l
```

更改`id_rsa.pub`文件权限命令

```bash
chmod 664 id_rsa.pub
```

> id\_rsa.pub文件权限为664，id\_rsa文件权限只能是60



