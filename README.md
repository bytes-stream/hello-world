# ab - Apache HTTP server benchmarking tool

### 1.概念

   **ab** is a tool for benchmarking your Apache Hypertext Transfer Protocol (HTTP) server. It is designed to give you an impression of how your current Apache installation performs. This especially shows you how many requests per second your Apache installation is capable of serving.


### 2.安装（ubuntu）
sudo apt-get install **apache2-utils**
 

### 3.命令格式 

ab [options] [http[s]://]hostname[:port]/path  


### 3.命令参数(options)

  
* **-A auth-username:password** <br/>
Supply BASIC Authentication credentials to the server. The username and password are separated by a single : and sent on the wire base64 encoded. The string is sent regardless of whether the server needs it (i.e., has sent an 401 authentication needed).

* **-b windowsize** <br/>
Size of TCP send/receive buffer, in bytes.

* **-B local-address**<br/>
Address to bind to when making outgoing connections.

* <font size=5 color=blue>**-c concurrency**</font> </big><br/>
Number of multiple requests to perform at a time. Default is one request at a time.

* **-C cookie-name=value** <br/>
Add a Cookie: line to the request. The argument is typically in the form of a name=value pair. This field is repeatable.

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

* **-H custom-header** <br/>
Append extra headers to the request. The argument is typically in the form of a valid header line, containing a colon-separated field-value pair (i.e., "Accept-Encoding: zip/zop;8bit").

* **-i** <br/>
Do HEAD requests instead of GET.

* **-k** <br/>
Enable the HTTP KeepAlive feature, i.e., perform multiple requests within one HTTP session. Default is no KeepAlive.

* **-l** <br/>
Do not report errors if the length of the responses is not constant. This can be useful for dynamic pages. Available in 2.4.7 and later.

* **-m HTTP-method**  <br/>
Custom HTTP method for the requests. Available in 2.4.10 and later.

* <font size=5 color=blue>**-n requests** </font> <br/>
Number of requests to perform for the benchmarking session. The default is to just perform a single request which usually leads to non-representative benchmarking results.

* **-p POST-file** <br/>
File containing data to POST. Remember to also set -T.

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

* **-t timelimit** <br/>
Maximum number of seconds to spend for benchmarking. This implies a -n 50000 internally. Use this to benchmark the server within a fixed total amount of time. Per default there is no timelimit.

* **-T content-type** <br/>
Content-type header to use for POST/PUT data, eg. application/x-www-form-urlencoded. Default is text/plain.

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
