# note

事务的ACID特性
    原子性 atomicity
		事务中的所有操作要么全部成功，要么全部失败，不存在成功一部分，这就是事务的原子性
    一致性 consconsistency
		数据库中的状态只能从一个一致性状态变成另一个一致性状态，即使中途系统崩溃了，也不会处于一种中间态，因为没有提交事务
    隔离性 isolation
        “通常来说”，一个事务所做的内容在没有提交之前，对于其他事务是不可见的。
    持久性 duradurability
        一旦事务提交，所做的修改会永久得保存到数据库中，这时候即使系统崩溃了，修改的数据也不会丢失


死锁
两个或多个事务在同个资源上相互占用，并请求锁定对方占用的资源，从而导致的恶性循环现象
1   START TRANSACTION;
    UPDATE StockPrice SET close = 45.50 WHERE stock_id = 4 and date = '2002-05-01';
    UPDATE StockPrice SET close = 19.80 WHERE stock_id = 3 and date = '2002-05-02';
    COMMIT;
    
2   START TRANSACTION;
    UPDATE StockPrice SET high = 20.12 WHERE stock_id = 3 and date = '2002-05-02';
    UPDATE StockPrice SET high = 47.20 WHERE stock_id = 4 and date = '2002-05-01';
    COMMIT;
    
 
