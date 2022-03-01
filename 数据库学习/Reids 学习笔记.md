# 1.Redis 简介

## 1.1 redis 简介

redis 是跨平台的非关系型数据库。Redis是一个开源的使用ANSI C 语言编写、遵守BSD协议、支持网络、可基于内存、分布式、持久性的键值对（Key-Value)存储数据库，并提供多语言的API。

Redis 通常被称为数据结构服务器，因为值（value）可以是字符串(String)、哈希(Hash)、列表(list)、集合(sets)和有序集合(sorted sets)等类型。

Redis 与其他 key - value 缓存产品有以下三个特点：

- Redis支持数据的持久化，可以将内存中的数据保存在磁盘中，重启的时候可以再次加载进行使用。
- Redis不仅仅支持简单的key-value类型的数据，同时还提供list，set，zset，hash等数据结构的存储。
- Redis支持数据的备份，即master-slave模式的数据备份。

## 1.2 Redis 优势

- 性能极高 – Redis能读的速度是110000次/s,写的速度是81000次/s 。
- 丰富的数据类型 – Redis支持二进制案例的 Strings, Lists, Hashes, Sets 及 Ordered Sets 数据类型操作。
- 原子 – Redis的所有操作都是原子性的，意思就是要么成功执行要么失败完全不执行。单个操作是原子性的。多个操作也支持事务，即原子性，通过MULTI和EXEC指令包起来。
- 丰富的特性 – Redis还支持 publish/subscribe, 通知, key 过期等等特性。

1.3 Redis 与其他Key-Value 存储有什么不同？

## 1.3 Redis与其他key-value存储有什么不同？

- Redis有着更为复杂的数据结构并且提供对他们的原子性操作，这是一个不同于其他数据库的进化路径。Redis的数据类型都是基于基本数据结构的同时对程序员透明，无需进行额外的抽象。
- Redis运行在内存中但是可以持久化到磁盘，所以在对不同数据集进行高速读写时需要权衡内存，因为数据量不能大于硬件内存。在内存数据库方面的另一个优点是，相比在磁盘上相同的复杂的数据结构，在内存中操作起来非常简单，这样Redis可以做很多内部复杂性很强的事情。同时，在磁盘格式方面他们是紧凑的以追加的方式产生的，因为他们并不需要进行随机访问。

# 2.Redis 安装

## 2.1 windows 下安装

## 2.2 Centos Linux下安装

# 3. Redis 配置

Redis 的配置文件位于 Redis 安装目录下，文件名为 **redis.conf**(Windows 名为 redis.windows.conf)。

可以通过Config 命令查看或设置配置项

## 3.1查看配置项

**语法**

Redis Config  命令格式如下：

```sh
redis 127.0.0.1:6379> CONFIG GET CONFIG_SEETING_NAME
```

**实例**

```sh
127.0.0.1:6379> CONFIG GET loglevel
1) "loglevel"
2) "verbose"
```

使用 * 获取所有配置项

## 3.2 编辑配置项

你可以通过修改 redis.conf 文件或使用 **CONFIG set** 命令来修改配置。

**语法**

CONFIG SET 命令基本语法：

redis 127.0.0.1:6379> CONFIG SET CONFIG_SEETING_NAME NEW_CONFIG_VALUE

**实例**

```sh
127.0.0.1:6379> CONFIG SET loglevel "notice"
OK
127.0.0.1:6379> CONFIG GET loglevel
1) "loglevel"
2) "notice"
127.0.0.1:6379>
```

## 3.3 参数说明

