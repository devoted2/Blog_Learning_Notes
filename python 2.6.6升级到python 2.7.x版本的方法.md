# python 2.6.6升级到python 2.7.x版本的方法
> 1.下载python2.7.x

wget https://www.python.org/ftp/python/2.7.6/Python-2.7.6.tgz

> 2.解压并编译安装

tar -zxvf Python-2.7.6.tgz && cd Python-2.7.6 && ./configure && make all && make install && make clean && make distclean
> 3.检查安装

/usr/local/bin/python2.7 -V

>4.建立软连接，使用系统默认的python指向

mv /usr/bin/python /usr/bin/python2.6.6
ln -s /usr/local/bin/python2.7 /usr/bin/python

>5.检查

python -V

>6.用yum需注意
解决系统 Python 软链接指向 Python2.7 版本后，因为yum是不兼容 Python 2.7的，所以yum不能正常工作，我们需要指定 yum 的Python版本
vim /usr/bin/yum 将头部#!/usr/bin/python 改成#!/usr/bin/python2.6.6(刚刚备份的)

以上所述是小编给大家介绍的python 2.6.6升级到python 2.7.x版本的方法，希望对大家有所帮助，如果大家有任何疑问请给我留言，小编会及时回复大家的。在此也非常感谢大家对脚本之家网站的支持！
原文链接：http://www.cnblogs.com/gaofubin/archive/2016/10/09/5941216.html