$SPARK_HOME/conf

spark-env.sh
LOCAL_IP = "127.0.0.1"

cp spark-defaults.conf.template spark-defaults.conf
spark.eventLog.enabled           true
spark.eventLog.dir               /home/cc/spark-2.1.3-bin-hadoop2.7/logs
spark.history.fs.logDirectory    /home/cc/spark-2.1.3-bin-hadoop2.7/logs

cp metrics.properties.template metrics.properties
#Enable CsvSink for all instances by class name
*.sink.csv.class=org.apache.spark.metrics.sink.CsvSink

#Polling period for the CsvSink
*.sink.csv.period=1
#Unit of the polling period for the CsvSink
*.sink.csv.unit=seconds

#Polling directory for CsvSink
*.sink.csv.directory=/home/cc/spark-2.1.3-bin-hadoop2.7/logs
#Polling period for the CsvSink specific for the worker instance
worker.sink.csv.period=10
#Unit of the polling period for the CsvSink specific for the worker instance
worker.sink.csv.unit=seconds

HiBench/conf/hibench.conf datasize
HiBench/conf/spark.conf master local[\*]