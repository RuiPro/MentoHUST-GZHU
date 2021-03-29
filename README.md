# mentohust
在网上下载的mentohust不一定能够在GZHU进行认证，但是这个版本可以
适用于MT7620系列处理器，也就是mips64架构的处理器才能够使用。

### 使用方法：

1、将[mentohust](bin/mentohust)上载到\bin\中

2、将配置文件[mentohust.conf](etc/)上载到\etc\中（当然你也可以跳过这一步，让他自己生成配置文件）

* 如果你跳过了第二步，请先启动再关闭一次生成一次配置文件：
```
mentohust
mentohust -k
```

3、用SSH软件登录路由器后台

4、编辑配置文件
你可以直接连接scp对/etc/mentohust.conf进行编辑
也可以连接ssh进行配置（别忘了wq!）：
```
cd /etc
vi mentohust.conf
```

* 配置文件说明：[配置清单.txt](/)

修改完成配置后，即可在后台运行：
```
mentohust -b 1
```

### 注意事项：
* 输入：mentohust -h可查看帮助

* 在路由器管理界面确认wan口是否为DHCP客户端模式

### 自启动：

将[mentohust](/etc/init.d)上传至/etc/init.d目录下，设置文件权限为0755。登录luci后台，在系统-启动项下找到mentohust启动即可

### 多拨：
* 此方式需要你的固件支持虚拟wan！

如果你的路由器没有这个服务且ROM空间充足，你可以通过安装软件包来实现。

①你可以通过后台通过命令来安装：

```
opkg updata
opkg -force-checksum install luci-app-syncdial
```
②也可以在luci后台-系统-软件包搜索syncdial进行安装。

③更多地，你可以直接上传本地软件包进行安装。

安装成功后，你可以在luci后台-网络中找到虚拟wan


在虚拟wan目录下，设置虚拟wan数量为1，勾选使用旧的macvlan创建方式，然后开启
* 进过测试，gzhu通过设置3个虚拟wan口网速最高可达到11mb/s下载，1.1mb/上传，但非常不稳定，且经常掉ping。比较稳定的虚拟wan个数是1，也就是双拨。尽管如此，掉ping的现象仍然存在(待研究）

开启虚拟wan后，在网络-接口页面可以看到多出来一个VWAN1(网卡为macvlan1)，设置该接口为dhcp客户端模式，并应用。

接着SSH登录路由器后台，
```
mentohust -u账号 -p密码 -daemonize1 --pid-file none -nmacvlan1
```
等到弹出余额过一会即可多拨成功

* 多拨不能开机自启，必须手动配置Vwan
* 可以使用top命令来查看进程，也可以随时kill pid


