# Dockerfile Maven
[![License](https://img.shields.io/github/license/spotify/dockerfile-maven.svg)](LICENSE)

资产云通用流程中心，基于[flowable]二次开发

[flowable]: https://github.com/flowable/flowable-engine


## 环境要求

`java 8`
`mysql` 
`maven 3`

## 启动

新建数据库，运行abpm-process-center/src/main/resources/sql下[abpm.sql]文件

[abpm.sql]:https://github.com/assetcloud/assetBPM/blob/master/abpm-process-center/src/main/resources/sql/abpm.sql

修改以下配置文件

abpm-process-center/src/main/resources/flowable.cfg.xml `数据库连接`
abpm-process-center/src/main/resources/application.properties `spring.profiles.active`
abpm-process-center/src/main/resources/config/database/jdbc-dev.properties `数据库连接`
abpm-process-center/src/main/resources/config/database/jdbc-test.properties `数据库连接`

运行com.asset.FlowableApplication ，访问 [http//:localhost:9000] 

## docker部署

搭建horbor私库
pom.xml需配置私库地址`docker.registry.url`。
如果是域名，必须使用https
配置docker 
docker login 私库地址


构建镜像 
```
mvn dockerfile:build
```
推送镜像
```
mvn dockerfile:push
```
