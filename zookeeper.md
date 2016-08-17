# ZooKeeper

## Installation (Single Development Machine)

* Download and extract the zookeeper distribution (e.g. `zookeeper-3.4.6.tar.gz`).

* Copy/rename the extracted directory to the following three directories:
    * `zk1`
    * `zk2`
    * `zk3`

* Inside the `conf` directory of each of these _zk*_ directories, put a file `zoo.cfg` with the following content:
```
    tickTime=2000
    dataDir=data
    clientPort=[PORT]
    initLimit=5
    syncLimit=2
    server.1=localhost:2888:3888
    server.2=localhost:2889:3889
    server.3=localhost:2887:3887
```

* Replace _[PORT]_ with 2181, 3181, and 4181, respectively.

* In each of the _zk*_ directories, create a directory `data`.

* In each of these `data` directories, create a file called `myid`.
Each file must contain a single number: _1_, _2_, or _3_, depending on which directory it is in.

* Optionally, edit logging configuration file `log4j.properties` in the `conf` directory
to disable logging to console, and enable rolling file appender.


## Running ZooKeeper

* To start each ZooKeeper instance as a background process, run the following command in each 
_zk*_ directory in turn: `bin/zkServer.sh start`.
Node: do not cd into `bin` or otherwise the `data` directory will not be found.

* To stop each zookeeper instance, run `bin/zkServer.sh stop` under its directory.


## Monitoring ZooKeeper

* To start the command line interface, run 'bin/zkCli.sh'. 
