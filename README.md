# mentohust
在网上下载的mentohust不一定能够在GZHU进行认证，但是这个版本可以
适用于MT7620系列处理器，也就是mips64架构的处理器才能够使用。
### 使用方法：
1、将[mentohust](bin/mentohust)上载到\bin\中

2、将配置文件[mentohust.conf](etc/)上载到\etc\中（当然你也可以跳过这一步，让他自己生成配置文件）

3、用SSH软件登录后直接输入
```
mentohust
```
开始引导配置

### 注意事项：
* 输入：mentohust -h可查看帮助

* 若没有上载此处的conf文件，可能需要手动修改DHCP脚本为
```
udhcpc -i eth0.2
```
* 在路由器管理界面确认wan口是否为DHCP客户端模式

* 正常使用后可在路由器启动项的exit上方加入
```
mentohust -w -u 用户名 -p 密码
```
即可把mentohust加入启动项
