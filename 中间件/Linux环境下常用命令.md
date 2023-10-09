## MySql

```sql
# 1.备份数据库
mysqldump --set-gtid-purged=OFF --single-transaction --quick  --host=localhost -P3307 -uroot -przoncloud -C --databases tsms >  D:\\database-migrate\\tsms-back.sql
```

## Kafka
[[zookeeper集群配置]]
[[kafka安装]]
```bash
# 1.启动kafka
./bin/kafka-server-start.sh -daemon config/server.properties

# 2.创建新的topic
./bin/kafka-topics.sh --create --bootstrap-server v9:9092 --partitions 2 --topic user-info-setting

# 3.设置log保存时间，默认7天
./bin/kafka-configs.sh --bootstrap-server test-kafka1:9092 --alter --entity-name user-behavior-log --entity-type topics --add-config retention.ms=3000

# 4.监听某个topic
**.**/bin/kafka-console-consumer.sh --bootstrap-server test-kafka1:9092 --topic user-behavior-log
# 5.查看topic列表
./bin/kafka-topics.sh --zookeeper 192.168.1.100:2181,192.168.0.250:2181,192.168.0.250:2182,192.168.0.172:2181 --list
```

## Logstash

```bash
# 1.启动logstash
nohup ./bin/logstash -f config/user-behavior-log-to-kafka.conf &
```