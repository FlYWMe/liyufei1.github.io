---
title: verify
date: 2018-02-01 09:55:55
tags: 
categories: project
---
0.第一次运行出错：端口、redis

  解决：要先启动redis

    cd /etc/redis/  
    sudo redis-server ./redis.conf

  验证：redis-cli

1.问题：运行reg/search/compare报错CUDA，显存不够用

  解决：将caffeThreads设为1

2.端口被占用：lsof -i:33388

  解决：kill -9 xxxx

3.测试base64编码，运行带有opencv库

  解决：gcc Test.c -o Test \`pkg-config --cflags --libs opencv `

4.git相关：


- git fetch origin develop 取回远程分支更新
- git pull origin develop:dev-lyf
   =git fetch origin + git merge origin/develop
- git checkout -b dev-lyf
- git reset --hard 清除本地修改
- git add cudascan.cu
- git commit -m "update"
- git push origin lyf
- 在分支右侧发pull request