# wordpress自动给图片添加alt和title
```
/**
* WordPress判断并自动添加图片alt和title属性
* http://www.ilxtx.com/how-to-add-alt-and-title-properties-to-image-automatically.html
*/
/* 智能判断添加图片alt属性 来自 @缙哥哥的博客*/
    function lxtx_image_alt( $imgalt ){
            global $post;
            $title = $post->post_title;
            $imgUrl = "<img\s[^>]*src=(\"??)([^\" >]*?)\\1[^>]*>";
            if(preg_match_all("/$imgUrl/siU",$imgalt,$matches,PREG_SET_ORDER)){
                    if( !empty($matches) ){
                            for ($i=0; $i < count($matches); $i++){
                                    $tag = $url = $matches[$i][0];
                                    $judge = '/alt=/';
                                    preg_match($judge,$tag,$match,PREG_OFFSET_CAPTURE);
                                    if( count($match) < 1 )
                                    $altURL = ' alt="'.$title.'" ';
                                    $url = rtrim($url,'>');
                                    $url .= $altURL.'>';
                                    $imgalt = str_replace($tag,$url,$imgalt);
                            }
                    }
            }
            return $imgalt;
    }
    add_filter( 'the_content','lxtx_image_alt');
 
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