# Linux
## 用户管理  
- 创建  
  useradd [选项] {username}  
  创建一个普通用户，其家目录是在/tedu/jerry，主组root,附加组tom,adm。  
  			useradd -d /tedu/jerry -m -g root -G tom,adm jerry
  执行用户的shell程序为/bin/sh，UID为80000  
        useradd -s /bin/sh -u 80000 test1
  创建伪用户：
        useradd -s /sbin/nologin test3
- 修改  
  usermod [选项] {UserName}  
- 删除  
  userdel [选项] {UserName}  
- 密码管理  
  passwd [选项] {UserName}
- 用户身份切换  
  su {username}  
  su -{username}
## 用户组的增删改  
- 创建  
  groupadd [选项] {groupName}
- 修改  
  groupmod [选项] {groupName}
- 删除  
  groupdel {groupName}
- 用户组的切换  
  newgrp {GroupName}
## 权限  
- 逻辑权限   
  1. rwx读写执行，每三个权限为一组，共三组（user/group/other）。
  2. 修改文件/夹的权限 chmod
  3. 改变文件的所有者 chown
- 物理权限  
  1. chattr [选项] file/dir
  2. lsattr [选项] 文件/夹 
- 普通用户的root权限    
  vim /root/sudoers
## 挂载  
- 挂载  
  mount 文件系统 目录（挂载点）
- 取消挂载  
  umount 挂载点  
## 网络地址  
- IP地址
- 子网掩码
- 网关
- DNS
- DNS分类  
1. 静态  
  优点：可以使我们PC/服务器有一个更快的解析速度。维护方式是手动配置服务器上hosts文件。  
  缺点：hosts一般都是为本机系统所有，维护一台服务器还好说。如果是上千台集群，那么维护的工作很困难  
2. 动态  
  优点：只需要给服务器指明DNS服务器地址即可，无需手动配置hosts文件。  
  缺点：有一定响应时间，(延迟)。若DNS服务器宕机，那么我们就立即失去访问域名的能力。
 ## NAT和桥接的优缺点  
 - 桥接    
 优点：同一个局域网中的任意一台物理机想要访问虚拟机时，只要拥有账户和密码，就可以直接进行通信。  
 缺点：如果宿主主机没有连接网络，那么虚拟机也就不存在与该真实网络环境中，换句话，虚拟机使用桥接模式的时候，它的网络依赖于宿主的网络环境。  
 - NAT  
 优点：可以无视物理机(宿主主机)网络环境。即便是物理机没有网络，也不影响本机和虚拟机进行通信，也不影响本机上的其他虚拟机之间互相通信。因为虚拟机真正通信网卡是VMNet8提供(网络环境)  
 缺点：其他物理机想要访问NAT模式下的虚拟机时，比较麻烦。  
## 其它网络知识  
- 远程拷贝  
1. 从本机拷贝数据到远程的服务器上  
scp [-r] [path]/fie | dir  {UserName}@Host_IP:/[path]  
2. 从远程服务器上拷贝数据到本机  
scp {UserName}@Host_IP:/[path]/file  /[path]
- 登录远程服务器  
ssh root@192.168.89.128
## SSH免密登录
- 证书生成  
ssh-keygen
- 证书注册  
ssh-copy-id {UserName}@Host_IP
## Linux自带下载工具
- **wget**支持断点下载功能.同时支持FTP和HTTP下载方式.支持代理服务器  
	使用wget -O下载并以不同的文件名保存  
wget -O NewName.new  http://www.tedu.cn
## 进程
- 静态查询[ps]  
查询特定进程  
ps -aux | grep  sshd
- 动态查询 
每秒刷新一次top，以批次输出5次。  
top -d 1 -b -n 5  >> top.log
- 进程管理
  单进程管理  
  语法：kill  信号量 PID  
  多进程管理  
  语法：killall 信号量 程序名/命令名
## 系统资源监控
- free：内存监控
- uname:查阅系统与核心相关信息  
- uptime：观察系统启动时间与工作负载  
- netstat：网络监控  
- vmstat :侦测系统资源变化  
- Linux防火墙：  
  临时处理防火墙：如果系统重启，那么防火墙将恢复到之前的状态。  
  开启： service iptables start or /etc/init.d/iptables start  
  关闭： service iptables stop or /etc/init.d/iptables stop  
  重启： service iptables restart or /etc/init.d/iptables restart  
  查看： service iptables status	or /etc/init.d/iptables status  
  永久处理防火墙：(需重启系统后才能生效)  
  开启：	chkconfig iptables on  
	查看状态	chkconfig iptables --list  
	关闭：	chkconfig iptables off
## 任务管理
- 查看后台任务
- 将前台任务放置后台暂停
- 如何运行任务时，使其在后台运行 
- 如何将后台任务调至前台
- 如何将后台任务修改为运行状态
- 终止job




