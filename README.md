# Google-compute-engine-Redis-cluster-installation-guide
On each instance, run this:
```
git clone https://github.com/antirez/redis.git
sudo apt-get install -y gcc
cd redis/deps/
make hiredis jemalloc linenoise lua geohash-int
cd ..
make
sudo apt-get install -y tcl
make test
```
#Reference
http://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/Clusters.Create.CON.RedisCluster.html
http://docs.aws.amazon.com/AmazonElastiCache/latest/UserGuide/Replication.Redis-RedisCluster.html
