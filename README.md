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
**磁盘损坏修复:** 输入root用户密码--->fsck 损坏磁盘--->yes--->reboot

## Linux  
  
### 文件操作  
**权限:** 可读（r/2^2)---可写（w/2^1)---可执行（针对脚本文件x/2^0)  ---(-表示的没有任何权限)  
**文件的归属:** 拥有者（owner/u)---属于组(group/g)---其他人(other/o)  
**文件类型:** 文件(_)---目录(d)---连接(l) （软连接/硬连接）  
**文件详细说明:**
1. 第一部分：第一个代表文件的类型，后面分三组代表不同权限用户的权限（u/g/o)  
2. 第二部分：拥有者---属于组  
3. 文件的大小---文件的创建日期---文件的名称  
  
**显示当前目录:** pwd---切换目录：cd(文件夹有空格需要加上'')  
**显示当前目录下的文件:** ls/ls -l/ls -lt/ls -a/ls -at/ll/ll -al  
**特殊目录标识符:** 一个点.表示当前目录----两个点..表示父级目录  
**查看主机名称:** hostname---修改主机名称:hostname newname(重启后失效）  
**读取文件内容:** cat---cat /etc/sysconfig/network  
**编辑文件内容:** vi(i键进入编辑插入模式，esc键退出，:wq保存/q!不保存）---vi /etc/sysconfig/network  
**文件拷贝:** cp&nbsp;文件名&nbsp;目标位置（文件名/目录）---cp&nbsp;-r&nbsp;目录&nbsp;目录  
**改变文件的拥有者/所在组:** chown/chgrp&nbsp;用户名&nbsp;文件名(-R,--recursive递归，如果改变的是文件夹，其自己也需要同样的权限，在chown/chgrp后加上-R）---chown&nbsp;用户名:用户名&nbsp;文件名（第一个代表用户，第二个代表组)  
**删除文件:** rm&nbsp;-rf&nbsp;文件名  
**创建文件夹:** mkdir&nbsp;文件夹名(mkdir后面加-p可创建多级目录）  
**创建文件:** touch&nbsp;文件名---vi/vim&nbsp;文件名  
**追加内容:** echo "xxxx" >> 文件名  
**查看文件内容:** cat（全部内容）---more(翻页查看）---tail（文件末尾，通常与-f/-100f连用，ctrl+c退出)---head(文件开头）  
**文件的移动和重命名:** mv&nbsp;source&nbsp;target(source是要移动的文件或是文件夹，target是文件或者是文件夹，同目录则重命名，不同目录则移动，如果后加其它文件名或者是文件夹，则移动加重命名）  
**删除文件/文件夹:** rmdir&nbsp;文件夹(必须是空目录）---rm&nbsp;-rf&nbsp;source(最好是绝对路径，确定好才删除）  
**文件查找:** find ~ -name 文件名/文件夹名(当前目录)---find / -name 文件名/文件夹名(跟目录)---可以匹配正则表达式  
**创建连接:** ln -s 文件名/文件夹名 连接名(有-s是软连接，无-s是硬连接,相当于拷贝)(桌面快捷方式的目标位置: 桌面/连接名)  
  
### vi/vim快捷键  
**(查看模式下）**  
**删除光标所在行:** dd  
**保存文件内容:** ZZ  
**将光标处的字符给删除:** x  
**在光标下一行插入内容:** o  
  
 ### 用户操作  
#：表示root用户---$：普通用户  
**查看命令所在位置:** witch date  
**查看当前用户**: who/whoami  
**查看用户信息:** id  
**启用root用户:** sudo passwd root  
**root用户下新增普通用户:** useradd/adduser hehuan---设置密码:passwd hehuan123---用户目录:/home/hehuan(\~代替)  
**切换用户:** 切换到root用户:su root(获取权限,未获取环境变量;su - root(su)直接切换)---切换到普通用户:su hehuan(su - hehuan)  
**注销当前用户:** exit  
  
**用户权限改变**  
**命令查看:** man cmd_name  
**命令补全:** Tab  
**修改权限:** chmod(-R,--recursive递归，如果改变的是文件夹，其自己也需要同样的权限，在chmod后加上-R）  
1. chmod&nbsp;g-w&nbsp;文件名  
2. chmod&nbsp;(二进制数值/664） 
  
**设置普通用户的sudo权限:** su-->vi /etc/sudoers-->在第一行添加-->hehuan ALL=(root)NOPASSWD:ALL  
  
 ### IP及远程连接  
**ip配置:** 菜单虚拟机-->网络适配器-->设备状态-->启动是连接-->网络连接-->NAT模式  
**查看IP：ifconfig**---主要看网卡和IP地址---ping www.baidu.com进行检查  
**IP文件查看:** cd /etc/sysconfig/network-scripts/  
**更改为固定IP:** 图形界面-->右击-->edit connections-->网卡名-->点击-->ipv4 setting-->manual-->输入address、netmast、  
gateway-->apply-->disconnect-->connect-->最后是连不上网的，作为知识点练习  
**本机主机名host:** 0.0.0.0  
**是否安装ssh服务:** ps -e | grep ssh  
**安装ssh服务:** sudo apt-get install openssh-server  
**启动ssh服务:** /etc/init.d/ssh start  
  
**远程连接**  
**要素:** ip地址/用户名/密码/协议ssh  
**工具**    
1. **SecureCRT**---步骤：win7-->C：windows\System32\drivers\hosts-->localhost-->ip&nbsp;主机名&nbsp;域名  
-->secureCRT-->快速连接-->主机名-->用户名-->密码-->cat /etc/hosts-->root-->vi /etc/hosts-->ip&nbsp;主机名&nbsp;域名  
2. **远程FTP:** 主机/用户名/密码/端口（22）-->通过文件拖拽上传与下载  
3. **Notepad:** show-->setting-->profile setting-->addnew-->主机名/端口/用户名/密码-->进行连接  
-->**创建文件**-->touch readme.txt-->先VI命令添加随便添加一点点东西-->Notepad打开进行编辑保存  
**ultraEdit:** FTP帐号-->帐号管理-->帐号/协议/服务器/端口(22)/用户名/密码-->视图-->查看方式(可以根据不同的用处选择编辑模式） 
4. **远程界面工具:Xmanager4**-->Xbrowser-->new-->Xstart&nbsp;Session-->名称/主机名/协议/用户名/密码/  
-->Execution&nbsp;Command(选择最后一个）-->双击-->保存-->右击-->open in terminal  
  
## 系统管理  
**关机:** halt---重启：reboot/init 6(安全重启）（root用户下）  
**进入终端:** Ctrl+Alt+T  
**清除终端:** clear   
**查看系统:** uname---查看内核：uname&nbsp;-r  
**查看cpu:** cat&nbsp;/proc/cpuinfo  
**查看内存:** cat&nbsp;/proc/meminfo  
**显示磁盘的使用:** df&nbsp;-lh---du(显示当前目录下磁盘使用情况）---du&nbsp;-s/sh&nbsp;/home/hehuan(显示指定目录下磁盘剩余空间,s显示kb,sh显示M）  
**查看创建系统时磁盘的挂载情况:** fdisk&nbsp;-l(root用户下）---mount  
**修复磁盘:** fsck&nbsp;磁盘地址(自动修复)  
**挂载与卸载磁盘:** mount&nbsp;/dev/sda*&nbsp;/data---卸载磁盘:umount&nbsp;/dev/sda*(root用户下）  
**查看内存使用情况:** free/free&nbsp;-m(kb/M)  
**查看进程使用情况:** top(M详细情况)  
  
**防火墙**  
**查看防火墙状态:** sudo service iptables status  
**关闭防火墙:** sudo service iptables stop  
**启动临时防火墙:** sudo service iptables start（restar）  
**永久关闭/开启防火墙:** sudo chkconfig iptables off/on  
  
**另外一种方式**  
**查看防火墙状态:** sudo service httpd status  
**开启防火墙:** sudo service httpd start  
**永久关闭防火墙:** sudo chkconfig httpd off  
**查看防火墙永久状态:** sudo checkconfig --list|grep httpd(2,3,4,5是on即是开启）  
**给防火墙开启端口:** sudo ufw allow 22  
  
**SELINUX禁用**  
sudo vi /etc/sysconfig/selinux--->SELINUX=disabled  

  
## 软件安装  
1. RPM命令  
**检查软件是否安装:** rpm&nbsp;-qa|grep&nbsp;java  
**卸载已安装的软件:** rpm&nbsp;-e&nbsp;--nodeps&nbsp;java(多个软件中间用空格隔开）  
**安装软件:** rpm&nbsp;-ivh&nbsp;java.rpm  
2. tar软件（源码，编译,不推荐）  
**解压:** tar -zxvf xxx.tar.gz（到当前目录）---tar -zxvf xxxx.tar.gz -C dir（到指定目录）  
**压缩:** tar -zcvf xxx.tar.gz dir  
**安装软件:** bin/java  
**添加环境变量:** vi&nbsp;/etc/profile-->文件最后的位置插入-->export JAVA_HOME=（bin文件的父目录）-->换行-->export PATH=$PATH:$JAVA_HOME/bin/-->保存退出-->source /etc/profile(让目录生效）--echo $JAVA_HOME(进行查看)-->echo $PATH-->java-->java -version
3. zip软件  
**解压:** unzip xxx.zip---压缩：zip yy.zip file  
4. yum  
需要配置源---解决了软件包依赖关系以及各个软件的安装顺序  
5. deb  
sudo apt-get install -f  
sudo apt dpkg -i 应用全名  
sudo apt remove sogoupinyin
sudo apt install 依赖包  
输入法--->设置--->高级--->Fick设置--->只留搜狗和键盘-英语--->关闭--->保存  
  
**VMware Tools安装**  
**前置更新:**  sudo apt-get update ---> sudo apt-get install net-tools  
**挂载:** sudo mount  /dev/cdrom /media  
**复制解压:** cp /media/VMwareTools-9.6.4-2441333.tar.gz /tmp ---> tar -xzvf VMwareTools-9.6.4-2441333.tar.gz  
**安装:** cd vmware-tools-distrib ---> ./vmware-install.pl  
  
### Crontab  
每个用户都可以调度自己的任务  
**编辑:** crontab -e(选择编辑模式:select -editor)--->插入命令(每分钟执行一次)---> */1 * * * * /bin/date >> /home/hehuan/test.txt  
**查看:** crontab -l  
**删除:** crontab -r  
**基本格式:** \* \* \* \* \* command  
每个\*的含义:  
1. 分 1-59 \*/10  
2. 时 0-23 */2  
3. 日 1-31 
4. 月 1-12  
5. 星期 0-6 0代表星期天  
  
**例子**  
每天21:30执行---> 30 21 * * * cmd  
每个月1,11,21的2:30执行---> 30 2 1,11,21 * * cmd  
每周六或者每周日1:45执行---> 45 1 * * 6,0 cmd  
每天20:00至23:00,每半个小时执行一次---> 0,30 20-23 * * * cmd  
每一小时执行一次---> * */1 * * * cmd  

### shell编程  
sbin/hadoop-deamon.sh start namenode(.sh结尾的shell脚本,start namenode是位置参量)  
  
**什么是shell程序:**   
1. 文本形式,批量的linux命令集合,能被shell解释执行  
2. 由linux命令、shell命令、控制语句以及注释语句构成  
3. 纯文本文件,可用任意编辑器编写,通常以.sh作为后缀名  
  
**程序执行的方式**  
1. ./test.sh  
2. . test.sh  
3. sh test.sh  
  
**第一行:** 指定用哪个程序来编译和执行脚本---> #!/bin/bash或者#!/bin/sh  
**注释:** 使用#符号  
  
**变量:**  
**变量命名:** 必须以字母或下划线开头,后面可以跟字母、数字或者下划线,任何其他字符都标志变量名的结束.---变量名关于大小写敏感,变量类型不是那么重要  
  
**变量作用域:** 
1. **本地变量**:  只是在当前shell程序中可用
2. **全局环境变量:** ---> /etc/profile  
3. **用户环境变量:** --->vi  /home/hehuan/.bash_profile--->插入--->exprot name=hehuan--->source /home/hehuan/ .hash_profile--->echo ${name}  
 环境变量需要大写 ,如果父shell进程产生了子shell进程,则环境变量可被"继承"并复制  
   
**变量的赋值**  
等号两边不能有空格  
在等号后面跟一个换行符给变量赋空值  
举例:name=hehuan---echo $name / echo ${name} / echo "$name"  
清除变量: unset name  
显示所有变量: set  
a=${b:-c} --->解释: 如果b存在,a=b;如果b不存在,a=c,c相当与默认值  
  
**位置参量**  
- 是一组特殊的内置变量,通常被shell脚本用来从命令行接受参数,或被函数用来保存传递给它的参数  
- 执行shell脚本,用户可以通过命令行向脚本传递信息,跟在脚本名后面的用空格隔开的每个字符串都称为位置参量  
- 在脚本中使用这些参数,需要通过位置参量来引用,如$1表示第一个参数,数字也可以用花括号括起来,如${1},但从10开始必须用花括号括起来;  
-  ./test.sh $1 ${2},其中可以传递位置参量,也可以不传递   
  
**位置参数的含义** 
$0--->表示当前文件名---> **三种执行方式不结果不相同**---> ./test.sh(./test.sh)---> . test.sh(-bash)--->sh test.sh(test.sh)  
$1-$9  
$10  
$#--->实际的位置参数个数  
$*--->以单个字符显示所有位置参量  
$@--->未加双引号时与$*含义相同,加双引号时有区别  
$$--->脚本运行的当前进程号  
$!--->最后一个后台运行的进程的进程号  
**$?(退出码)**--->显示前面最后一个命令的退出状态,0表示没有错误,其他任何值表示有错误  
**注意:** 如果位置餐两种含有空格,需要使用双引号括起来  
  
**退出码**
- 任何命令进行时都会返回一个退出状态  
- 查看命令: echo $?  
- 应用中通常会在关键步骤后判定$?,以确定关键步骤的执行是否正常,尤其时调度系统里需要监控sh返回码  
- shell脚本的返回码取决于最后一个命令的返回码  
- 程序控制返回码: exit N--->退出状态为0,成功,无错误--->退出状态大于-,失败,某处有错误  
  
**数组**
赋值: arr=(one two three)  
输出一个: echo ${arr[0]} ---> 输出所有: echo ${arr[*]} ---> 输出个数: echo ${#arr[*]}  
修改值: arr[0]=modify  
  
**命令date**  
查看日期: date（显示当前日期时间）---date -R(显示时区）---cal 10 2017(显示某年某月日历）  
设置日期和时间: date -s 2017-08-28---date -s 07:11:52（root用户下）  
设置成当地时区: timedatectl set-local-rtc true 
赋值及格式: date1=$(date +%Y/%m%dT%H:%M:%S) --->输出: echo ${date1}  
两天前: date2=$(date --date='-2 days' +%Y-%m-%d) ---> 两天后: 将-2变成2(也可以用2 days ago)    
  
**判断(! 表示取反)**  
**注意**: 除了使用test之外,还可以用[ ](中括号),在bash的判断符号中括号的两端必须要有空格符来分隔,如[ -z "$Home" ]  
**文件是否存在:** test -e/-f/id filename (-e: 是否存在; -f: 是否存在且为为文件; -d: 是否存在且为目录)  
**判断权限状态(root权限有例外):** test -r/-w/-x filename (-r: 文件是否存在且有可读权限)  
**整数之间的判断**: test n1 -eq n2  
-eq ---> 两数值相等(equal)  
-ne ---> 两数值不等(not equal)  
-gt ---> n1大于n2(greater than)  
-lt --->n1小于n2(less than)  
-ge ---> n1大于等于n2(greater than or equal)  
-le ---> n1小于等于n2(less than or equal)  
  
**字符串判断**
test -z string ---> 字符串为0,及空字符串,则为true  
test -n string ---> 字符串不是空字符串,则为true,-n亦可省略  
test str1 =/== str2 ---> str1等于str2,则为true  
test str1 != str2 ---> str1不等于str2,则为true  
  
**if判断**  
**单层**: if [ 条件判断式 ];then  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;当条件判断式成立时,可以进行的指令工作内容;  
fi --->结束if的意思  
如果有多个条件要判断,可以将多个条件写入一个中括号,也可以用&&或||来隔开多个中括号  
**多重**  
在单层的基础上添加elif+else即可  
  
**循环**  
**第一种方式:**  
for var in 1 2 3 4 5  
do  
&nbsp;&nbsp;&nbsp;&nbsp;echo ${var}  
done  
**第二种方式:** (求0到9的累加)  
num=10  
s=0  
for((i=0;i<${num};i=i+1)) --->初始值;限制值;执行步阶  
do  
&nbsp;&nbsp;&nbsp;&nbsp;s=$((${s}+${i})) --->累加需要加两对括号
done  
  
**while do done**  
while [ condition ] --->满足条件循环执行程序段  
do  
&nbsp;&nbsp;&nbsp;&nbsp;程序段落  
done  
**until do done**  
until [ conditon ] --->满足条件停止执行程序段  
do  
&nbsp;&nbsp;&nbsp;&nbsp;程序段落  
done  
  
  **while read line  从文件或命令中逐行读取**    
  cat file | while read line  
  do  
  echo $line  
  done  
  **或**  
  cat `ls ./* .txt` | while read line  
  do  
  echo $line  
  done  

  



  




  














  

  






  




