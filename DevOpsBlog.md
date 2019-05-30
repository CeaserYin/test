#流水线的设计
##分支管理
-master分支：用于进行代码分布。
-Develop:	用于机场代码开发


##开发流程
###1.开发人员使用Develop分支进行日常发开，提交到Develop分支，然后自动触发Jenkins流水线



##提交阶段流水线
###目标：进行代码构建和质量扫描，提高代码质量
###触发条件：开发push代码到develop分支
###流程设计：
####-拉去代码
####-代码编译
####-单元测试
####-代码质量扫描
####-邮件通知开发人员

##流程的异常处理：邮件通知




##集成阶段流水线
###目标：完成代码测试，生成制品，并上传到制品库
###触发条件：项目负责人Merge代码到Master
###流程设计：
####-拉去代码
####-代码编译
####-单元测试
####-质量扫描
####-构建打包 
####-上传到制品库（测试包）
####-UAT环境部署审核
####-部署到UAT环境
####-自动化测试
####-人工测试
####-将制品标记为可生产部署





##部署阶段流水线
###阶段目标：将制品从制品库拉去，直接部署到生产环境
###触发条件：人工触发
###流程设计：
###-选择部署版本
###-执行部署

#使用SaltStack 
##先做database pipeline 后做code pipeline
##将所有的一切纳入版本控制中

#数据库代码法则
##数据库Schema向后兼容
##修改Schema只增加不删除
##只新增不修改

##新代码上线
###使用新字段
###兼容旧字段内容

##回滚
##进行数据转换


#开源的数据库版本控制
##flyway

#部署流水线分步骤实施
##-对价值流进行建模并创建简单的可工作框架
##-将构建和部署流程自动化（效果明显）
##-将单位测试和代码分析自动化（质量分析）
##-将验收测试自动化（测试）
##-将分布自动化（业务）



#持续集成
##持续集成是一种软件开发实践，即团队开发成员经常集成他们的工作。







node {
   stage("拉取代码") {
       echo "拉取代码"
       git branch: 'develop', credentialsId: '237053ff-5317-4f3b-b106-b3b026006401', url: 'git@git.womaiyun.com:yinfei/devops-demo.git'
   }
   
    stage("单元测试") {
       echo "单元测试"
   }
   stage("构建打包") {
       echo "构建打包"
   }
   stage("上传制品库") {
       echo "上传制品库"
   }
   stage("SIT部署审核"){
       sh 'cat /etc/hosts'
   }
   stage("部署SIT环境"){
       sh 'cat /etc/hosts'
   }
   stage("自动化测试"){
       sh 'cat /etc/hosts'
   }
   stage("标记制品为可发布"){
       sh 'cat /etc/hosts'
   }
   
}



#1.安装并配置NFS
[root@linux-node1 ~]# yum install -y nfs-utils rpcbind
[root@linux-node1 ~]# mkdir -p /data/k8s-nfs
[root@linux-node1 ~]# vim /etc/exports
/data/k8s-nfs *(rw,sync,no_root_squash)

#启动NFS
[root@linux-node1 ~]# systemctl enable rpcbind nfs
[root@linux-node1 ~]# systemctl start rpcbind nfs

sh 'scp index.html root@42.96.135.81:/opt/yinfei'

#测试
##A/B 测试与灰度发布
##在普通的一个网页的在放一个数据采集的脚本

#灰度发布

##蓝绿部署与A/B TEST的区别

##蓝绿部署是 部署环境蓝，绿环境，两个环境，蓝是1.0版本用户正在使用。绿版本是新版本，将用户环境逐渐转换到绿环境。如果绿环境有问题立即转换到绿环境

##金丝雀发布，就分新老版本，将新版本发布给一小部分用户，看反应如果，如果效果好在全局发布。尽量避免故障造成的重大影响。

##灰度发布是对某一产品的发布逐步扩大使用群体范围。

##灰度发布目标：
###1.降低影响的用户范围。
###2.更早获得用户反馈，提升质量。
###3.让用户参与产品测试，互动。


##灰度策略：
###1.目标用户规模；
###2。回滚策略；
###3.部署策略。


##用户筛选：
###1.用户特征；
###2.用户数量。
###3.用户范围。

##发布系统：
###1.灰度发布系统；
###2.分布规则；
###3.数据分析-->动态调整分流规则


##总结报告：
###1.系统运行情况报告；
###2.用户行为分析报告。
###3.用户调查问卷；


##持续改进：
###1.根据总结形成产品改进方案；
###2.检查实施效果；
###3.停止无效方案；
###4.下一轮灰度发布或者完整发布；




#运维知识体系
##客户端层：
###1.浏览器；
###2.DNS；
###3.客户端/APP；

