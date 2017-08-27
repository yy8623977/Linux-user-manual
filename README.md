# Linux-user-manual  
  
## Hadoop前置课程  
- Linux系统
- Java语言，JSE相关知识
- Mysql基本的DML和DDL

## CentOs 6.4版本  64位 安装 
http://archive.cloudera.com/cdh5/  
Hadoop支持debian(CentOS)、redhat、Sles、ubuntu,用的多的是redhat(CentOS),其次是Sles  
  
**虚拟化工具：VMWare**   
安装VMWare  
新建虚拟机  
安装CentOS 6.4操作系统 

## Linux  
**关机:**halt---重启：reboot/init 6(安全重启）（root用户下）  
**进入终端:**Ctrl+Alt+T  
**清除终端:**clear  
  
**文件操作**  
**权限:**可读（r/2^2)---可写（w/2^1)---可执行（针对脚本文件x/2^0)  ---(-表示的没有任何权限）  
**文件的归属:**拥有者（owner/u)---属于组(group/g)---其他人(other/o)
**文件类型:**文件(_)---目录(d)---连接(l)  
**文件详细说明:**
1. 第一部分：第一个代表文件的类型，后面分三组代表不同权限用户的权限（u/g/o)  
2. 第二部分：拥有者---属于组  
3. 文件的大小---文件的创建日期---文件的名称  
**显示当前目录:**pwd---切换目录：cd  
**显示当前目录下的文件:**ls/ls&nbsp;-l/ll/ls&nbsp;-lt/ls&nbsp;-a/ls&nbsp;-at  
**特殊目录标识符:**一个点.表示当前目录----两个点..表示父级目录  
**查看主机名称:**hostname---修改主机名称:hostname newname(重启后失效） 
**读取文件内容:**cat---cat /etc/sysconfig/network  
**编辑文件内容:**vi(i键进入编辑插入模式，esc键退出，:wq保存/q!不保存）---vi /etc/sysconfig/network
  
#：表示root用户---$：普通用户  
**启用root用户:**sudo passwd root  
**root用户下新增普通用户:**useradd hehuan---设置密码：passwd hehuan123---用户目录:/home/hehuan(~代替）   
**切换用户:**切换到root用户：su root(获取权限，未获取环境变量;su - root(su)直接切换)---切换到普通用户：su hehuan（su - hehuan)  
  
**ip配置:**菜单虚拟机-->网络适配器-->设备状态-->启动是连接-->网络连接-->NAT模式  
**查看IP：ifconfig**---主要看网卡和IP地址---ping www.baidu.com进行检查  
**更改为固定IP:**图形界面-->右击-->edit connections-->网卡名-->点击-->ipv4 setting-->manual-->输入address、netmast、  
gateway-->apply-->disconnect-->connect-->最后是连不上网的，作为知识点练习  
  
**远程连接**  
**要素:**ip地址/用户名/密码/协议ssh  
**工具:**    
1. **SecureCRT**---步骤：win7-->C：windows\System32\drivers\hosts-->localhost-->ip&nbsp;主机名&nbsp;域名  
-->secureCRT-->快速连接-->主机名-->用户名-->密码-->cat /etc/hosts-->root-->vi /etc/hosts-->ip&nbsp;主机名&nbsp;域名  
2. **远程FTP:**主机/用户名/密码/端口（22）-->通过文件拖拽上传与下载  
3. **Notepad**show-->setting-->profile setting-->addnew-->主机名/端口/用户名/密码-->进行连接  
-->**创建文件**-->touch readme.txt-->先VI命令添加随便添加一点点东西-->Notepad打开进行编辑保存  
**ultraEdit:**FTP帐号-->帐号管理-->帐号/协议/服务器/端口(22)/用户名/密码-->视图-->查看方式(可以根据不同的用处选择编辑模式） 
4. **远程界面工具:Xmanager4**-->Xbrowser-->new-->Xstart&nbsp;Session-->名称/主机名/协议/用户名/密码/  
-->Execution&nbsp;Command(选择最后一个）-->双击-->保存-->右击-->open in terminal

  




