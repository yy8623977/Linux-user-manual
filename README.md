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
  
### 文件操作  
**权限~**可读（r/2^2)---可写（w/2^1)---可执行（针对脚本文件x/2^0)  ---(-表示的没有任何权限)  
**文件的归属~**拥有者（owner/u)---属于组(group/g)---其他人(other/o)  
**文件类型~**文件(_)---目录(d)---连接(l) （软连接/硬连接）  
**文件详细说明~**
1. 第一部分：第一个代表文件的类型，后面分三组代表不同权限用户的权限（u/g/o)  
2. 第二部分：拥有者---属于组  
3. 文件的大小---文件的创建日期---文件的名称  
  
**显示当前目录~**pwd---切换目录：cd(文件夹有空格需要加上'')  
**显示当前目录下的文件~**ls/ls&nbsp;-l/ll/ls&nbsp;-lt/ls&nbsp;-a/ls&nbsp;-at  
**特殊目录标识符~**一个点.表示当前目录----两个点..表示父级目录  
**查看主机名称~**hostname---修改主机名称:hostname newname(重启后失效）  
**读取文件内容~**cat---cat /etc/sysconfig/network  
**编辑文件内容~**vi(i键进入编辑插入模式，esc键退出，:wq保存/q!不保存）---vi /etc/sysconfig/network  
**文件拷贝~**cp&nbsp;文件名&nbsp;目标位置（文件名/目录）---cp&nbsp;-r&nbsp;目录&nbsp;目录  
**改变文件的拥有者/所在组~**chown/chgrp&nbsp;用户名&nbsp;文件名(-R,--recursive递归，如果改变的是文件夹，其自己也需要同样的权限，在chown/chgrp后加上-R）---chown&nbsp;用户名:用户名&nbsp;文件名（第一个代表用户，第二个代表组)  
**删除文件~**rm&nbsp;-rf&nbsp;文件名  
**创建文件夹~**mkdir&nbsp;文件夹名(mkdir后面加-p可创建多级目录）  
**创建文件~**touch&nbsp;文件名---vi/vim&nbsp;文件名  
**追加内容~**echo&nbsp;"xxxx"&nbsp;>>&nbsp;文件名  
**查看文件内容~**cat（全部内容）---more(翻页查看）---tail（文件末尾，通常与-f/-100f连用，ctrl+c退出)---head(文件开头）  
**文件的移动和重命名~**mv&nbsp;source&nbsp;target(source是要移动的文件或是文件夹，target是文件或者是文件夹，同目录则重命名，不同目录则移动，如果后加其它文件名或者是文件夹，则移动加重命名）  
**删除文件/文件夹~**rmdir&nbsp;文件夹(必须是空目录）---rm&nbsp;-rf&nbsp;source(最好是绝对路径，确定好才删除）  
**文件查找~**find ~ -name 文件名/文件夹名(当前目录)---find / -name 文件名/文件夹名(跟目录)---可以匹配正则表达式  
**创建连接~**ln -s 文件名/文件夹名 连接名(有-s是软连接，无-s是硬连接,相当于拷贝)  
  
### vi/vim快捷键  
**(查看模式下）**  
**删除最光标所在行~**dd  
**保存文件内容~**ZZ  
**将光标处的字符给删除~**x  
**在光标下一行插入内容~**o  
  
 ### 用户操作  
#：表示root用户---$：普通用户  
**查看用户信息~**id  
**启用root用户~**sudo passwd root  
**root用户下新增普通用户~**useradd hehuan---设置密码:passwd hehuan123---用户目录:/home/hehuan(\~代替)  
**切换用户~**切换到root用户:su root(获取权限,未获取环境变量;su - root(su)直接切换)---切换到普通用户:su hehuan(su - hehuan)  
**注销当前用户~**exit  
  
**用户权限改变**  
**命令查看~**man cmd_name  
**命令补全~**Tab  
**修改权限~**chmod(-R,--recursive递归，如果改变的是文件夹，其自己也需要同样的权限，在chmod后加上-R）  
1. chmod&nbsp;g-w&nbsp;文件名  
2. chmod&nbsp;(二进制数值/664） 
  
**设置普通用户的sudo权限~**su-->vi /etc/sudoers-->在第一行添加-->hehuan ALL=(root)NOPASSWD:ALL  
  
 ### IP及远程连接  
**ip配置~**菜单虚拟机-->网络适配器-->设备状态-->启动是连接-->网络连接-->NAT模式  
**查看IP：ifconfig**---主要看网卡和IP地址---ping www.baidu.com进行检查  
**IP文件查看~**cd /etc/sysconfig/network-scripts/  
**更改为固定IP~**图形界面-->右击-->edit connections-->网卡名-->点击-->ipv4 setting-->manual-->输入address、netmast、  
gateway-->apply-->disconnect-->connect-->最后是连不上网的，作为知识点练习  
**本机主机名host~**0.0.0.0  
  
**远程连接**  
**要素~**ip地址/用户名/密码/协议ssh  
**工具~**    
1. **SecureCRT**---步骤：win7-->C：windows\System32\drivers\hosts-->localhost-->ip&nbsp;主机名&nbsp;域名  
-->secureCRT-->快速连接-->主机名-->用户名-->密码-->cat /etc/hosts-->root-->vi /etc/hosts-->ip&nbsp;主机名&nbsp;域名  
2. **远程FTP~**主机/用户名/密码/端口（22）-->通过文件拖拽上传与下载  
3. **Notepad~**show-->setting-->profile setting-->addnew-->主机名/端口/用户名/密码-->进行连接  
-->**创建文件**-->touch readme.txt-->先VI命令添加随便添加一点点东西-->Notepad打开进行编辑保存  
**ultraEdit~**FTP帐号-->帐号管理-->帐号/协议/服务器/端口(22)/用户名/密码-->视图-->查看方式(可以根据不同的用处选择编辑模式） 
4. **远程界面工具:Xmanager4**-->Xbrowser-->new-->Xstart&nbsp;Session-->名称/主机名/协议/用户名/密码/  
-->Execution&nbsp;Command(选择最后一个）-->双击-->保存-->右击-->open in terminal  
  
## 系统管理  
**关机~**halt---重启：reboot/init 6(安全重启）（root用户下）  
**进入终端~**Ctrl+Alt+T  
**清除终端~**clear  
**查看日期~**date（显示当前日期时间）---date&nbsp;-R(显示时区）---cal&nbsp;2017(显示某年日历）  
**设置日期和时间~**date&nbsp;-s&nbps;2017-08-28---date&nbsp;-s&nbps;07:11:52（root用户下）  
**查看系统~**uname---查看内核：uname&nbsp;-r  
**查看cpu~**cat&nbsp;/proc/cpuinfo  
**查看内存~**cat&nbsp;/proc/meminfo  
**显示磁盘的使用~**df&nbsp;-lh---du(显示当前目录下磁盘使用情况）---du&nbsp;-s/sh&nbsp;/home/hehuan(显示指定目录下磁盘剩余空间,s显示kb,sh显示M）  
**查看创建系统时磁盘的挂载情况~**fdisk&nbsp;-l(root用户下）---mount  
**修复磁盘~**fsck&nbsp;磁盘地址(自动修复)  
**挂载与卸载磁盘~**mount&nbsp;/dev/sda*&nbsp;/data---卸载磁盘:umount&nbsp;/dev/sda*(root用户下）  
**查看内存使用情况~**free/free&nbsp;-m(kb/M)  
**查看进程使用情况~**top(M详细情况)  
  
**防火墙~**
  
## 软件安装  
1. RPM命令  
**检查软件是否安装~**rpm&nbsp;-qa|grep&nbsp;java  
**卸载已安装的软件~**rpm&nbsp;-e&nbsp;--nodeps&nbsp;java(多个软件中间用空格隔开）  
**安装软件~**rpm&nbsp;-ivh&nbsp;java.rpm  
2. tar软件（源码，编译,不推荐）  
**解压~**tar -zxvf xxx.tar.gz（到当前目录）---tar -zxvf xxxx.tar.gz -C dir（到指定目录）  
**压缩~**tar -zcvf xxx.tar.gz dir  
**安装软件~**bin/java  
**添加环境变量~**vi&nbsp;/etc/profile-->文件最后的位置插入-->export JAVA_HOME=（bin文件的父目录）-->换行-->export PATH=$PATH:$JAVA_HOME/bin/-->保存退出-->source /etc/profile(让目录生效）--echo $JAVA_HOME(进行查看)-->echo $PATH-->java-->java -version
3. zip软件  
**解压~**unzip xxx.zip---压缩：zip yy.zip file  
4. yum  
需要配置源---解决了软件包依赖关系以及各个软件的安装顺序  
  






  




