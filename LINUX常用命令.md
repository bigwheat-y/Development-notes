# LINUX常用命令

#### 查看当前使用端口

```bash
netstat -ntlp //tcp
netstat -nulp //udp
lsof -i
```

#### firewall防火墙

1、查看firewall服务状态

```bash
systemctl status firewalld
#出现Active: active (running)切高亮显示则表示是启动状态。
#出现 Active: inactive (dead)灰色表示停止，看单词也行。
```

2、查看firewall的状态

```bash
firewall-cmd --state
```

3、开启、重启、关闭、firewalld.service服务

```bash
#开启
service firewalld start
#重启
service firewalld restart
#关闭
service firewalld stop
```

4、查看防火墙规则

```bash
firewall-cmd --list-all
```

5、查询、开放、关闭端口

```bash
#查询端口是否开放
firewall-cmd --query-port=8080/tcp
#开放80端口
firewall-cmd --permanent --add-port=80/tcp
#移除端口
firewall-cmd --permanent --remove-port=8080/tcp
#重启防火墙(修改配置后要重启防火墙)
firewall-cmd --reload
```

#### 直接用命令开启端口

```bash
#开放端口命令----保存-----重启服务-------查看端口是否开放

/sbin/iptables -I INPUT -p tcp --dport 6379 -j ACCEPT
/etc/rc.d/init.d/iptables save
/etc/init.d/iptables restart
/sbin/iptables -L -n

#修改文件配置
1.编辑/etc/sysconfig/iptables文件：vi /etc/sysconfig/iptables加入内容并保存：-A RH-Firewall-1-INPUT -m state --state NEW -m tcp -p tcp --dport 6397 -j ACCEPT
2.重启服务：/etc/init.d/iptables restart
3.查看端口是否开放：/sbin/iptables -L -n
```

#### Docker命令

```bash
#查看已存在的容器
docker ps -a 
#运行已停止的容器
docker start id
#移除已存在的容器
docker rm id
```

#### Git设置代理

```bash
git config --global http.proxy http://127.0.0.1:7890
git config --global https.proxy https://127.0.0.1:7890
```

