# 在 Ubuntu-16.04 下安装 Hadoop-2.7.3

  1.启用 root 账户
    ubuntu 安装好之后进入的是普通用户， root用户默认禁用。安装要在 root 用户下，用 sudo su 切换的不一样。所以要将 root 用户开启：
    * 启用 root 账户：进入终端，使用命令 sudo passwd root设置root的密码
    * 启用图形界面登录：输入命令，sudo vi /etc/lightdm/lightdm.conf，在文件末尾输入<br><b>
      allow-guest=false //禁用客人会话                                
      greeter-show-manual-login=true //开启图形登录</b></br>      
    * 重启系统，可以看到登录，输入 root 账户名的界面                   
    ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/one.PNG)

  2.设置静态ip： 
    修改ip：                                                             
    ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/two.PNG)
    重启网卡：service network-manager restart                       
    ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/three.PNG)



![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/two.PNG)
![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/two.PNG)
![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/two.PNG)
![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/two.PNG)
![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/two.PNG)
![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/two.PNG)
![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/two.PNG)
![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/two.PNG)                                                                          
    