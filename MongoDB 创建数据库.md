###        树莓派 Mongo DB 的使用方法

1. 安装mongodb

   ```
   sudo apt-get install mongodb
   ```

2. 使用mongodb

   ```
   sudo mongo
   ```

   ### MongoDB 创建数据库



   MongoDB 创建数据库的语法格式如下：

   ```
   use DATABASE_NAME
   ```

   如果数据库不存在，则创建数据库，否则切换到指定数据库。

   ### 实例

   第一步启动mongoDB

   ```
   sudo mongo
   ```

   

   以下实例我们创建了数据库 runoob:

   ```
   > use runoob
   switched to db runoob
   > db
   runoob
   > 
   ```

   如果你想查看所有数据库，可以使用 **show dbs** 命令：

   ```
   > show dbs
   admin   0.000GB
   config  0.000GB
   local   0.000GB
   > 
   ```

   可以看到，我们刚创建的数据库 runoob 并不在数据库的列表中， 要显示它，我们需要向 runoob 数据库插入一些数据。

   ```
   > db.runoob.insert({"name":"测试文本"})
   WriteResult({ "nInserted" : 1 })
   > show dbs
   admin   0.000GB
   config  0.000GB
   local   0.000GB
   runoob  0.000GB
   ```

   MongoDB 中默认的数据库为 test，如果你没有创建新的数据库，集合将存放在 test 数据库中。

   > **注意:** 在 MongoDB 中，集合只有在内容插入后才会创建! 就是说，创建集合(数据表)后要再插入一个文档(记录)，集合才会真正创建。

