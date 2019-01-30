
# YCSB
## 1 workload
执行时通过 `-P` 指定 workload 文件，参数都在类 `Workload` 和 `CoreWorkload` 中  
常用以下参数

load 阶段

参数 | 属性名 | 含义
:-:|:-:|:-:
fieldcount | FIELD_COUNT_PROPERTY | 一条记录中的列数
fieldlength | FIELD_LENGTH_PROPERTY | 列的大小
recordcount | RECORD_COUNT_PROPERTY | 记录条数
table | TABLENAME_PROPERTY | 表名
insertorder | INSERT_ORDER_PROPERTY | 生成 key 的方式，顺序 or hash

run 阶段

参数 | 属性名 | 含义
:-:|:-:|:-:
operationcount | OPERATION_COUNT_PROPERTY | 操作次数
readproportion | READ_PROPORTION_PROPERTY | 读比例
updateproportion | UPDATE_PROPORTION_PROPERTY | 更新比例
insertproportion | INSERT_PROPORTION_PROPERTY | 插入比例
scanproportion | SCAN_PROPORTION_PROPERTY | 扫描比例

## 2 build
    mvn -pl com.yahoo.ycsb:mongodb-binding -am clean package

构建完成后在对应数据库的目录下的 target 目录里可以找到一个 gz 文件

## 3 some key points
### functions
- buildKeyName
- doInsert: load 阶段使用

### var
- keysequence: key 的生成器

# RocksDBClient
类 `RocksDBClient`  
- rocksdb.dir: 数据库目录
- CF_NAMES: 列簇名

**ATTENTION**  
阅读 CF_NAMES 相关的代码可知，要在 `$rocksdb.dir$
` 目录下生成一个 CF_NAMES 文件，文件里写入列簇名(表名，rocksdb 默认有个 default)

# reference
<https://github.com/brianfrankcooper/YCSB/wiki/Core-Properties>