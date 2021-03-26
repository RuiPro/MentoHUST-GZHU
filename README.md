# mentohust
在网上下载的mentohust不一定能够在GZHU进行认证，但是这个版本可以
适用于MT7620系列处理器，也就是mips64架构的处理器才能够使用。
### 使用方法：

1、将[mentohust](bin/mentohust)上载到\bin\中

2、将配置文件[mentohust.conf](etc/)上载到\etc\中（当然你也可以跳过这一步，让他自己生成配置文件）

*如果你跳过了第二步，请先启动再关闭一次生成一次配置文件：
```
mentohust
mentohust -k
```

配置清单

3、用SSH软件登录路由器后台

4、编辑配置文件
你可以直接连接scp对/etc/mentohust.conf进行编辑
也可以连接ssh：
```
cd /etc
vi mentohust.conf
```
进行配置（别忘了wq!）


修改完成配置后，即可运行：
```
mentohust -b 1
```


### 注意事项：
* 输入：mentohust -h可查看帮助

* 在路由器管理界面确认wan口是否为DHCP客户端模式
