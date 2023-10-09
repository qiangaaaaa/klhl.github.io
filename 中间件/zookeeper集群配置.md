
### 配置

```bash
# The number of milliseconds of each tick
tickTime=2000
# The number of ticks that the initial 
# synchronization phase can take
initLimit=10
# The number of ticks that can pass between 
# sending a request and getting an acknowledgement
syncLimit=5
# the directory where the snapshot is stored.
# do not use /tmp for storage, /tmp here is just 
# example sakes.
dataDir=/root/apps/zookeeper/data/zk01/data
dataLogDir=/root/apps/zookeeper/data/zk01/logs
# the port at which the clients will connect
clientPort=2181
# the maximum number of client connections.
# increase this if you need to handle more clients
#maxClientCnxns=60
#
# Be sure to read the maintenance section of the 
# administrator guide before turning on autopurge.
#
# <http://zookeeper.apache.org/doc/current/zookeeperAdmin.html#sc_maintenance>
#
# The number of snapshots to retain in dataDir
autopurge.snapRetainCount=7
# Purge task interval in hours
# Set to "0" to disable auto purge feature
autopurge.purgeInterval=24

## Metrics Providers
#
# <https://prometheus.io> Metrics Exporter
#metricsProvider.className=org.apache.zookeeper.metrics.prometheus.PrometheusMetricsProvider
#metricsProvider.httpPort=7000
#metricsProvider.exportJvmInfo=true
server.1=192.168.0.250:2888:3888
server.2=192.168.0.250:2889:3889
server.3=192.168.0.172:2888:3888
```

在以上配置中指定的data目录中，创建一个`myid`文件写入当前节点id，id与serverId对应

```bash
# 创建文件写入id
echo '1' > /root/apps/zookeeper/data/zk01/data/myid
```

### 启动

```bash
./bin/zkServer.sh start
```