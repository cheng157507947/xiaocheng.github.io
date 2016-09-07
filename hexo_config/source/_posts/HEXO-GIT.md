---
title: HEXO+GIT
date: 2016-09-07 14:13:51
tags:
---

记录当前部署博客部署步骤及问题。

# 环境准备
### GIT环境部署：[GIT-DOWNLOAD](https://git-scm.com/download/win)
需配置GIT用户及SSH KEYS
```bash
# 设置本机SSH KEYS
$ ssh-keygen -t rsa -C "邮件地址@youremail.com"

# 测试连接
$ ssh -T git@github.com

# 设置本机用户
$ git config --global user.name "joryhe"
$ git config --global user.email  "1032473410@qq.com"
```

### HEXO环境部署
```bash
# 安装
$ npm install -g hexo

# 初始化
$ hexo init
```

### HEXO常用命令
```bash
#清除hexo编译文件
$ hexo clean
#编译hexo静态文件
$ hexo g
#本地测试（可无debug）
$ hexo s --debug
```

### HEXO部署
1.修改hexo文件夹下主配置文件_config.yml
```bash
deploy:
  type: git
  repository: git@github.com:你的repository名字/你的repository名字.github.io.git
  branch: master
```
```bash
$ hexo deploy
```
注：该步骤由于各种错误尚未跑通，目前采用第二种方法

### HEXO插件
```bash
#GIT插件
$ npm install hexo-deployer-git --save

# RSS插件
npm install hexo-generator-feed --save
```

2.hexo文件夹下的public文件夹为编译完成的静态页面，直接将此文件夹下的所有文件上传至git工程master分支下即可。（每次需更新文件重新提交）

# 主题及源文件管理
目前使用next主题，在git工程下新建them-next分支，用于管理源文件
1.根目录中文件及文件夹（除hexo_config外）均为主题文件
2.hexo_config文件夹中为hexo配置文件及source文件
```bash
hexo_config
    |-_config.yml
    |-source
        |-404.html
        |-favicon.ico
        |-tags //标签页
        |-categories  //分类页
        |-about  //关于页
        |-_post  //博文内容页
```