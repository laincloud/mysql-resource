# MySQL Resource

## 1. Introduction

MySQL Resource是MySQL Service的Resource化。适用于需要独占MySQL实例的应用。其功能和MySQL Service类似，可以参考MySQL Service的[相关文档](http://github.com/laincloud/mysql-service/blob/master/README.md)。本文档只介绍Resource的配置。

## 2. Configuration

MySQL Resource为了满足不同规模的应用使用，目前提供了内存、`buffer_pool_size`和实例个数的配置，如下表：

|参数名称|类型|说明|默认值|
|:-:|:-:|:-:|:-:|
|memory|string|每个实例分配的内存大小，需要指定单位(M,m,g,G)|512M|
|pool_size|string|每个实例的`buffer_pool_size`，需要指定单位(M,m,g,G)|128M|
|num_instances|int|实例个数|3|

在lain.yaml中，一个标准的使用MySQL Resource的配置如下：

```yaml
use_resources:
	mysql-resource:
	    memory: 1G
	    pool_size: 256M
	    num_instances: 3
		services:
	        - mysql-master
	        - mysql-slave
```

## 3. Installation
MySQL-Reource的主体是MySQL-Service，在代码中MySQL-Service以git submodule的形式存在。因此克隆本代码仓库后并不会包含所有的MySQL-Service代码。
在构建前，需要执行
```sh
git submodule init
git submodule update
```

## 4. License
MySQL-Resource遵循[MIT](https://github.com/laincloud/mysql-resource/blob/master/LICENSE)开源协议。
