blog-spark-recommendation
=========================

Simple example on how to use recommenders in Spark / MLlib using the Play framework.
More info on our blog: http://chimpler.wordpress.com/2014/07/22/building-a-food-recommendation-engine-with-spark-mllib-and-play/

UPDATE
2016/04/18

I am going to start with this project in order to learn more about how to build recomendation engines using spark.

More info in my blog http://aironman2k.wordpress.com

TODO

	update build.sbt to use latest versions of dependencies

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
