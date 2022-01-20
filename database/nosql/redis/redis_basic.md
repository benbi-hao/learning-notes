# Redis基础
本文参考《Redis In Action》一书中的内容和实验指导，进行了实验，帮助学习Redis的基础理论知识。

## Redis简介

Redis是一个内存数据库、NoSQL数据库、Key-Value数据库。

## 启动、连接、关闭

1. 理论知识
- 启动
  - redis-server
  
redis-server是启动Redis服务的命令，默认在localhost:6379上开启服务。

- 连接
  - 使用redis-cli

redis-cli是Redis自带的客户端命令行工具，默认连接localhost:6379的服务。使用exit命令可以退出redis-cli客户端。

- 关闭
  - 使用redis-cli

在redis-cli命令行中使用shutdown命令关闭redis服务。

2. 相关实验
- 使用redis-server启动服务
```shell
$ redis-server
```
观察到Redis服务启动在了localhost的6379端口。
- 使用redis-cli连接服务
打开一个新的终端，使用下列命令连接开启的Redis服务
```shell
$ redis-cli
```
观察到连接的服务位于127.0.0.1:6379。
- 关闭服务
在redis-cli客户端上使用如下命令
```
> shutdown
```
观察到Redis服务被正常关闭，连接的服务变为unconnected。再使用如下命令退出redis-cli客户端
```
> exit
```


## 数据结构

1. 理论知识
- STRING
  - 描述
    
    Redis的字符串和其他编程语言或者其他键值存储提供的字符串非常相似。

  - 主要操作
    - GET 获取存储在给定键中的值
    - SET 设置存储在给定键中的值
    - DEL 删除存储在给定键中的值（这个命令可以用于所有类型）

- LIST
  - 描述

    Redis的列表是链表结构，可以有序地存储多个字符串。

  - 主要操作
    - RPUSH 将给定值推入表的右端
    - LRANGE 获取列表在给定范围上的所有值
    - LINDEX 获取列表在给定位置上的单个元素
    - LPOP 从列表的左端弹出一个值

- SET
  - 描述

    就是集合，使用无序方式存储元素。

  - 主要操作
    - SADD 将给定元素添加到集合
    - SMEMBERS 返回集合所包含的元素
    - SISMEMBER 检查给定的元素是否存在于集合中
    - SREM 如果给定的元素存在于集合中，那么移除这个元素

- HASH
  - 描述

    存储键值对映射，值可以是字符串也可以是数字值。

  - 主要操作
    - HSET 在散列里关联起给定的键值对
    - HGET 获取指定散列键的值
    - HGETALL 获取散列包含的所有键值对
    - HDEL 如果给定键存在于散列里面，那么移除这个键

- ZSET
  - 描述

    有序集合，其键值对中的键被称为成员（member），值被称为分值（score），分值必须为浮点数。只有有序集合既可以根据成员访问元素，又可以根据分值以及分值的排列顺序访问元素。

  - 主要操作
    - ZADD 将一个带有给定分值的成员添加到有序集合里面
    - ZRANGE 根据元素在有序排列中所处的位置，从有序集合里面获取多个元素
    - ZRANGEBYSCORE 获取有序集合在给定分值范围内的所有元素
    - ZREM 如果给定成员存在于有序集合，那么移除这个成员

2. 相关实验
- 启动Redis服务
```shell
$ redis-server
```
- 连接Redis服务
```shell
$ redis-cli
```
在redis-cli中运行如下命令
- STRING
```
> set hello world
OK
> get hello
"world"
> del hello
(integer) 1
> get hello
(nil)
```

- LIST
```
> rpush list-key item
(integer) 1                     // 返回操作完成后列表的长度
> rpush list-key item2
(integer) 2
> rpush list-key item
(integer) 3
> lrange list-key 0 -1
1) "item"
2) "item2"
3) "item"
> lindex list-key 1
"item2"
> lpop list-key
"item"
> lrange list-key 0 -1
1) "item2"
2) "item"
```

- SET
```
> sadd set-key item
(integer) 1                         // sadd返回1表示添加元素成功
> sadd set-key item2
(integer) 1
> sadd set-key item3
(integer) 1
> sadd set-key item
(integer) 0                         // sadd返回0表示要添加的元素已在集合中
> smembers set-key
1) "item3"
2) "item2"
3) "item"
> sismember set-key item4
(integer) 0                         // sismember返回布尔值表示结果
> sismember set-key item
(integer) 1                         
> srem set-key item2
(integer) 1                         // srem返回被移除元素的数量
> srem set-key item2
(integer) 0
> smembers set-key
1) "item3"
2) "item"
```

- HASH
```
> hset hash-key sub-key1 value1
(integer) 1                         // 返回1表示给定的键之前不存在于散列中
> hset hash-key sub-key2 value2
(integer) 1
> hset hash-key sub-key1 value1
(integer) 0                         // 返回0表示给定的键已存在与散列中
> hgetall hash-key
1) "sub-key1"
2) "value1"
3) "sub-key2"
4) "value2"
> hdel hash-key sub-key2            // 返回1表示给定的键之前存在于散列中
(integer) 1
> hdel hash-key sub-key2
(integer) 0                         // 返回0表示给定的键之前不存在与散列中
> hget hash-key sub-key1
"value1"
> hgetall hash-key
1) "sub-key1"
2) "value1"
```

- ZSET
```
127.0.0.1:6379> zadd zset-key 728 member1
(integer) 1                         // 返回新添加元素的数量
127.0.0.1:6379> zadd zset-key 982 member0
(integer) 1
127.0.0.1:6379> zadd zset-key 982 member0
(integer) 0
127.0.0.1:6379> zrange zset-key 0 -1 withscores
1) "member1"                        // 获取有序集合包含的元素时，多个元素按照分值大小进行排序
2) "728"
3) "member0"
4) "982"
127.0.0.1:6379> zrangebyscore zset-key 0 800 withscores
1) "member1"                        // 也可以根据分值范围获取一部分元素
2) "728"
127.0.0.1:6379> zrem zset-key member1
(integer) 1                         // 返回被移除元素的数量
127.0.0.1:6379> zrem zset-key member1
(integer) 0
127.0.0.1:6379> zrange zset-key 0 -1 withscores
1) "member0"
2) "982"
```



