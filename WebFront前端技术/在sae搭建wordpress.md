# 在SAE搭建wordpress

现在的SAE已经没有免费的WordPress4SAE了，所以需要手动安装并进行配置。在安装模板，插件和数据导入部分比较繁琐。

准备工作
--

注册 [SAE](http://sae.sina.com.cn/) 账号，创建一个PHP应用，应用创建后，到代码管理中初始化代码库，建立版本号为1的代码库，在MySql中初始化一个mysql数据库，再到Storage中创建一个新的Storage，给storage起一个名字。

> 这里storage的名字需要全部是英文小写

下载最新版本的WordPress源码，中文用户可以到 [WordPress中文网](https://cn.wordpress.org/) 去下载最新的源码包，下载完成后解压缩

上传代码
--

首先将代码从服务器上将代码Check下来，我在mac下使用的是smartSVN（可破解）。

> Check的仓库地址为 https://svn.sinaapp.com/app_name ，邮箱使用安全邮箱，密码是安全密码，这些在个人资料中可以查找和设置。

Check完成后，会得到一个数字根目录，也就是刚刚初始过的代码库。将WordPress代码复制到数字目录下。

> 不要复制根目录，要复制根目录里面的文件，保证 index.php 在SVN数字目录的根目录下

完成后点击commit提交，提交成功访问网站就可以看到WordPress的配置界面了。

安装数据库
--

因为直接对SAE没有写权限，所以传统方法是安装不了数据库的，需要手动安装。按照wp-config-sample.php手动创建wp-config.php，并且修改几个数据库选项：

```
define('DB_NAME', SAE_MYSQL_DB);
define('DB_USER', SAE_MYSQL_USER);
define('DB_PASSWORD', SAE_MYSQL_PASS);
define('DB_HOST', SAE_MYSQL_HOST_M.':'.SAE_MYSQL_PORT);
```

> 这里要注意各个值都不要修改，因为是SAE默认的值

安装主题和插件
--

同样因为没有写权限的问题，无法直接安装主题和插件，需要通过SVN方式来上传。wordpress的插件和主题代码分别放在wp-content/plugins和wp-content/themes目录下。

导入数据库
--

需要将原来博客的内容迁移过来时，第一步需要使用导出插件，将博客内容导出为一个XML文件，然后下载到本地。但是不能直接导入，需要用到之前创建的storage，同时安装 [导入插件](https://wordpress.org/plugins/wordpress-importer/) 。

storage这是SAE为应用提供的存储资源，通过importer将xml文件放到storage domain里去。需要修改一下wordpress的代码，将所有的写文件操作都重定向到storage。

> 这里参照了SAE论坛的一个讨论帖 [我可以上传自己的wordpress吗，和应用里的不一样吗？](http://cloudbbs.org/forum.php?mod=viewthread&tid=10085&highlight=wordpress%2B%E4%B8%8A%E4%BC%A0)

在应用根目录，创建sae.php，

```
<?php
/* 在SAE的Storage中新建的Domain名，比如“wordpress” */
define('SAE_STORAGE',wordpress);
/* 设置文件上传的路径和文件路径的URL，不要更改 */
define('SAE_DIR', 'saestor://'.SAE_STORAGE.'/uploads');
define('SAE_URL', 'http://'.$_SERVER['HTTP_APPNAME'].'-'.SAE_STORAGE.'.stor.sinaapp.com/uploads');
?>
```

修改wp-includes/functions.php文件，在 `require( ABSPATH . WPINC . '/option.php' );`前添加

```
include( ABSPATH . '/sae.php' );  //调用SAE的Storage文件域名设置  //for SAE
```

然后注释掉如下代码：

```
//$wrapper = null;
// strip the protocol
//if( wp_is_stream( $target ) ) {
//    list( $wrapper, $target ) = explode( '://', $target, 2 );
//}
// from php.net/mkdir user contributed notes
//$target = str_replace( '//', '/', $target );
// put the wrapper back on the target
//if( $wrapper !== null ) {
//    $target = $wrapper . '://' . $target;
//}
```

替换为：

```
//for SAE begin
// from php.net/mkdir user contributed notes
if ( substr($target, 0, 10) == 'saestor://' ) {
return true;
}
$target = str_replace( '//', '/', $target );
//for SAE end
```

在 `$basedir = $dir;` 的上面添加

```
// for SAE begin
$dir = SAE_DIR;
$url = SAE_URL;
//for SAE end
```

在 `/** * Send a HTTP header to limit rendering of pages to same origin iframes.`的上面添加，

```
// for SAE begin
if ( !function_exists('utf8_encode') ) {
function utf8_encode($str) {
$encoding_in = mb_detect_encoding($str);
return mb_convert_encoding($str, 'UTF-8', $encoding_in);
}
}
//for SAE end
```

最后修改 wp-admin/includes/file.php，注释掉如下代码：

```
// Set correct file permissions
//$stat = stat( dirname( $new_file ));
//$perms = $stat['mode'] & 0000666;
//@ chmod( $new_file, $perms );
```

将所有的修改保存后Commit，大功告成，可以导入xml的内容了。