| 序号 | 配置项                                               | 值                                                           | 说明                                                         |
| ---- | ---------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1    | daemonize   no                                       |                                                              | Redis 默认不是以守护进程的方式运行，可以通过该配置项修改，使用 yes 启用守护进程 |
| 2    | pidfile /var/run/redis.pid                           |                                                              | 当 Redis 以守护进程方式运行时，Redis 默认会把 pid 写入 /var/run/redis.pid 文件，可以通过 pidfile 指定 |
| 3    | port 6379                                            |                                                              | 指定 Redis 监听端口，默认端口为 6379，作者在自己的一篇博文中解释了为什么选用 6379 作为默认端口，因为 6379 在手机按键上 MERZ 对应的号码，而 MERZ 取自意大利歌女 Alessia Merz 的名字 |
| 4    | bind 127.0.0.1                                       |                                                              | 绑定的主机地址                                               |
| 5    | timeout  300                                         |                                                              | 当客户端闲置多长秒后关闭连接，如果指定为 0 ，表示关闭该功能  |
| 6    | loglevel  notice                                     |                                                              | 指定日志记录级别，Redis 总共支持四个级别：debug、verbose、notice、warning，默认为 notice |
| 7    | logfile stdout                                       |                                                              | 日志记录方式，默认为标准输出，如果配置 Redis 为守护进程方式运行，而这里又配置为日志记录方式为标准输出，则日志将会发送给 /dev/null |
| 8    | databases  16                                        |                                                              | 设置数据库的数量，默认数据库为0，可以使用SELECT 命令在连接上指定数据库id |
| 9    | save <seconds> <changes>                             | Redis 默认配置文件中提供了三个条件：**save 900 1**、**save 300 10**、**save 60 10000 ** 分别表示 900 秒（15 分钟）内有 1 个更改，300 秒（5 分钟）内有 10 个更改以及 60 秒内有 10000 个更改。 | 指定在多长时间内，有多少次更新操作，就将数据同步到数据文件，可以多个条件配合 |
| 10   | rdbcompression yes                                   |                                                              | 指定存储至本地数据库时是否压缩数据，默认为 yes，Redis 采用 LZF 压缩，如果为了节省 CPU 时间，可以关闭该选项，但会导致数据库文件变的巨大 |
| 11   | dbfilename dump.rdb                                  |                                                              | 指定本地数据库文件名，默认值为 dump.rdb                      |
| 12   | dir ./                                               |                                                              | 指定本地数据库存放目录                                       |
| 13   | slaveof <masterip><masterport>                       |                                                              | 设置当本机为 slave 服务时，设置 master 服务的 IP 地址及端口，在 Redis 启动时，它会自动从 master 进行数据同步 |
|      | masterauth <master-password>                         |                                                              | 当 master 服务设置了密码保护时，slave 服务连接 master 的密码 |
|      | requirepass foobared                                 |                                                              | 设置 Redis 连接密码，如果配置了连接密码，客户端在连接 Redis 时需要通过 AUTH <password> 命令提供密码，默认关闭 |
|      | maxclients 128                                       |                                                              | 设置同一时间最大客户端连接数，默认无限制，Redis 可以同时打开的客户端连接数为 Redis 进程可以打开的最大文件描述符数，如果设置 maxclients 0，表示不作限制。当客户端连接数到达限制时，Redis 会关闭新的连接并向客户端返回 max number of clients reached 错误信息 |
|      | maxmemory <bytes>                                    |                                                              | 指定 Redis 最大内存限制，Redis 在启动时会把数据加载到内存中，达到最大内存后，Redis 会先尝试清除已到期或即将到期的 Key，当此方法处理 后，仍然到达最大内存设置，将无法再进行写入操作，但仍然可以进行读取操作。Redis 新的 vm 机制，会把 Key 存放内存，Value 会存放在 swap 区 |
|      | appendonly  no                                       |                                                              | 指定是否在每次更新操作后进行日志记录，Redis 在默认情况下是异步的把数据写入磁盘，如果不开启，可能会在断电时导致一段时间内的数据丢失。因为 redis 本身同步数据文件是按上面 save 条件来同步的，所以有的数据会在一段时间内只存在于内存中。默认为 no |
|      | appendfilename appendonly.aof                        |                                                              | 指定更新日志文件名，默认为 appendonly.aof                    |
|      | vm-enabled no                                        |                                                              | 指定更新日志条件，共有 3 个可选值：**no**：表示等操作系统进行数据缓存同步到磁盘（快）**always**：表示每次更新操作后手动调用 fsync() 将数据写到磁盘（慢，安全）**everysec**：表示每秒同步一次（折中，默认值） |
|      | vm-swap-file /tmp/redis.swap                         |                                                              | 虚拟内存文件路径，默认值为 /tmp/redis.swap，不可多个 Redis 实例共享 |
|      | vm-max-memory 0                                      |                                                              | 将所有大于 vm-max-memory 的数据存入虚拟内存，无论 vm-max-memory 设置多小，所有索引数据都是内存存储的(Redis 的索引数据 就是 keys)，也就是说，当 vm-max-memory 设置为 0 的时候，其实是所有 value 都存在于磁盘。默认值为 0 |
|      | vm-page-size 32                                      |                                                              | Redis swap 文件分成了很多的 page，一个对象可以保存在多个 page 上面，但一个 page 上不能被多个对象共享，vm-page-size 是要根据存储的 数据大小来设定的，作者建议如果存储很多小对象，page 大小最好设置为 32 或者 64bytes；如果存储很大大对象，则可以使用更大的 page，如果不确定，就使用默认值 |
|      | vm-pages 134217728                                   |                                                              | 设置 swap 文件中的 page 数量，由于页表（一种表示页面空闲或使用的 bitmap）是在放在内存中的，，在磁盘上每 8 个 pages 将消耗 1byte 的内存。 |
|      | vm-max-threads 4                                     |                                                              | 设置访问swap文件的线程数,最好不要超过机器的核数,如果设置为0,那么所有对swap文件的操作都是串行的，可能会造成比较长时间的延迟。默认值为4 |
|      | glueoutputbuf yes                                    |                                                              | 设置在向客户端应答时，是否把较小的包合并为一个包发送，默认为开启 |
|      | hash-max-zipmap-entries 64 hash-max-zipmap-value 512 |                                                              | 指定在超过一定的数量或者最大的元素超过某一临界值时，采用一种特殊的哈希算法 |
|      | activerehashing yes                                  |                                                              | 指定是否激活重置哈希，默认为开启（后面在介绍 Redis 的哈希算法时具体介绍） |
|      | include /path/to/local.conf                          |                                                              | 指定包含其它的配置文件，可以在同一主机上多个Redis实例之间使用同一份配置文件，而同时各个实例又拥有自己的特定配置文件 |

