# redis-tips


# Create a lab cluster
```sh
mkdir redis-cluster
cd redis-cluster
mkdir 700{0..5}
```

### redis.conf
```ini
port 7000
cluster-enabled yes
cluster-config-file nodes.conf
cluster-node-timeout 5000
appendonly yes
protected-mode no
bind 127.0.0.1
dir /path/to/7000
```
```sh
cp redis.conf 7000/
sed -i s/7000/7001/ redis.conf
cp redis.conf 7001/
sed -i s/7001/7002/ redis.conf
cp redis.conf 7002/
sed -i s/7002/7003/ redis.conf
cp redis.conf 7003/
sed -i s/7003/7004/ redis.conf
cp redis.conf 7004/
sed -i s/7004/7005/ redis.conf
cp redis.conf 7005/
```

### Run
```sh
redis-server 7000/redis.conf &
redis-server 7001/redis.conf &
redis-server 7002/redis.conf &
redis-server 7003/redis.conf &
redis-server 7004/redis.conf &
redis-server 7005/redis.conf &
```

### Initiate Cluster
```sh
redis-cli --cluster create \
127.0.0.1:7000 127.0.0.1:7001 127.0.0.1:7002 \
127.0.0.1:7003 127.0.0.1:7004 127.0.0.1:7005 \
--cluster-replicas 1
```


### Test with redis-cli
```sh
redis-cli -c -p 7000
```
- Required `-c` to switch between nodes!
```cli
SET foo 1
SET bar 1
```
```cli
CLUSTER KEYSLOT foo
CLUSTER SLOTS
CLUSTER INFO
```







