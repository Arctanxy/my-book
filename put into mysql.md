二手房交易网站中爬取房价信息，并存储到MySQL数据库中

```Python
def printgoods(itl):
    tplt = "{:2}\t{:8}\t{:16}"
    print(tplt.format("序号", "价格", "商品名称"))

    count = 0
    conn = pymysql.connect(host='127.0.0.1', user='root', password='123456', db='company',charset="utf8")

    cur = conn.cursor()

    sqlc = '''
                create table coffee(
                id int(11) not null auto_increment primary key,
                name varchar(255) not null,
                price float not null)DEFAULT CHARSET=utf8;
                '''

    try:
        A = cur.execute(sqlc)
        conn.commit()
        print('成功')
    except:
        print("错误")
    for g in itl:
        count = count + 1
        b=tplt.format(count, g[0], g[1])



        sqla = '''
        insert into  coffee(name,price)
        values(%s,%s);
       '''
        try:
            B = cur.execute(sqla,(g[1],g[0]))
            conn.commit()
            print('成功')
        except:
            print("错误")

        # save_path = 'D:/taobao.txt'
        # f=open(save_path,'a')
        #
        # f.write(b+'\n')
        # f.close()

    conn.commit()
    cur.close()
    conn.close()
```
```Python
    def storeDB(self,table,news):
        #use dict store news
        news_date = time.strftime('%Y-%m-%d',time.localtime(time.time()))
        news_time = time.strftime('%Y-%m-%d %H:%M:%S',time.localtime(time.time()))
        #test insert only 1 record
        text = "'" + news[0] + "'"  #Chinese character and symbol
        time_now = "'" + news_time + "'"
        date = "'" + news_date + "'"

        #connect mysqlDB
        conn = pymysql.connect(
            host='127.0.0.1', 
            port=3306, 
            user='root', 
            passwd='root', 
            db='test',
            use_unicode=1,
            charset='utf8')

        try:
            with conn.cursor() as cursor:
                #create a table
                sql = """CREATE TABLE IF NOT EXISTS %s (
                            text  VARCHAR(200),
                            time  VARCHAR(200),
                            date VARCHAR(200))""" % (table,)
                cursor.execute(sql)
                # Create a new record
                sql = "INSERT INTO %s (%s,%s,%s) VALUES (%s,%s,%s)" % (table, 'text', 'date', 'time', text, date, time_now)
                cursor.execute(sql)
                # connection is not autocommit by default. So you must commit to save
                # your changes.
                conn.commit()

            with conn.cursor() as cursor:
                # Read all records
                sql = "SELECT * FROM (%s) " %(table,)
                cursor.execute(sql)
                result = cursor.fetchall()
                print(result)
                cursor.close()
        finally:
            conn.close()
```
