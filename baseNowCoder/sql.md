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

### No.65

[**SQL65** **按照数量和价格排序**](https://www.nowcoder.com/practice/bd05a6684e534bd1bf2d9ebbda475333)

```sql
select quantity,item_price from OrderItems  order by quantity desc ,item_price desc 
```

### No.66

[**SQL66** **检查SQL语句**](https://www.nowcoder.com/practice/ba2d42708239429e870fa80db81c07da)

```sql
SELECT vend_name
FROM Vendors 
ORDER by vend_name DESC;
```

### No.67

[**SQL67** **返回固定价格的产品**](https://www.nowcoder.com/practice/9949bfb933614abe8bd2bc26c129843e)

```sql
select prod_id,prod_name from Products where prod_price = 9.49
```

### No.68

[**SQL68** **返回更高价格的产品**](https://www.nowcoder.com/practice/f6153be7485448cdb444279dcc105cb8)

```sql
select prod_id,prod_name from Products where prod_price >= 9
```

### No.69

[**SQL69** **返回产品并且按照价格排序**](https://www.nowcoder.com/practice/560c94bf434e4e77911982e2d7ca0abb)

```sql
select prod_name,prod_price from Products  where prod_price <= 6 and prod_price >= 3 order by prod_price
```

### No.70

[**SQL70** **返回更多的产品**](https://www.nowcoder.com/practice/dc91b7d2de3c4603a55995e83210f605)

```sql
select distinct order_num from OrderItems where quantity >= 100
```

### No.71

[**SQL71** **检索供应商名称**](https://www.nowcoder.com/practice/c4d520ed6a264ad3900eff95e4195d59)

```sql
select vend_name from Vendors where vend_country = "USA" and vend_state = "CA"
```

### No.72

[**SQL72** **检索并列出已订购产品的清单**](https://www.nowcoder.com/practice/674d99a46a96494d8267ae4d162ed459)

```sql
select order_num ,prod_id,quantity from OrderItems where quantity >= 100 order by prod_id,quantity DESC
```

### No.73

[**SQL73** **返回所有价格在 3美元到 6美元之间的产品的名称和价格**](https://www.nowcoder.com/practice/e4268b4e044e4b94875c238098d98cf8)

```sql
select prod_name , prod_price from Products where prod_price >= 3 and prod_price <= 6 order by prod_price
```

### No.74

[**SQL74** **纠错2**](https://www.nowcoder.com/practice/ec773e81e8084d70bc62fd9012eabae5)

```sql
SELECT
    vend_name
FROM
    Vendors
WHERE
    vend_country = "USA"
    AND vend_state = "CA"
ORDER BY
    vend_name
```

