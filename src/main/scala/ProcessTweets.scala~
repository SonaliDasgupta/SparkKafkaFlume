import org.apache.spark.streaming._
import org.apache.spark.streaming.flume.FlumeUtils
import org.apache.spark.{SparkConf, SparkContext}
import org.apache.spark.sql.SQLContext
//import org.apache.spark.sql.SQLContext.implicits._
object ProcessTweets{

	def main(args: Array[String]){
		val sparkConf=new SparkConf().setAppName("Flafka")
		val sc=new SparkContext(sparkConf)
		val ssc=new StreamingContext(sc,Seconds(5))
		val stream=FlumeUtils.createPollingStream(ssc,"localhost",9988)
		val sqlContext=new SQLContext(sc)
		import sqlContext.implicits._
		val tweets=stream.map(e=> new String(e.event.getBody.array))
	//	if(tweets.count()!=0)
	//		tweets.saveAsTextFiles("/user/hive/warehouse/tweets")
		tweets.foreachRDD{
		rdd=> //if(df_tweets.count()>0)
	//		df_tweets=df_tweets.unionAll(rdd.toDF())
	//		else
				var df_tweets=rdd.toDF()
		

		
		df_tweets.registerTempTable("tweets")
	//	val sqlContext=new SQLContext(sc)
		sqlContext.sql("select count(*) from tweets")	
		sqlContext.sql("describe tweets")
	}
		ssc.start()
		ssc.awaitTermination()
	}
}
	
