注：从60题开始免费，故从此开始

### No.60

[**SQL60** **从 Customers 表中检索所有的 ID**](https://www.nowcoder.com/practice/009199576d094b56807a8368058841ee)

```sql
select cust_id from Customers
```

### No.61

[**SQL61** **检索并列出已订购产品的清单**](https://www.nowcoder.com/practice/9e4741b77f4244149a069883bc0d23be)

```sql
select distinct(prod_id) from OrderItems
```

### No.62

[**SQL62** **检索所有列**](https://www.nowcoder.com/practice/cf0e3919ba8e4fa2ba19ea09df7fb756)

```sql
select * from Customers 
```

### No.63

[**SQL63** **检索顾客名称并且排序**](https://www.nowcoder.com/practice/6cfabb1b49554c4c8d8f9977bf6a3a5d)

```sql
select cust_name from Customers order by cust_name DESC
```

### No.64

[**SQL64** **对顾客ID和日期排序**](https://www.nowcoder.com/practice/fa4eb4880d124a4ead7a9b025fe75b70)

```sql
select cust_id , order_num
from Orders
order by cust_id , order_date DESC
```

