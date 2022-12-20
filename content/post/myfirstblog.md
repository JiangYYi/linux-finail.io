---
title: "Myfirstblog"
date: 2022-12-18T14:37:59+08:00
---
# 江江的Linux操作系统课程学习
### 学习笔记
- 搜索查找类
###### 1、find
```
#find指令  将从指定目录向下递归的遍历其各个子目录，将满足条件的文件或者目录显示在终端
find [搜索范围] [选项]
#选项说明
#-name <查询方式>   按照指定的文件名查找模式查找文件
#-user <用户名>		查找属于指定用户名所有文件
#-size <文件大小>   按照指定的文件大小查找文件

#按文件名，根据名称查找/home目录下的hello.txt文件
find /home -name hello.txt
#按拥有者，查找/opt目录下，用户名称为root的文件
find /opt -user root
#查找整个linux系统下大于20M的文件（+n 大于    -n 小于    n 等于）
find / -size +20M
#查询根目录下，所有后缀为.txt的文件
find / -name *.txt
```  
###### 2、locate
```
#locate指令  可以快速定位文件路径。locate指令利用事先建立的系统中所有文件名称及路径的locate数据库实现快速定位给定的文件。locate指令无需遍历整个文件系统，查询速度较快。为了保证查询结果的准确度，管理员必须顶起更新locate时刻。
locate 搜索文件
#由于locate指令基于数据库进行查询，所以第一次运行前。必须使用updatedb指令创建locate数据库

#使用locate指令快速定位hello.txt文件所在目录
updatedb
locate hello.txt
```
###### 3、grep & 管道符号 |
```
#grep过滤查找
#管道符 "|" ,表示将前一个命令的处理结果，输出传递给后面的命令处理。

grep [选项] 查找内容 源文件

#选项
# -n		显示匹配行及行号
# -i		忽略字母大小写

#应用实例 ： 请在hello.txt文件中，查找 "yes" 所在行，并且显示行号
cat hello.txt | grep -ni yes
#cat hello.txt  将hello.txt的内容浏览出来
# | 是将cat浏览出来的内容交给后面的命令处理
#grep yes  是将 | 交过来的内容进行过滤查找

```
+ 压缩和解压缩类
###### 1、gzip & gunzip
```
#gzip用于压缩
#gunzip用于解压

gzip 文件				#压缩文件，只能将文件压缩为 *.gz 文件
gunzip 文件.gz		#解压缩文件命令

```
###### 2、zip & unzip
```
#zip用于压缩
#unzip用于解压
#在项目打包发布中很有用

zip [选项] xxx.zip 将要压缩的内容	#压缩文件和目录的命令
unzip [选项] xxx.zip				#解压缩文件

#zip常用选项：-r  递归压缩，即压缩目录
#unzip常用选项：-d <目录>   指定解压后文件的存放目录
```
###### 3、tar
```
#打包指令  最后打包后的文件是.tar.gz的文件

tar [选择] xxx.tar.gz 打包的内容	#打包目录，压缩后的文件格式是.tar.gz

#常用选项
#-c 	产生.tar打包文件
#-v 	显示详细信息
#-f		指定压缩后的文件名
#-z		打包同时压缩
#-x		解包.tar文件

#案例
#1、压缩多个文件，将/home/a1.txt和/home/a2.txt压缩成a.tar.gz
tar -zcvf /home/a.tar.gz /home/a1.txt /home/a2.txt
#2、将/home的文件夹压缩成myhome.tar.gz
tar -zcvf myhome.tar.gz /home/
#3、将a.tar.gz解压到当前目录下
tar -zxvf a.tar.gz
#4、将myhome.tar.gz解压到/opt目录下(指定的目录必须是存在的)
tar -zxvf myhome.tar.gz -C /opt/
```
### 大作业完成步骤  
1.使用git管理大作业相关的代码、配置文件等，要求有能反映大作业过程的git提交记录。
```
sudo yum -y install git#下载git
ssh-keygen -t rsa -C "邮箱"#生成ssh key
git init#初始化
git add 文件名#将我们需要提交的代码从工作区添加到暂存区
git commit -m "提交"#将暂存区里的改动给提交到本地的版本库
git push origin master#将本地版本库的分支推送到远程服务器对应的分支上
```
提交结果:  
![img](/12.png )
2.用socket 技术编写程序使用容器技术Docker，将socket客户端和服务端分别运行在不同的容器中
，实现socket客户端和服务端之间的信息传递。
3.Hugo
