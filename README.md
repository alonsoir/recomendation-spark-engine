blog-spark-recommendation
=========================

Simple example on how to use recommenders in Spark / MLlib using the Play framework.
More info on our blog: http://chimpler.wordpress.com/2014/07/22/building-a-food-recommendation-engine-with-spark-mllib-and-play/

UPDATE
2016/04/18

I am going to start with this project in order to learn more about how to build recomendation engines using spark.

More info in my blog http://aironman2k.wordpress.com

TODO

	update build.sbt to use latest versions of dependencies. 
	There is a problem with dependencies, i cannot upgrade spark and akka to latest versions
	so i am going to update first spark dependencies and disable everything related with akka and play...	
	
	Add movielensALS to project 
Setup
=====

You will need:

* Scala 2.10+
* Play Framework
* MongoDB

Download the food review file (500K reviews) using the `download.sh` script.

Running the example
===================

    $ cd $YOUR_PROJECT_FOLDER
    $ sbt
    $ play package run



	$ YOUR-SPARK-FOLDER/spark-1.6/bin/spark-submit --driver-memory 2g --class MovieLensALS target/scala-2.10/movielens-als_2.10-0.1.jar /FOLDER-MOVIES FOLDER/personalRatings.txt
	Using Spark's default log4j profile: org/apache/spark/log4j-defaults.properties
	16/04/19 13:56:25 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
	16/04/19 13:56:26 INFO Slf4jLogger: Slf4jLogger started
	16/04/19 13:56:26 INFO Remoting: Starting remoting
	16/04/19 13:56:26 INFO Remoting: Remoting started; listening on addresses :[akka.tcp://sparkDriverActorSystem@192.168.1.34:56275]
	16/04/19 13:56:28 WARN : Your hostname, MacBook-Pro-Retina-de-Alonso.local resolves to a loopback/non-reachable address: fe80:0:0:0:2080:c7:ea77:cc77%utun0, but we couldn't find any external IP address!
	16/04/19 13:56:33 INFO FileInputFormat: Total input paths to process : 1
	16/04/19 13:56:33 INFO deprecation: mapred.tip.id is deprecated. Instead, use mapreduce.task.id
	16/04/19 13:56:33 INFO deprecation: mapred.task.id is deprecated. Instead, use mapreduce.task.attempt.id
	16/04/19 13:56:33 INFO deprecation: mapred.task.is.map is deprecated. Instead, use mapreduce.task.ismap
	16/04/19 13:56:33 INFO deprecation: mapred.task.partition is deprecated. Instead, use mapreduce.task.partition
	16/04/19 13:56:33 INFO deprecation: mapred.job.id is deprecated. Instead, use mapreduce.job.id
	16/04/19 13:56:33 INFO FileInputFormat: Total input paths to process : 1
	Got 10000054 ratings from 69878 users on 10677 movies.                          
	Training: 6002484, validation: 1999675, test: 1997906                           
	16/04/19 13:57:00 WARN BLAS: Failed to load implementation from: com.github.fommil.netlib.NativeSystemBLAS
	16/04/19 13:57:00 WARN BLAS: Failed to load implementation from: com.github.fommil.netlib.NativeRefBLAS
	16/04/19 13:57:00 WARN LAPACK: Failed to load implementation from: com.github.fommil.netlib.NativeSystemLAPACK
	16/04/19 13:57:00 WARN LAPACK: Failed to load implementation from: com.github.fommil.netlib.NativeRefLAPACK
	RMSE (validation) = 0.8238705536926691 for the model trained with rank = 8, lambda = 0.1, and numIter = 10.
	RMSE (validation) = 0.8176944784396943 for the model trained with rank = 8, lambda = 0.1, and numIter = 20.
	RMSE (validation) = 3.667982949261605 for the model trained with rank = 8, lambda = 10.0, and numIter = 10.
	RMSE (validation) = 3.667982949261605 for the model trained with rank = 8, lambda = 10.0, and numIter = 20.
	RMSE (validation) = 0.8220343829870203 for the model trained with rank = 12, lambda = 0.1, and numIter = 10.
	RMSE (validation) = 0.8156340429261287 for the model trained with rank = 12, lambda = 0.1, and numIter = 20.
	RMSE (validation) = 3.667982949261605 for the model trained with rank = 12, lambda = 10.0, and numIter = 10.
	RMSE (validation) = 3.667982949261605 for the model trained with rank = 12, lambda = 10.0, and numIter = 20.
	The best model was trained with rank = 12 and lambda = 0.1, and numIter = 20, and its RMSE on the test set is 0.8157463251391568.
	The best model improves the baseline by 23,03%.
	Movies recommended for you:
	 1: Maradona by Kusturica (2008)
	 2: Shadows of Forgotten Ancestors (1964)
	 3: Constantine's Sword (2007)
	 4: Godfather, The (1972)
	 5: Another Man's Poison (1952)
	 6: Somebody Up There Likes Me (1956)
	 7: Godfather: Part II, The (1974)
	 8: December 7th (1943)
	 9: Power of Nightmares: The Rise of the Politics of Fear, The (2004)
	10: Tunnel, The (Der Tunnel) (2001)
	11: Wetherby (1985)
	12: Shoah (1985)
	13: Human Condition III, The (Ningen no joken III) (1961)
	14: Purple Butterfly (Zi hudie) (2003)
	15: Shawshank Redemption, The (1994)
	16: Casablanca (1942)
	17: Unreasonable Man, An (2006)
	18: Bridge on the River Kwai, The (1957)
	19: Mafioso (1962)
	20: Island of Lost Souls (1932)
	21: Hole, The (a.k.a. Night Watch, The) (Trou, Le) (1960)
	22: Patton (1970)
	23: Saving Private Ryan (1998)
	24: Raiders of the Lost Ark (Indiana Jones and the Raiders of the Lost Ark) (1981)
	25: Before the Fall (NaPolA - Elite für den Führer) (2004)
	26: Where the Sidewalk Ends (1950)
	27: Double Indemnity (1944)
	28: Detective Story (1951)
	29: Goodfellas (1990)
	30: Bad Blood (Mauvais sang) (1986)
	31: Close-Up (Nema-ye Nazdik) (1990)
	32: Seven Samurai (Shichinin no samurai) (1954)
	33: Lawrence of Arabia (1962)
	34: Sergeant York (1941)
	35: One Flew Over the Cuckoo's Nest (1975)
	36: Silence of the Lambs, The (1991)
	37: Schindler's List (1993)
	38: Great Escape, The (1963)
	39: 12 Angry Men (1957)
	40: Dark Knight, The (2008)
	41: Good, the Bad and the Ugly, The (Buono, il brutto, il cattivo, Il) (1966)
	42: Odds Against Tomorrow (1959)
	43: Usual Suspects, The (1995)
	44: Hanzo the Razor: Sword of Justice (Goyôkiba) (1972)
	45: Sting, The (1973)
	46: Rear Window (1954)
	47: Best of Youth, The (La Meglio gioventù) (2003)
	48: Shooting Dogs (a.k.a. Beyond The Gates) (2005)
	49: It's a Wonderful Life (1946)
	50: Eve and the Fire Horse (2005)
	took 239 seconds...
	16/04/19 14:00:25 INFO RemoteActorRefProvider$RemotingTerminator: Shutting down remote daemon.
	16/04/19 14:00:25 INFO RemoteActorRefProvider$RemotingTerminator: Remote daemon shut down; proceeding with flushing remote transports.