# SparkKafkaFlume
Spark streaming and Spark SQL integration with Flume using Kafka Channel

Ensure Spark is up and running.

To run, first start kafka server and create a Kafka producer with topic 'Twitter'.

Then run the Spark-Submit job with the jar in the target/scala-2.11 folder. Ensure atleast 8 GB memory configured for the job.

Start the Flume agent to receive the tweets, process them and store into tables. Analyze on the go using SQL!!
