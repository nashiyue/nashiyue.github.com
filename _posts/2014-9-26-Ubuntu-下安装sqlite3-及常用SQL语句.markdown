---
layout: post
title:  "Ubuntu 下安装sqlite3 及常用SQL 语句"
date:   2014-9-26 20:06:17
categories: SQL
---

安装sqlite3命令如下:
{% highlight ruby %}
sudo apt-get install sqlite3
{% endhighlight %}
创建或者打开已有的数据库文件:
{% highlight ruby %}
sqlite3 test.db
{% endhighlight %}
进入数据库后,可以进行以下常用SQL语句操作:
{% highlight ruby %}
CREATE TABLE ONT_USER_TABLE(
    ONT_USER_NAME text PRIMARY KEY,
    ONT_USER_PWD  text NOT NULL,
    ONT_CREATE_TIME text
);

INSERT INTO ONT_USER_TABLE values('admin','123456','2014-09-26 19:25');

UPDATE ONT_USER_TABLE SET ONT_USER_PWD = 'abcdefg';

DELETE FROM ONT_USER_TABLE WHERE ONT_USER_NAME = 'admin';
{% endhighlight %}
查询表结构代码如下:
{% highlight ruby %}
.schema
{% endhighlight %}
查询当前已有的表
{% highlight ruby %}
.table
{% endhighlight %}

退出:
{% highlight ruby %}
.quit
{% endhighlight %}


