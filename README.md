# Cross-Device Graph calculation

Cross-Device Graph creation demo for "A billion nodes graph processing" workshop @ DataFest Tbilisi 2017. 

All the instructions below are present in the [Jupyter notebook](Cross-device-graph.html).

## Dependencies

The notebook requires 
1. Python, Jupyter, Spark and Apache Toree to be installed in order to run
1. A folder `anonymised-tracking-event-data`, containing ids to compute the graph from in the same directory as this notebook

## Installation

### 1. Install Python

This guid will cover MacOS installation, for any guidance for your OS, please check with [www.python.org](https://www.python.org/).

```
brew install python
```

### 2. Install Spark

This guid will cover MacOS installation, for any guidance for your OS, please check with [spark.apache.org](https://spark.apache.org/).

```
brew install apache-spark
```

Notice the installation path, it will be used further:
```
brew list apache-spark
```
On my machine it's (most of the output is replaced with "...")
```
/usr/local/Cellar/apache-spark/2.2.0/bin/find-spark-home
...
/usr/local/Cellar/apache-spark/2.2.0/libexec/jars/ (209 files)
...
```

### 3. Install Jupyter and Apache Toree

Use the following commands to install Jupyter and iPython kernel. iPython kernel is optional for this notebook, but a must for people who prefer Python to Scala.
```
pip install --upgrade jupyter
pip install --upgrade ipykernel
```

Use the following commands to install Apache Toree. Please make sure, that the `SPARK_HOME` path corresponds to the one reported earlier by `brew list apache-spark` or your spark installation directory if you are not running a MacOS.

```
pip install --upgrade https://dist.apache.org/repos/dist/dev/incubator/toree/0.2.0/snapshots/dev1/toree-pip/toree-0.2.0.dev1.tar.gz
```
```
SPARK_HOME=/usr/local/Cellar/apache-spark/2.2.0/libexec jupyter toree install --spark_opts='--conf "spark.jars.packages=graphframes:graphframes:0.5.0-spark2.1-s_2.11,org.knowm.xchart:xchart:3.5.0" --conf "spark.sql.parquet.binaryAsString=true" --conf "spark.executor.extraJavaOptions=-XX:+UseG1GC" --driver-memory 4g' --ToreeInstall.user=True
```

Note that the command above sets the following:
 * Toree will install GraphFrames Spark package as well as XChart charting library for you to be accessible in Toree notebooks
 * A G1 garbage collector is chosen – you can remove that setting if you don't want that
 * Spark's `--driver-memory` is set to be **4GB**

## Running

As long as everything is ready, just start the Jupyter and open this notebook. 
```
jupyter notebook
```

Go to [localhost:8888](localhost:8888) and navigate to this notebook. 

Have fun experimenting!
