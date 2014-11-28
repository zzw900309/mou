# Mac下使用XAMPP配置前端测试环境

Windows中，可以使用IIS的方式来配置前端测试环境，MacOS虽然自带阿帕奇服务，但是纯命令行的操作上手比较慢，比较常见的方式是使用免费工具XAMPP。

下载安装 XAMPP
--

XAMPP 可以从 [官网](https://www.apachefriends.org/zh_cn/index.html) 直接下载到，下载后直接安装。

配置 XAMPP
--

XAMPP 默认的文件目录必须在 /Applications/XAMPP/htdocs/ 目录下，但是我们一般都有自己存放代码的地方（比如自己的Git目录），所以需要修改配置到自己的代码目录。

修改的方式是打开 /Applications/XAMPP/etc/httpd.conf 文件，将 /Applications/XAMPP/htdocs/ 修改为自己代码存放的目录（共有两处），修改完成后保存，再重新启动所有服务即可。

> 这里有两个注意点：

> 1. Mac的Host中必须有 `127.0.0.1 localhost`

>  mac打开hosts文件的方法是访问 /etc/，hosts文件就在里面

> 2. Mac下查看自己ip地址的方法：在网络偏好设置里面查看或使用终端命令行 ifconfig
