# 在 Ubuntu-16.04 下安装 Hadoop-2.7.3

  1.启用 root 账户
  
  <b>注意：</b>ubuntu 安装好之后进入的是普通用户， root账户默认禁用。安装要在 root 账户下进行，用 sudo su 切换的不一样。所以要将 root 账户开启：                                                                                                       
  * 启用 root 账户：进入终端，使用命令 sudo passwd root设置root的密码                                                              
  * 启用图形界面登录：输入命令，sudo vi /etc/lightdm/lightdm.conf，在文件末尾输入                                             
  <b>allow-guest=false //禁用客人会话                                
  greeter-show-manual-login=true //开启图形登录</b>                                                 
  * 重启系统，可以看到登录，输入 root 账户名的界面                                                               
  ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/one.PNG)

2.设置静态ip                                                                                                 
  * 修改ip：                                                                                                         
  ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/two.PNG)
  * 重启网卡：service network-manager restart                          
  ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/three.PNG)                                            

3.修改主机名                                                                                                                  
  * 输入 hostname xxx 改变主机名                                             
  * 配置文件使之永久生效：输入命令 vi /etc/hostname  将hostname改掉                                              
  ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/hostname.PNG)
  * 把主机名和ip绑定：输入命令 vi /etc/hosts，增加一行 192.168.80.100 xxx(hostname)                                            
  ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/hosts.PNG)
  
4.关闭防火墙                                                                                        
  * 查看防火墙状态：输入命令 ufw status                                            
  * 开启防火墙：输入命令 ufw enable                                            
  * 关闭防火墙：输入命令 ufw disable                                            
  ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/ufw.PNG)                                            

5.使用SSH进行免密码登陆                                                                                        
  * 产生密钥文件：依次输入命令 cd ~/.ssh、ls                                                  
  * 把公钥放入 authorized_keys 文件：依次输入命令 cp ~/.ssh/id-rsa.pub ~/.ssh/authorized_keys、ls                                                                                                                
  * 登陆ssh：ssh local                                                                                          
  ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/ssh.PNG)

6.安装JDK                                                                           
  * 选择安装目录：这里在 /usr/lib/ 下新建 jvm 文件夹，将解压和重命名的文件 jdk1 放入 jvm 下                              
  * 配置环境文件：输入命令 vi /etc/profile，增加如下代码，保存退出，让改动立即生效：输入命令 source /etc/profile      
  ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/java.PNG)                              
  * 验证：输入命令 java -version (出现java版本则成功）                                                            
  ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/javav.PNG)                              

7.安装hadoop                                                                                                         
   * 选择目录解压并重命名文件：这里输入的命令依次为 tar -zxvf hadoop-2.7.3.tar.gz、mv hadoop-2.7.3                                                                                                                  
   * 修改配置文件：输入命令 vi /etc/profile ，增加如下代码，保存退出，输入 source /etc/profile 使之生效               
   ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/hadoop.PNG)                              
   * 测试环境配置是否正确：输入命令 hadoop，出现如下界面表示成功                                             
   ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/hadp.PNG)                                             
   * 修改配置文件，使适应伪分布，修改位于 $HADOOP_HOME/conf 目录下的 hadoop-env.sh、core-site.xml、hdfs-site.xml、mapred-site.xml 文件
                                                                           
   $: vi hadoop-env.sh                                                            

   <b>export JAVA_HOME=/usr/lib/jvm/jdk1</b>                                                               
                     
   core-site.xml：                                                            
   ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/core.PNG)                              
   hdfs-site.xml:                                                                                          
   ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/hdfs.PNG)                                              
   mapred-site.xml:                                                                                                 
   ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/mapred.PNG)                                               
   * 对 hadoop 进行格式化：输入命令 bin/hadoop namenode -format                              
   ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/bin.PNG)
   * 启动：输入命令 start -all.sh                                                            
   ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/start.PNG)  
   * 验证：用 jps 查看java进程                                                            
   ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/yes.PNG)  
   * 浏览器查看：                                                            
   ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/namenode.PNG) 
   * 如果多次格式话造成安装不成功，删除 tmp 文件                                                                           
   ![图片](https://github.com/Hiooary/hadoop_3.io/blob/master/images/tmp.PNG)                                                 


