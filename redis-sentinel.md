# Redis Sentinel Architecture Lab
```sh
mkdir -p /opt/redis/{master,replica1,replica2,sentinel1,sentinel2,sentinel3}
```

### redis.conf
/opt/redis/master/redis.conf
```ini
port 6379
bind 0.0.0.0
protected-mode no

dir /opt/redis/master
appendonly yes
```


/opt/redis/replica1/redis.conf
```ini
port 6380
bind 0.0.0.0
protected-mode no

replicaof 127.0.0.1 6379
dir /opt/redis/replica1
appendonly yes
```

/opt/redis/replica2/redis.conf
```ini
port 6381
bind 0.0.0.0
protected-mode no

replicaof 127.0.0.1 6379
dir /opt/redis/replica2
appendonly yes
```
