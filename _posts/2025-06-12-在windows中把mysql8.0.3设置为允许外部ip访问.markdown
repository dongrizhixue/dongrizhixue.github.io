# 在windows中把mysql8.0.3设置为允许外部ip访问

---
layout: post

title:  "在windows中把mysql8.0.3设置为允许外部ip访问"

date:   2025-06-12 09:45:10 +0800

categories: dongrizhixue update

---

要在 Windows 系统中设置 MySQL 8.0.3 允许外部 IP 访问，你需要按照以下步骤操作：

1. 登录到 MySQL
首先，你需要使用管理员账号登录到 MySQL：

~~~bash
mysql -u root -p
~~~

输入密码后，你将进入 MySQL 命令行界面。

2.更新用户权限
接下来，你需要更新用户的权限，允许从任何主机（即任何 IP 地址）访问。这通常涉及到修改 MySQL 的用户表中的主机字段。例如，如果你想让 root 用户可以从任何地方访问，你可以执行以下命令：

~~~bash
UPDATE mysql.user SET Host = '%' WHERE User = 'root';
~~~

或者，如果你想添加一个新用户，可以使用以下命令：

~~~bash
GRANT ALL PRIVILEGES ON *.* TO 'newuser'@'%' IDENTIFIED BY 'yourpassword';
~~~

这里 'newuser' 是新的用户名，'%' 表示任何主机，'yourpassword' 是新用户的密码。

3.刷新权限
更新完权限后，你需要刷新权限缓存，以便让 MySQL 立即生效：

~~~bash
FLUSH PRIVILEGES;
~~~

4.重启 MySQL 服务
为了确保所有的更改都能生效，你需要重启 MySQL 服务。在命令行中，你可以使用以下命令来重启 MySQL 服务：

~~~bash
net stop mysql
net start mysql
~~~

这里的 mysql 可能需要替换成你的 MySQL 服务的实际名称，如果你在安装 MySQL 时更改过服务名。

5.检查防火墙设置
确保你的 Windows 防火墙允许外部访问 MySQL 的默认端口 3306。你可能需要创建一个入站规则来允许 TCP 端口 3306 的连接。

6.检查 my.ini 配置文件
确认你的 my.ini 文件中 bind-address 设置为 0.0.0.0 或者没有这一行，这样 MySQL 才会监听所有网络接口：

~~~bash
[mysqld]
bind-address = 0.0.0.0
~~~

如果 bind-address 缺省或设置为 127.0.0.1，MySQL 只会监听本地回环接口，外部 IP 将无法访问。

完成以上步骤后，你应该能够从外部 IP 地址访问 MySQL 数据库了。如果仍然遇到问题，检查错误日志以获取更多细节，或者确认是否有其他网络设备（如路由器）阻止了外部连接。
