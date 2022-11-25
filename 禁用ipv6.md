打开 /etc/sysctl.conf 然后添加以下内容：

```bash
vi /etc/sysctl.conf

net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6=1
```

运行以下命令：

```bash
sysctl -p
```

上一步已经禁用了 IPv6，但是重启后会复原。要想重启后也禁用，则必须做这一步。

```bash
vim /etc/rc.local
```

填入内容：

```bash
#!/bin/bash
# /etc/rc.local
/etc/sysctl.d
/etc/init.d/procps restart
exit 0
```

授权文件可执行：

```bash
chmod 755 /etc/rc.local
```

重启后执行` ip a `验证，无ipv6代表成功。

------
[1]: https://zhuji.gd/7210.html	"参考文献"

