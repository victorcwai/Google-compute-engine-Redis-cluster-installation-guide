# Google-compute-engine-Redis-cluster-installation-guide

Using Ubuntu 14.04, done with 5 instances. On each instance, run this:

```
git clone https://github.com/antirez/redis.git
sudo apt-get install -y gcc
cd redis/deps/
make hiredis jemalloc linenoise lua geohash-int
cd ..
make
sudo apt-get install -y tcl
make test

mkdir cluster-test
cd cluster-test
#mkdir for 5 ports on 5 instances example
mkdir 7000 7001 7002 7003 7004 

#cd to directory of the current instance's port number
cd 7000
sudo vim redis.conf
#content
port 7000 #use different port for different instances
cluster-enabled yes
cluster-config-file nodes.conf
cluster-node-timeout 5000
appendonly yes
#content end

cp ../../src/redis-server ..
#run the server
../redis-server ./redis.conf

#create the cluster

```
# Reference
https://redis.io/topics/cluster-tutorial

https://github.com/antirez/redis

http://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/Clusters.Create.CON.RedisCluster.html

http://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/Replication.Redis-RedisCluster.html
