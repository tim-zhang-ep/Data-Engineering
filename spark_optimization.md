```
# framework


driver  -   ----   ------------------   worker: JVM * 1
job (action)                                    executor * 1
stg (wide dependency)                           [core] * 4 -> [task] (compute perspective), [partition] (memory perspective)   
task                                    broadcast??
                                        cache??
                                        
wide dependency: 
- 一个父RDD partition对应多个子RDD partition, 有shuffle(一个父分区经过shuffle划分到子RDD不同分区)
- something cannot be done internally in a single worker, take all data shuffle around (write and read) put it back to those workers






# optimization 

spark-submit -> UI

observe 
  - Jobs (action) and Stages (wide dependency)
    卡在哪个stg (parallism) 哪个task (data skew) 多大data volume?？# of records??
    shuffle spill说明什么??
  - Executor
  - SQL (query plan)
    query plan：phycical query plan optimization, predicate pushdown， 高效sql
    data volume

optimization 
  - data perspective
    reduce data [volume] - [preaggregate]
  - spark mechanism perspective
    avoid shuffle - [broadcast]大小表
    avoid skew - [repartition]: sortPartitioner vs hashPartitioner, partitionBy
               - hot key [union]
    avoid recompute - [cache], stg table, view
  - resource perspective
    [partition] parrallism - default shuffle partition, partition vs shuffle write I/O 
    [executor-core] vs [memory(GC)]
    
    

```


```

# db desgin

index - sort??
partition - predication pushdown
physical query plan??

- schema design best practice (fact dimension scd, redundency norm)



```
