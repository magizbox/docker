# Redis

![](http://media.charlesleifer.com/blog/photos/p1432653421.74.png)

Redis is an open source (BSD licensed), in-memory data structure store, used as database, cache and message broker. [^1]

It supports data structures such as strings, hashes, lists, sets, sorted sets with range queries, bitmaps, hyperloglogs and geospatial indexes with radius queries.

Redis has built-in replication, Lua scripting, LRU eviction, transactions and different levels of on-disk persistence, and provides high availability via Redis Sentinel and automatic partitioning with Redis Cluster.

[^1]: [Redis.io](http://redis.io/)

# Redis: Client

## Python Client

[pipy/redis](https://pypi.python.org/pypi/redis)

Installation

```
pip install redis
```

Usage

```
import redis
r = redis.StrictRedis(host='localhost', port=6379, db=0)
r.set('foo', 'bar')
-> True

r.get('foo')
-> 'bar'

r.delete('foo')

# after delete
r.get('foo')
-> None
```

## Java Client

[https://redislabs.com/redis-java](https://redislabs.com/redis-java)

# Redis: Docker

### Docker Run

```
docker run -d -p 6379:6379 redis
```

### Docker Compose

```
version: "2"

services:
 redis:
  image: redis
  ports:
   - 6379:6379
```
