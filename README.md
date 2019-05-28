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
现在11