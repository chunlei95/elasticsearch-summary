# elasticsearch安装
## 单节点安装
> 环境：centos 7 jdk1.8<br/>
> 安装方式: tar安装
#### 获取压缩包
>1 从[官网](https://www.elastic.co/downloads/elasticsearch)下载压缩包
>2 
#### 解压获取的压缩包
#### 创建用户组以及用户
> 由于elasticsearch不能以root用户运行，所以需要创建一个用户来运行elasticsearch：<br/>
```
    groupadd elastic
    useradd elastic -g elastic
    su root
    chown -R elastic elastic /usr/local/elasticsearch
    su elastic
    bin/elasticsearch
```
> 此时启动时会报配置错误:
> 解决方法:
```
    sudo vi /etc/security/limits.conf
    添加如下配置:
    elastic - nofile 65536
    elastic - nproc 4096
```
> 重新启动虚拟机(网上的说法不用重新启动，但是我的一直报错用户处理线程数的问题没有解决，直到重启虚拟机之后才没有报错，能够正常启动)<br/>
> 浏览器访问'http://ip:9200'可以获取到elasticsearch单节点集群的信息，安装完成
