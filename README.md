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
**进入终端:**Ctrl+Alt+T  
**清除终端:**clear
   
#：表示root用户---$：普通用户  
**启用root用户:**sudo passwd root  
*root用户下新增普通用户:**useradd hehuan---设置密码：passwd hehuan123  
**切换用户:**切换到root用户：su root(获取权限，未获取环境变量;su - root(su)直接切换)---切换到普通用户：su hehuan（su - hehuan)  
  
  
**ip配置:**菜单虚拟机-->网络适配器-->设备状态-->启动是连接-->网络连接-->NAT模式  
**查看IP：ifconfig**---主要看网卡和IP地址---ping www.baidu.com进行检查  
**更改为固定IP:**图形界面-->右击-->edit connections-->网卡名-->点击-->ipv4 setting-->manual-->输入address、netmast、  
gateway-->apply-->disconnect-->connect-->最后是连不上网的，作为知识点练习   
  