# 4. Redis 数据类型

Redis 支持五种数据类型：string (字符串)、hash（哈希）、list (列表)、set (集合) 及 zset(sorted set：有序集合)。

## 4.1 String (字符串)

string 是 redis 最基本的类型，你可以理解成与 Memcached 一模一样的类型，一个key 对应一个 value.

string 类型是二进制安全的。意思是redis 的 string 可以包含任何数据。比如 jpg 图片或者序列化对象。

string 类型是Redis 最基本的数据类型，string 类型的值最大能存储512M。

**实例**

```sh
127.0.0.1:6379> SET testKey "testValue"
OK
127.0.0.1:6379> GET testKey
"testValue"
```

在以上实例中我们使用了 Redis 的 **SET** 和 **GET** 命令。键为 testKey，对应的值为 **testValue**。

注意：一个键最大能存储512M

## 4.2 hash （哈希）

Redis hash 是一个键值（key=>value）对集合。

Redis hash 是一个 string 类型的 field 和 value 的映射表， hash 特别适合用于存储对象。

**实例**

```sh
127.0.0.1:6379> HASET runoob field1 "hello" filed2 "world"
(error) ERR unknown command 'HASET'
127.0.0.1:6379> HMSET runoob field1 "hello" field2 "world"
OK
127.0.0.1:6379> HGET runoob field1
"hello"
```

实例中，我们使用了Redis HMSET,HGET命令HMSET设置了两个field=>value对，HGET获取对应field对应的value。

每个hash可以存储2<sup>32</sup> - 1 键值对（40多亿）。

## 4.3  List (列表)

Redis 列表是简单的字符串列表，按照插入顺序的排序。你可以添加一个元素列表的头部（左边）或者尾部（右边）。

**实例**

```
127.0.0.1:6379> lpush runoob redis
(integer) 1
127.0.0.1:6379> lpush runoob mongodb
(integer) 2
127.0.0.1:6379> lpush runoob rabbitmq
(integer) 3
127.0.0.1:6379> lrange runoob 0 1
1) "rabbitmq"
2) "mongodb"
127.0.0.1:6379> lrange runoob 0 0
1) "rabbitmq"
```

列表最多可存储 232 - 1 元素 (4294967295, 每个列表可存储40多亿)。

## 4.4 Set (集合)

Redis 的 Set  是string 类型的无序集合。

集合是通过哈希表实现的。所以，添加、删除、查找的复杂度都是O(1)。

**sadd命令**

添加一个string 元素到key对应的set集合，成功返回1，如果元素已经在集合中返回0。

```sh
sadd key member
```

**实例**

```sh
127.0.0.1:6379> sadd runoob redis
(integer) 1
127.0.0.1:6379> sadd runoob mogodb
(integer) 1
127.0.0.1:6379> sadd runoob mogodb
(integer) 0
127.0.0.1:6379> smembers runoob
1) "mogodb"
2) "redis"
```

以上实例中 mogodb添加了两次，但根据集合内元素的唯一性，第二次插入的元素将被忽略。

集合中最大的成员数为 232 - 1(4294967295, 每个集合可存储40多亿个成员)。

## 4.5 zset(sorted set:有序集合)

Redis zset 和set 一样也是string 类型元素的集合，且不允许重复的成员。

不同的是每个元素都会关联一个dobule类型的分数。redis 正是通过分数来为集合中的成员进行小到大的排序。

zset 的成员 是唯一的，但分数（score）却可以重复。

**zadd 命令**

添加元素到集合，元素在集合中存在则更新对应score

```sh
zadd key score memeber
```

**实例**

```sh
127.0.0.1:6379> zadd runoob 0 redis
(integer) 1
127.0.0.1:6379> zadd runoob 0 mongodb
(integer) 1
127.0.0.1:6379> zadd runoob 2 rabbitmq
(integer) 1
127.0.0.1:6379> zadd runoob 1 rocketmq
(integer) 1

127.0.0.1:6379> zrangebyscore runoob 0 10
1) "mongodb"
2) "redis"
3) "rocketmq"
4) "rabbitmq"
```

# 5.redis 命令

## 5.1 在远程服务上执行命令

