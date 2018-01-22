## nginx用作HTTP负载均衡
### 介绍
通过多台应用程序实例的负载均衡通常用作优化资源利用，增大吞吐量，减少延时，确保容错性的配置。
你可以把nginx当做非常高效的负载均衡用来将请求分发到多个服务器，从而提高性能，伸缩性和可依赖性。
### 负载均衡方法
nginx支持以下几种负载均衡方法。
* __轮询调度__ - 请求将以轮询调度的方式分发到不同的服务器。
* __最少连接__ - 将下一个请求发往拥有最少活动连接的服务器。
* __IP哈希__ - 用哈希函数决定下一个请求发往的服务器，基于客户端的IP地址。
### 默认的负载均衡配置
下面就是一个nginx简单的负载均衡的例子
```
http {
    upstream myapp1 {
        server serv1.exapmle.com;
        server serv2.example.com;
        server serv3.example.com;
    }

    server {
        listen 80;

        localtion / {
            proxy_pass http://myapp1;
        }
    }
}
```
上面的例子中，应用程序配置有三台服务器从serv1到serv3。当负载均衡方法没有配置的时候，__默认会采用轮询调度方法__。所有通过myapp1组的代理请求，都会被nginx的负载均衡分发。