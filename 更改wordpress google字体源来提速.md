# 更改wordpress google字体源来提速
first
>打开wordpress代码中的文件wp-includes/script-loader.php文件

then
>搜索：`fonts.googleapis.com`找到这行代码：
$open_sans_font_url = "//fonts.googleapis.com/css?family1=Open+Sans:300italic,400italic,600italic,300,400,600&subset=$subsets";

last
>把调用地址fonts.googleapis.com替换为fonts.useso.com

修改完保存，再次刷新，大家就可以发现，自己的网站速度已经比以前快了很多，几乎瞬间就可以拿到Google字体了。原因就是本来需要从美国服务器才能拿到的google字体，现在已经遍布360全国的机房了。
