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