**连接远程服务端语法**(windows客户端连接Linux 服务端Redis)

```sh
redis-cli -h host -p port -a passowrd
```



```sh
D:\redis\Redis-x64-3.2.100> .\redis-cli.exe -h 192.168.4.94 -p 6379 -a zoesoft@2021
192.168.4.94:6379>
```

## 5.2 Redis keys 命令

| 序号 | 命令                                      | 描述                                                         |
| ---- | ----------------------------------------- | ------------------------------------------------------------ |
| 1    | DEL key                                   | 该命令用于在 key 存在时删除 key。                            |
| 2    | DUMP key                                  | 序列化给定 key ，并返回被序列化的值。                        |
| 3    | EXISTS key                                | 检查给定 key 是否存在。                                      |
| 4    | EXPIRE key econds                         | 为给定key设置过期时间，以秒计。                              |
| 5    | EXPIREAT key timestamp                    | EXPIREAT 的作用和 EXPIRE 类似，都用于为 key 设置过期时间。 不同在于 EXPIREAT 命令接受的时间参数是 UNIX 时间戳(unix timestamp)。 |
| 6    | PEXPIRE key milliseconds                  | 设置 key 的过期时间以毫秒计。                                |
| 7    | PEXPIREAT key milliseconds-timestamp      | 设置 key 过期时间的时间戳(unix timestamp) 以毫秒计           |
| 8    | KEYS pattern                              | 查找所有符合给定模式( pattern)的 key 。                      |
| 9    | MOVE key db                               | 将当前数据库的key移动到给定的数据库db当中                    |
| 10   | PERSIS key                                | 移除 key 的过期时间，key 将持久保持。                        |
| 11   | PTTL key                                  | 以毫秒为单位返回 key 的剩余的过期时间。                      |
| 12   | TTL key                                   | 以秒为单位，返回给定 key 的剩余生存时间(TTL, time to live)。 |
| 13   | RANDOMKEY                                 | 从当前数据库中随机返回一个 key 。                            |
| 14   | RENAME key newkey                         | 修改 key 的名称                                              |
| 15   | RENAMENX key newkey                       | 仅当 newkey 不存在时，将 key 改名为 newkey 。                |
| 16   | SCAN cursor [MATCH pattern]\[Count count] | 迭代数据库中的数据库键。                                     |
| 17   | TYPE key                                  | 返回 key 所储存的值的类型。                                  |

## 5.3 Redis 字符串命令

| 序号 | 命令                         | 描述                                                         |
| ---- | ---------------------------- | ------------------------------------------------------------ |
| 1    | SET key value                | 设置指定key的值                                              |
| 2    | GET key                      | 获取指定key的值                                              |
| 3    | GETRANGE key start end       | 返回 key 中字符串值的子字符                                  |
| 4    | GETSET key value             | 将给定 key 的值设为 value ，并返回 key 的旧值(old value)。   |
| 5    | GETBIT key offset            | 对 key 所储存的字符串值，获取指定偏移量上的位(bit)。         |
| 6    | MGET key1[key...]            | 获取所有(一个或多个)给定 key 的值。                          |
| 7    | SETBIT key offset value      | 对 key 所储存的字符串值，设置或清除指定偏移量上的位(bit)。   |
| 8    | SETEX key seconds value      | 将值 value 关联到 key ，并将 key 的过期时间设为 seconds (以秒为单位)。 |
| 9    | SETNX key value              | 只有在 key 不存在时设置 key 的值。                           |
| 10   | SETRANGE key offset value    | 用 value 参数覆写给定 key 所储存的字符串值，从偏移量 offset 开始。 |
| 11   | STRLEN key                   | 返回 key 所储存的字符串值的长度。                            |
| 12   | MSET key value [key value]   | 同时设置一个或多个key-value对                                |
| 13   | MSETNT key value [key value] | 同时设置一个或多个 key-value 对，当且仅当所有给定 key 都不存在。 |
| 14   | PSETEX key millseconds value | 这个命令和 SETEX 命令相似，但它以毫秒为单位设置 key 的生存时间，而不是像 SETEX 命令那样，以秒为单位。 |
| 15   | INCR key                     | 将 key 中储存的数字值增一。                                  |
| 16   | INCRBY key increment         | 将 key 所储存的值加上给定的增量值（increment）               |
| 17   | INCRBYFLOAT key increment    | 将 key 所储存的值加上给定的浮点增量值（increment） 。        |
| 18   | DECR key                     | 将 key 中储存的数字值减一。                                  |
| 19   | DECRBY  key decrement        | key 所储存的值减去给定的减量值（decrement）                  |
| 20   | APPEND key value             | 如果 key 已经存在并且是一个字符串， APPEND 命令将指定的 value 追加到该 key 原来值（value）的末尾。 |

## 5.4 Redis 字符串命令