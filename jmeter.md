https://www.jianshu.com/p/815c8286326d
https://zhuanlan.zhihu.com/p/28319871

### 下载

官网主页：http://jmeter.apache.org/download_jmeter.cgi
http://apache.mirrors.tds.net//jmeter/binaries/apache-jmeter-5.2.1.tgz
http://apache.mirrors.tds.net//jmeter/binaries/apache-jmeter-5.2.1.zip
https://github.com/apache/jmeter

### websocket压测插件

官方下载：https://jmeter-plugins.org/files/packages/websocket-sampler-1.0.2-SNAPSHOT.zip
备用下载：http://image.mariojd.cn/WebSocketSampler-Jars.zip
note:将下载好的Jar包放到JMeter的`lib\ext`目录下即可。

### notice:

websocket压测长连接时，要设置定时器，否则链接建立成功后会自动断开

### 问题解决

jmeter压测报错socket closed解决方法
https://blog.csdn.net/pittpakk/article/details/95338079

返回repose code 429 
是限制单个ip并发访问的数量，laravel去掉throttle中间件 

生成html报告，使用no gui模式
```
jmeter –n –t <jmx filepath> -l <csv log path>  -e –o <report folder path>

-n: 非GUI模式执行JMeter
-t: 执行测试文件所在的位置
-l: 指定生成测试结果的保存文件，jtl文件格式
-e: 测试结束后，生成测试报告
-o: 指定测试报告的存放位置
```

