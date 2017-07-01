#给wordpress文章图片自动添加链接

WordPress图片附件的默认链接方式是通过 image_default_link_type 来定义的，类型可以是’none’,’file’,’post’三个类型，分别是无链接，链接到媒体文件(原始地址)，链接到附件页面。

要自定义默认的链接方式为”链接到媒体文件(原始地址)“，可以在主题的 functions.php 文件中添加以下代码即可：
```
//图片默认连接到媒体文件(原始链接)
update_option('image_default_link_type', 'file');
```
或者访问  http://yoursite.com/wp-admin/options.php 这个地址，找到 image_default_link_type 填上file即可。