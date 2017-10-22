# ab - Apache HTTP server benchmarking tool

### 1.概念

   **ab** is a tool for benchmarking your Apache Hypertext Transfer Protocol (HTTP) server. It is designed to give you an impression of how your current Apache installation performs. This especially shows you how many requests per second your Apache installation is capable of serving.

### 2.原理
ab是apachebench命令的缩写。<br/>

ab命令会创建多个并发访问线程，模拟多个访问者同时对某一URL地址进行访问。它的测试目标是基于URL的，因此，它既可以用来测试apache的负载压力，也可以测试nginx、lighthttp、tomcat、IIS等其它Web服务器的压力。<br/>

ab命令对发出负载的计算机要求很低，它既不会占用很高CPU，也不会占用很多内存。但却会给目标服务器造成巨大的负载，其原理类似CC攻击。自己测试使用也需要注意，否则一次上太多的负载。可能造成目标服务器资源耗完，严重时甚至导致死机



### 3.安装（ubuntu）
sudo apt-get install **apache2-utils**
 

### 4.命令格式 

ab [options] [http[s]://]hostname[:port]/path  


### 5.命令参数(options)


* <font size=5>**-n requests** </font> <br/>
Number of requests to perform for the benchmarking session. The default is to just perform a single request which usually leads to non-representative benchmarking results.(在测试会话中所执行的请求个数。默认时，仅执行一个请求。)

* <font size=5>**-c concurrency**</font> </big><br/>
Number of multiple requests to perform at a time. Default is one request at a time. (一次产生的请求个数。默认是一次一个)

* **-t timelimit** <br/>
Maximum number of seconds to spend for benchmarking. This implies a -n 50000 internally. Use this to benchmark the server within a fixed total amount of time. Per default there is no timelimit.-t (测试所进行的最大秒数。其内部隐含值是-n 50000，它可以使对服务器的测试限制在一个固定的总时间以内。默认时，没有时间限制。)

* **-C cookie-name=value** <br/>
Add a Cookie: line to the request. The argument is typically in the form of a name=value pair. This field is repeatable.

* **-T content-type** <br/>
Content-type header to use for POST/PUT data, eg. application/x-www-form-urlencoded. Default is text/plain.

* **-p POST-file** <br/>
File containing data to POST. Remember to also set -T.

* **-H custom-header** <br/>
Append extra headers to the request. The argument is typically in the form of a valid header line, containing a colon-separated field-value pair (i.e., "Accept-Encoding: zip/zop;8bit").

* **-A auth-username:password** <br/>
Supply BASIC Authentication credentials to the server. The username and password are separated by a single : and sent on the wire base64 encoded. The string is sent regardless of whether the server needs it (i.e., has sent an 401 authentication needed).

* **-b windowsize** <br/>
Size of TCP send/receive buffer, in bytes.

* **-B local-address**<br/>
Address to bind to when making outgoing connections.

* **-d** <br/>
Do not display the "percentage served within XX [ms] table". (legacy support).

* **-e csv-file** <br/>
Write a Comma separated value (CSV) file which contains for each percentage (from 1% to 100%) the time (in milliseconds) it took to serve that percentage of the requests. This is usually more useful than the 'gnuplot' file; as the results are already 'binned'.

* **-f protocol** <br/>
Specify SSL/TLS protocol (SSL2, SSL3, TLS1, TLS1.1, TLS1.2, or ALL). TLS1.1 and TLS1.2 support available in 2.4.4 and later.

* **-g gnuplot-file** <br/>
Write all measured values out as a 'gnuplot' or TSV (Tab separate values) file. This file can easily be imported into packages like Gnuplot, IDL, Mathematica, Igor or even Excel. The labels are on the first line of the file.

* **-h** <br/>
Display usage information.


* **-i** <br/>
Do HEAD requests instead of GET.

* **-k** <br/>
Enable the HTTP KeepAlive feature, i.e., perform multiple requests within one HTTP session. Default is no KeepAlive.

* **-l** <br/>
Do not report errors if the length of the responses is not constant. This can be useful for dynamic pages. Available in 2.4.7 and later.

* **-m HTTP-method**  <br/>
Custom HTTP method for the requests. Available in 2.4.10 and later.


* **-P proxy-auth-username:password** <br/>
Supply BASIC Authentication credentials to a proxy en-route. The username and password are separated by a single : and sent on the wire base64 encoded. The string is sent regardless of whether the proxy needs it (i.e., has sent an 407 proxy authentication needed).

* **-q** <br/>
When processing more than 150 requests, ab outputs a progress count on stderr every 10% or 100 requests or so. The -q flag will suppress these messages.

* **-r** <br/>
Don't exit on socket receive errors.

* **-s timeout** <br/>
Maximum number of seconds to wait before the socket times out. Default is 30 seconds. Available in 2.4.4 and later.

* **-S** <br/>
Do not display the median and standard deviation values, nor display the warning/error messages when the average and median are more than one or two times the standard deviation apart. And default to the min/avg/max values. (legacy support).


* **-u PUT-file** <br/>
File containing data to PUT. Remember to also set -T.

* **-v verbosity** <br/>
Set verbosity level - 4 and above prints information on headers, 3 and above prints response codes (404, 200, etc.), 2 and above prints warnings and info.

* **-V** <br/>
Display version number and exit.

* **-w** <br/>
Print out results in HTML tables. Default table is two columns wide, with a white background.

* **-x &lt;table&gt;-attributes** <br/>
String to use as attributes for &lt;table&gt;. Attributes are inserted &lt;table here &gt;.

* **-X proxy[:port]** <br/>
Use a proxy server for the requests.

* **-y &lt;tr&gt;-attributes** <br/>
String to use as attributes for &lt;tr&gt;.

* **-z &lt;td&gt;-attributes** <br/>
String to use as attributes for &lt;td&gt;.

* **-Z ciphersuite** <br/>
Specify SSL/TLS cipher suite (See openssl ciphers)


### 6.测试与结果分析

 测试：ab -n 1000 -c 100  me.love/hi

![](http://p.ananas.chaoxing.com/star3/origin/10d222aa119812759bd199bcd845618e.png "测试结果")




* **Server Software**: Apache-coyote/1.1
//平台apache 版本1.1

* **Server Hostname**: me.love
//服务器主机名

* **Server Port**: 80
//服务器端口

* **Document Path**: /hi
//测试的页面文档

* **Document Length**: 1018 bytes
//文档大小


* **Concurrency Level**: 100
//并发数

* **Time taken for tests**: 1.732 seconds
//整个测试持续的时间

* **Complete requests**: 1000
//完成的请求数量

* **Failed requests**: 0
//失败的请求数量

* **Write errors**: 0

* **Total transferred**: 142000 bytes
//整个场景中的网络传输量

* **HTML transferred**: 20000 bytes
//整个场景中的HTML内容传输量


* **Requests per second**: 577.36 [#/sec] (mean)
 <br/>
服务器并发处理能力的量化描述，单位是reqs/s，指的是在某个并发用户数下单位时间内处理的请求数。	
<br/>
某个并发用户数下单位时间内能处理的最大请求数，称之为最大吞吐率。
记住：吞吐率是基于并发用户数的。这句话代表了两个含义：
<br/>
a、吞吐率和并发用户数相关
<br/>
b、不同的并发用户数下，吞吐率一般是不同的
计算公式：总请求数/处理完成这些请求数所花费的时间，即
Request per second=Complete requests/Time taken for tests
必须要说明的是，这个数值表示当前机器的整体性能，值越大越好。


* **Time per request**: 173.201 [ms] (mean)
<br/>
用户平均请求等待时间.
<br/>
计算公式：处理完成所有请求数所花费的时间/ （总请求数 / 并发用户数），即
Time per request = Time taken for tests /( Complete requests / Concurrency Leve).


* **Time per request**: 1.732 [ms] (mean, across all concurrent requests)
<br/>计算公式：处理完成所有请求数所花费的时间/总请求数，即：
Time taken for tests/Complete requests；
<br/>可以看到，它是吞吐率的倒数。
同时，它也等于用户平均请求等待时间/并发用户数，即
Time per request/Concurrency Level

* **Transfer rate**: 80.06 [Kbytes/sec] received
//平均每秒网络上的流量，可以帮助排除是否存在网络流量过大导致响应时间延长的问题



                                                         
 **Percentage of the requests served within a certain time (ms)**

  **50%    153**

  **66%    167**

  **75%    177**

  **80%    183**

  **90%    294**

  **95%    334**

  **98%    349**

  **99%    352**

 **100%    377 (longest request)**


//整个场景中所有请求的响应情况。在场景中每个请求都有一个响应时间，其中50％的用户响应时间小于153 毫秒，60％ 的用户响应时间小于167 毫秒，最大的响应时间小于377 毫秒
