# wordpress自动给图片添加title
```
/* 强制用文章标题作为图片的title属性。不想设置图片的title属性的话可删除掉下面的代码！ */
function lxtx_image_title($content){
 global $post;
 $pattern = "/<img(.*?)src=('|\")(.*?).(bmp|gif|jpeg|jpg|png)('|\")(.*?)>/i";
 $replacement = '<img$1src=$2$3.$4$5 title="'.$post->post_title.'"$6>';
 $content = preg_replace($pattern,$replacement,$content);
 return $content;
}
add_filter('the_content','lxtx_image_title',15);
```
原文链接：[enter link description here](http://www.ilxtx.com/how-to-add-attribute-alt-and-title-to-image-automatically.html)