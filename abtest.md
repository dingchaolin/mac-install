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
- ab -n 全部请求数 -c 并发数 测试url
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

### 结果分析 
- ab -n 1000 -c 50 http://www.newdev.gztest.com/
```
Server Software:         Microsoft-IIS/7.0
Server Hostname:        www.newdev.gztest.com
Server Port:            80
Document Path:         
Document Length:        82522 bytes  #请求文档大小

Concurrency Level:      50           #并发数  
Time taken for tests:   92.76140 seconds #全部请 求完成耗时
Complete requests:      10000          #全部请求数
Failed requests:        1974           #失败的请求
  (Connect: 0, Length: 1974, Exceptions: 0)
Write errors:           0
Total transferred:      827019400 bytes   #总传输大小 
HTML transferred:       825219400 bytes //整个场 景中的HTML内容传输量
Requests per second:    108.61 [#/sec] (mean)   #每秒请 求数(平均)//大家最关心的指标之一，相当于 LR 中的每秒事务数，后面括 号中的 mean 表示这是一个平均值
Time per request:       460.381 [ms] (mean)   #每次并发请求时间(所有并发) //大家最关心的指标之二，相当于 LR 中的平均事务响应时间， 后面括号中的 mean 表示这是一个平均值
Time per request:       9.208 [ms] (mean, across all concurrent requests)   #每一请求时间(并发平均)  //每个请求实际运行时间的平均值
Transfer rate:          8771.39 [Kbytes/sec] received    #传输速 率//平 均每秒网络上的流量，可以帮助排除是否存在网络流量过大导致响应时间延长的问题
Percentage of the requests served within a certain time (ms)
 
 50%   2680
  66%   2806
  75%   2889
  80%   2996
  90%  11064
  95%  20161
  98%  21092
  99%  21417
 100%  21483 (longest request)
//整个场景中所有请求的响应情况。在场景中每个请求都有一个响应时间，其 中50％的用户响应时间小于2680毫秒，60％ 的用户响应时间小于2806毫秒，最大的响应时间小于21417毫秒
由于对于并发请求，cpu实际上并不是同时处理的，而是按照每个 请求获得的时间片逐个轮转处理的，所以基本上第一个Time per request时间约等于第二个Time per request时间乘以并发请求数。

Connection Times (ms)    #连接时 间
             min  mean[+/-sd] median   max
Connect(#连接):        0    0   2.1      0      46
Processing(#处理):    31  458  94.7    438    1078
Waiting(#等待):       15  437  87.5    422     938
Total:         31  458  94.7    438    1078
```