======
My SQL
======

-------------------------------------------------
Setting up MySQL replication without the downtime
-------------------------------------------------

https://plusbryan.com/mysql-replication-without-downtime

------------------------------------------
mysql.sock文件作用（轉）
------------------------------------------

這個mysql.sock應該是mysql的主機和客戶機在同一主機上的時候，使用unix domain socket做為通訊協議的載體，它比tcp快通常遇到這個問題的原因就是你的mysql服務器沒運行起來。

Mysql有兩種連接方式：
（1），TCP / IP
（2），socket
對於mysql.sock來說明，其作用是程序與mysqlserver處於同一台機器，發起本地連接時可用。
例如你無須定義連接主機的具體IP得，只要為空或localhost就可以。
在這種情況下，即使你改變mysql的外部port也是一樣可能正常連接。
因為你在my.ini中或my.cnf中改變端口後，mysql.sock是隨每一次mysql server啟動生成的。已經根據你在更改完my.cnf後重啟mysql時間重新生成了一次，信息已跟著變更。

那麼對於外部連接，必須是要更改port才能連接的。

linux下安裝mysql連接的時候經常回提示說找不到mysql.sock文件，解決辦法很簡單：

如果是新安裝的mysql，提示找不到文件，就搜索下，指定正確的位置。

如果mysql.sock文件誤刪的話，就需要重啟mysql服務，如果重啟成功的話會在datadir目錄下面生成mysql.sock到時候指定即可。

如果還不行就選擇用TCP連接方式連接就行了，其實windows下還支持管道連接方式。

Source: http://0001111.iteye.com/blog/1418638}{http://0001111.iteye.com/blog/1418638
