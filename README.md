# test

1.使用Git Bash生成证书

$ssh-keygen.exe -t rsa
2.切换到用户家目录的.ssh目录下

$cd ~/.ssh
3.列出目录下所有文件

$ ls
id_rsa  id_rsa.pub
4.查看文件内容

$ cat id_rsa.pub
5.把公钥id_rsa.pub的内容放置到github/gitlab上。

GitHub: 打开Github。点击用户图像-->Settings--SSH and GPG keys--New SSH
GitLab:
6.完成代码提交

#配置Git
git config --global user.email "you@example.com"
git config --global user.name "Your Name"

#克隆仓库代码
git clone git@github.com:su-cloud/devops.git


#切换到devops项目目录下
cd ~/Desktop/devops

# 增加修改的文件到暂存区
git add README.md

# 本地提交
git commit -m "增加说明" README.md

# 推送代码到远程仓库
git push
Pipeline 练习：

node {
   stage("拉取代码") {
       echo "拉取代码"
   }
   stage("代码编译") {
       echo "代码编译"
   }
   stage("单元测试") {
       echo "单元测试"
   }
   stage("代码质量检查") {
       echo "代码质量检查"
   }
}





#流水线的设计
##分支管理
-master分支：用于进行代码分布。
-Develop:	用于机场代码开发


##开发流程
1.开发人员使用Develop分支进行日常发开，提交到Develop分支，然后自动触发Jenkins流水线



##提交阶段流水线
目标：进行代码构建和质量扫描，提高代码质量
触发条件：开发push代码到develop分支
流程设计：
-拉去代码
-代码编译
-单元测试
-代码质量扫描
-邮件通知开发人员

流程的异常处理：邮件通知




##集成阶段流水线
目标：完成代码测试，生成制品，并上传到制品库
触发条件：项目负责人Merge代码到Master
流程设计：
-拉去代码
-代码编译
-单元测试
-质量扫描
-构建打包 
-上传到制品库（测试包）
-UAT环境部署审核
-部署到UAT环境
-自动化测试
-人工测试
-将制品标记为可生产部署





##部署阶段流水线
阶段目标：将制品从制品库拉去，直接部署到生产环境
触发条件：人工触发
流程设计：
-选择部署版本
-执行部署

