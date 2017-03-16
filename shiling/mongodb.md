# study
studyspringboot mongodb

mongdb常用命令

mongo 进入命令行 或 mongo + 数据库名字
show dbs 显示数据库列表
use + 数据库名字 使用指定数据库
show collections 显示当前数据库下的所有集合（类似表）

springboot配置mongodb在工程的application.properties或者是application.yaml中配置
spring:  
  data:  
    mongodb:  
      uri: mongodb://192.168.0.9:27017/test  test为数据库名
