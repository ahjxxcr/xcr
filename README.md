# xcr
测试GitHub

1. 启动远端jstatd.
  1.1 配置安全访问，将如下的代码存为文件jstatd.all.policy (名字随便起)，但要放到JAVA_HOME/bin中，其内容如下，
    grant codebase"file:${java.home}/../lib/tools.jar"{permission java.security.AllPermission;};
  1.2 进入到JAVA_HOME/bin中
    执行./jstatd -J-Djava.security.policy=jstatd.all.policy -J-Djava.rmi.server.hostname=182.180.113.222
    （jstatd -J-Djava.security.policy=/usr/admin/jstatd.java.policy -J-Djava.rmi.server.logCalls=true 可查看日志）
    其中ip需在/etc/hosts中设置
			
2.本地启动java visualvm 在远程中添加该ip，即可

3.catalina.sh 设置

JAVA_OPTS="-Xms256m-Xmx512m  -Xss1024K-XX:PermSize=64m-XX:MaxPermSize=128m"

3.关闭防火墙
	1.首先查看防火墙状态：
	service iptables status
	
	永久性生效，重启后不会复原
	开启：
	chkconfig iptables on
	关闭：
	chkconfig iptables off
	
	即时生效，重启后复原
	开启：
	service iptables start
	关闭：
	service iptables stop
  
./jstatd -J-Djava.security.policy=jstatd.all.policy -J-Djava.rmi.server.hostname=182.180.14.156
