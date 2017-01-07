Kafka 最后一周大作业

---------------------
1.创建topic脚本
bin/kafka-topics.sh --create --zookeeper 192.168.157.146:2181 --replication-factor 1 --partitions 1 --topic orders
bin/kafka-topics.sh --create --zookeeper 192.168.157.146:2181 --replication-factor 1 --partitions 1 --topic items
bin/kafka-topics.sh --create --zookeeper 192.168.157.146:2181 --replication-factor 1 --partitions 1 --topic users
bin/kafka-topics.sh --create --zookeeper 192.168.157.146:2181 --replication-factor 1 --partitions 1 --topic orderuser-repartition-by-item
bin/kafka-topics.sh --create --zookeeper 192.168.157.146:2181 --replication-factor 1 --partitions 1 --topic my-result

2.消费者代码
com.jasongj.kafka.consumer.DemoConsumerManualCommit

3.Kafka Stream
com.jasongj.kafka.stream.PurchaseAnalysis4

4.读文件中的数据并发布到Kafka的Producer
com.jasongj.kafka.stream.producer.ItemProducer
com.jasongj.kafka.stream.producer.UserProducer
com.jasongj.kafka.stream.producer.OrderProducer

5.测试数据文件
/demokafka.0.10.1.0/src/main/resources/items.csv
/demokafka.0.10.1.0/src/main/resources/users.csv
/demokafka.0.10.1.0/src/main/resources/orders.csv

6.测试过程
  1)先启动消费者，对结果topic进行消费
  2)执行PurchaseAnalysis4 启动Kafka Stream
  3)按照顺序执行 item生产者，user生产者，order生产者，发送到对应topic

7.结果
  通过对结果topic进行消费可以得到以下结果
  1447113610000,1447113615000,pod,ipod,91,1888.88,171888.08000000007,1

  1447113610000,1447113615000,pad,ipad,91,4888.88,444888.08000000013,1

  1447113610000,1447113615000,watch,iwatch,105,2668.88,280232.4000000001,1

  1447113610000,1447113615000,phone,iphone,98,5388.88,528110.2400000002,1
  1447113610000,1447113615000,phone,vivo,21,2000.66,42013.86000000001,2
  1447113610000,1447113615000,phone,zhongxing,21,1388.88,29166.48,3