##外部层：
###1.第三方CDN;
###2.云计算；

##网络层：1.互联网层；
##接入层：



#自动化运维发展
##1.标准化运维
##2.Web化运维
##3.服务化



#自动化-数据化处理-AI


##安装并配置
###1.包管理工具；2.源码编译 3.二进制

##配置
###网络相关
###路径相关
###日志相关
###安装相关
###容量相关
###性能相关
###功能配置

##启动
###系统服务
###直接执行
###Nohup
###screen





##运维层次发展
###把服务运行起来 
####搭建服务 
####工程师

###让服务飞起来	
####用好服务	
####高级工程师

##自动化安装
cobbler-SALTASTACK-ZABBIX-Jenkins-elastic  

###基于cobbler的自动化安装
###基于Zabbix构建企业及监控平台
###ZABBIX之故障升级




##SALTASTACK(服务的配置管理)把所有的操作系统之上
###1.ANSIBLE开源的管理工具 被redhat收购了  
###2.puppetlab（ruby语音） 夕阳工具
###SALTSTACK ssh+agent	
###saltStack是一个新的基础平台管理工具，之需要花费数分钟即可运行起来，可以支撑管理上万台服务器的规模，数秒中即可完成数据传递。
###SaltStack是使用Python语音开发的，同时提供Rest API方便二次开发以及和其他平台进行集成。

##三种运行方式
###LOCAL
###Master/Minion （c/s结构）主控端是master 被控端是Minion
###Salt SSH  


##在linux下的salt操作
###停git，gitlab-ctl stop
###停jenkins ：systemctl stop jenkins 
###Nestat -nlp


##安装Saltack master
yum install https://mirrors.aliyun.com/saltstack/yum/redhat/salt-repo-latest-2.el7.noarch.rpm
sed -i "s/repo.saltstack.com/mirrors.aliyun.com\/saltstack/g" /etc/yum.repos.d/salt-latest.repo
yum install -y salt-master python-setproctitle
yum install salt-master salt-ssh salt-minion salt-cloud salt-api

###第一台装
hostnamectl set-hostname linux-node1.example.com	(修改主机名)
yum install https://mirrors.aliyun.com/saltstack/yum/redhat/salt-repo-latest-2.el7.noarch.rpm  （在阿里云上下载saltstack）
sed -i "s/repo.saltstack.com/mirrors.aliyun.com\/saltstack/g" /etc/yum.repos.d/salt-latest.repo （下载一个流管理工具，把当前文件下载到一个临时缓存区中）
yum install -y salt-master python-setproctitle
yum install -y salt-master salt-ssh salt-minion salt-cloud salt-api   （安装salt中的master方法包 ）


###第二台装
yum install -y  salt-minion



删除salt 
删除salt
yum remove salt-master salt-minion 这个是卸载

然后  rm -rf /etc/salt





LINUX命令
vim命令
set nu 显示行数
sz /etc/salt/minion 把文件传到windows桌面上

修改主机名
hostnamectl set-hostname linux-node1.example.com
hostnamectl set-hostname linux-node2.example.com




linux-node1的操作

#设置主机名
hostnamectl set-hostname linux-node1.example.com

#安装Salt master
yum install https://mirrors.aliyun.com/saltstack/yum/redhat/salt-repo-latest-2.el7.noarch.rpm
sed -i "s/repo.saltstack.com/mirrors.aliyun.com\/saltstack/g" /etc/yum.repos.d/salt-latest.repo
yum install salt-master salt-ssh salt-minion salt-cloud salt-api

#启动salt-master
systemctl start salt-master

#修改minion配置文件
vim /etc/salt/minion

#启动salt-minion
systemctl start salt-minion




#修改minion配置文件
vim /etc/salt/minion

#启动salt-minion
systemctl start salt-minion






salt '*' test.ping 查看master上minion是否链接成功

salt '*' test.ping  test是一个模块，ping是一种方法


用一个消息队列方式进行发布
master（使用4505端口）进行发布


请求与返回
master（4506端口）进行返回


状态管理



声明是管理
规则1 缩进
YAML “YAML不是一种标记语言”
YAML使用一个固定的缩进风格表示数据层结构关系。
Salt需要每个缩进级别由两个空格组成。
不要使用table
规则2冒号（所有的冒号都需要空格，除了以冒号结尾）
YAML my_key: my_value

规则3 列表 使用一个短横杠加一个空格。


vim /etc/salt/roster---salt的配置SSH文件
salt-ssh  '*' test.ping


salt '×' cmd.run 'df -h'



远程执行三大模块
目标，模块，返回
目标分为两种类型
