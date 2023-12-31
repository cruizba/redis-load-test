# Redis load test

Simple tool to load test redis write/read/delete operations.
Each goroutine will write and read a key, and then remove it.

Just run it with the following command:

```
docker run -it --rm ghcr.io/cruizba/redis-load-test:latest \
    -cluster=redis-1:6379,redis-2:6379,redis-3:6379 \
    -password=yourpassword \
    -goroutines 10 \
    -sleep 1s
```

- `cluster` is a comma separated list of redis nodes.
- `password` is the redis password.
- `goroutines` is the number of goroutines to use.
- `sleep` is the time to sleep between each write/read.

In case of errors, they will appear in the stout.

I've written this just to check redis faultolerance while starting and removing servers from a redis cluster.

> Note: This can polute your redis cluster, so don't use it in real production.

