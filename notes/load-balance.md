* 四层负载均衡
* 七层负载均衡

1. 负载均衡器通常称为四层交换机(L4 Switch)或七层交换机(L7 Switch)。四层交换机主要分析IP层及TCP/UDP层，实现四层流量负载均衡。七层交换机除了支持四层负载均衡以为，还有分析应用的信息，如HTTP协议URI或者Cookie信息。

2. 四层交换机，工作在OSI第四层，也就是说TCP层。这类Load Balance不理解应用协议（如HTTP/FTP/MySQL等）。有LVS，F5

3. 七层交换机，工作在OSI最高层，应用层。这类Load Balancer能理解应用协议。有haproxy，MySQL proxy。