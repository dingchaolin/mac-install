# mac ab测试

## 启动Apache
- sudo apachectl start
- 打开浏览器地址栏输入 “http://localhost”，可以看到内容为“It works!”的页面

## 安装httpd
- http://mirrors.hust.edu.cn/apache//httpd/httpd-2.4.29.tar.gz
- tar -xvf httpd-2.4.29.tar.gz
- mv httpd-2.4.29 httpd

## 测试
- 进入 httpd/support
- ab -n 4 -c 1 http://mirrors.hust.edu.cn/apache//httpd/

## ab测试命令简介
```
    -n在测试会话中所执行的请求个数。默认时，仅执行一个请求。
    
    -c一次产生的请求个数。默认是一次一个。
    
    -t测试所进行的最大秒数。其内部隐含值是-n 50000，它可以使对服务器的测试限制在一个固定的总时间以内。默认时，没有时间限制。
    
    -p包含了需要POST的数据的文件。
    
    -P对一个中转代理提供BASIC认证信任。用户名和密码由一个:隔开，并以base64编码形式发送。无论服务器是否需要(即, 是否发送了401认证需求代码)，此字符串都会被发送。
    
    -T POST数据所使用的Content-type头信息。
    
    -v设置显示信息的详细程度-4或更大值会显示头信息，3或更大值可以显示响应代码(404,200等),2或更大值可以显示警告和其他信息。
    
    -V显示版本号并退出。
    
    -w以HTML表的格式输出结果。默认时，它是白色背景的两列宽度的一张表。
    
    -i执行HEAD请求，而不是GET。
    
    -x设置<table>属性的字符串。
    
    -X对请求使用代理服务器。
    
    -y设置<tr>属性的字符串。
    
    -z设置<td>属性的字符串。
    
    -C对请求附加一个Cookie:行。其典型形式是name=value的一个参数对，此参数可以重复。
    
    -H对请求附加额外的头信息。此参数的典型形式是一个有效的头信息行，其中包含了以冒号分隔的字段和值的对(如,"Accept-Encoding:zip/zop;8bit")。
    
    -A对服务器提供BASIC认证信任。用户名和密码由一个:隔开，并以base64编码形式发送。无论服务器是否需要(即,是否发送了401认证需求代码)，此字符串都会被发送。
    
    -h显示使用方法。
    
    -d不显示"percentage served within XX [ms] table"的消息(为以前的版本提供支持)。
    
    -e产生一个以逗号分隔的(CSV)文件，其中包含了处理每个相应百分比的请求所需要(从1%到100%)的相应百分比的(以微妙为单位)时间。由于这种格式已经“二进制化”，所以比'gnuplot'格式更有用。
    
    -g把所有测试结果写入一个'gnuplot'或者TSV(以Tab分隔的)文件。此文件可以方便地导入到Gnuplot,IDL,Mathematica,Igor甚至Excel中。其中的第一行为标题。
    
    -i执行HEAD请求，而不是GET。
    
    -k启用HTTP KeepAlive功能，即在一个HTTP会话中执行多个请求。默认时，不启用KeepAlive功能。
    
    -q如果处理的请求数大于150，ab每处理大约10%或者100个请求时，会在stderr输出一个进度计数。此-q标记可以抑制这些信息。
```

- 参数很多,一般我们用 -c 和 -n 参数就可以了. 例如: ab -c 100 -n 10000 http://127.0.0.1/index.php 