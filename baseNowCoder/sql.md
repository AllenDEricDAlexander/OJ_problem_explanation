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

### No.75

[**SQL75** **检索产品名称和描述（一）**](https://www.nowcoder.com/practice/47e8101cb2b447038effcf5159e6aa7f)

```sql
select
    *
from
    Products
where
    prod_desc like "%toy%"
```

### No.76

[**SQL76** **检索产品名称和描述（二）**](https://www.nowcoder.com/practice/669913837a7648f9aa0caaf6a88c834f)

```sql
select
    *
from
    Products
where
    instr (prod_desc, "toy") = 0
order by
    prod_name asc
```

```sql
select
    prod_name,
    prod_desc
from
    Products
where
    prod_desc not like "%toy%"
order by
    prod_name asc
```

```sql
select
    prod_name,
    prod_desc
from
    Products
where
    locate ("toy", prod_desc) = 0
order by
    prod_name asc
```

### No.77

[**SQL77** **检索产品名称和描述（三）**](https://www.nowcoder.com/practice/4302920bc3da44169a3ac458eb549d01)

```sql
select
    prod_name,
    prod_desc
from
    Products
where
    prod_desc like "%toy%"
    and prod_desc like "%carrots %"
```

```sql
select prod_name,prod_desc
from Products
# where prod_desc like '%toy%' and prod_desc like '%carrots%';#行
# where prod_desc like '%toy%' and '%carrots%';不行
where prod_desc like '%carrots%toy%';#行
# where prod_desc like '%toy%carrots%';不行
```

### No.78

[**SQL78** **检索产品名称和描述（四）**](https://www.nowcoder.com/practice/a9099944fa9c4cf0b7e406f22ee8c9a0)

```sql
select
    prod_name,
    prod_desc
from
    Products
where
    prod_desc like "%toy%carrots%"
```

### No.79

[**SQL79** **别名**](https://www.nowcoder.com/practice/3a4ec448b6f74dc49f886692887aaf84)

```sql
select
    vend_id,
    vend_name as vname,
    vend_address as vaddress,
    vend_city as vcity
from
    Vendors
order by
    vname
```

### No.80

[**SQL80** **打折**](https://www.nowcoder.com/practice/90bb4ccf41b24f3fa7e5f460ff6ee7cd)

```sql
select
    prod_id,
    prod_price,
    prod_price * 0.9 as sale_price
from
    Products
```

### No.81

[**SQL81** **顾客登录名**](https://www.nowcoder.com/practice/7cbf5e3082954c21a80fc750ce97350f)

```sql
select
    cust_id,
    cust_name,
    upper(concat(substring(cust_name,1,2),substring(cust_city,1,3)))  as user_login
from
    Customers
```

### No.82

[**SQL82** **返回 2020 年 1 月的所有订单的订单号和订单日期**](https://www.nowcoder.com/practice/c7734db33854477aa94ae238a3390435)

```sql
select
    order_num,
    order_date
from
    Orders
where
    month (order_date) = 1
    and year (order_date) = 2020
order by
    order_date
```

### No.83

[**SQL83** **确定已售出产品的总数**](https://www.nowcoder.com/practice/a271dc25594a4db28f5b957aad07f9ee)

```sql
select
    sum(quantity) as items_ordered
from
    OrderItems
```

### No.84

[**SQL84** **确定已售出产品项 BR01 的总数**](https://www.nowcoder.com/practice/a225d8a7bc4f496283fe8e21293e841c)

```sql
select
    sum(quantity) as items_ordered
from
    OrderItems
where
    prod_id = "BR01"
group by
    prod_id
```

### No.85

[**SQL85** **确定 Products 表中价格不超过 10 美元的最贵产品的价格**](https://www.nowcoder.com/practice/19d1f06a58b04258aabe5a5a9934e611)

```sql
select distinct
    max(prod_price) as max_price
from
    Products
where
    prod_price <= 10
```

### No.86

[**SQL86** **返回每个订单号各有多少行数**](https://www.nowcoder.com/practice/cf1f8d4a514d455aa0468718fb411f41)

```sql
select
    order_num,
    count(order_num) as order_lines
from
    OrderItems
group by
    order_num
order by
    order_lines ASC
```

### No.87

[**SQL87** **每个供应商成本最低的产品**](https://www.nowcoder.com/practice/f0679d06b50049499691e12a435de8d8)

```sql
select
    vend_id,
    min(prod_price) as cheapest_item
from
    Products
group by
    vend_id
order by
    cheapest_item ASC
```

### No.88

[**SQL88** **返回订单数量总和不小于100的所有订单的订单号**](https://www.nowcoder.com/practice/ff77e82b59544a15987324e19488aafd)

```sql
select
    order_num
from
    OrderItems
group by
    order_num
having
    sum(quantity) >= 100
order by
    order_num ASC
```

### No.89

[**SQL89** **计算总和**](https://www.nowcoder.com/practice/d8a624021183454586da94d280cc8046)

```sql
select
    order_num,
    sum(item_price * quantity) as total_price
from
    OrderItems
group by
    order_num
having
    total_price >= 1000
order by
    order_num ASC
```

### No.90

[**SQL90** **纠错3**](https://www.nowcoder.com/practice/3870c9bca7a4406f899af3e903b8bf51)

```sql
SELECT
    order_num,
    COUNT(*) AS items
FROM
    OrderItems
GROUP BY
    order_num
HAVING
    COUNT(*) >= 3
ORDER BY
    items,
    order_num;
```

### No.91

[**SQL91** **返回购买价格为 10 美元或以上产品的顾客列表**](https://www.nowcoder.com/practice/827eb2a210c64ccdb8ec28fe4c50c246)

```sql
select
    cust_id
from
    Orders
    left join OrderItems on Orders.order_num = OrderItems.order_num
where
    OrderItems.item_price >= 10
// or 
SELECT DISTINCT
    cust_id
FROM
    Orders
WHERE
    order_num IN (
        SELECT
            order_num
        FROM
            OrderItems
        WHERE
            item_price >= 10
    )
```

### No.92

[**SQL92** **确定哪些订单购买了 prod_id 为 BR01 的产品（一）**](https://www.nowcoder.com/practice/b692b0174c0444fa9452aee2d082fbbb)

```sql
select
    cust_id,
    order_date
from
    Orders as o
    left join OrderItems as oi on o.order_num = oi.order_num
where
    prod_id = "BR01"
order by
    order_date
```

### No.93

[**SQL93** **返回购买 prod_id 为 BR01 的产品的所有顾客的电子邮件（一）**](https://www.nowcoder.com/practice/962b16554fbf4b99a87f4d68020c5bfb)

```sql
select
    cust_email
from
    Customers as c
    left join Orders as o on o.cust_id = c.cust_id
    left join OrderItems as oi on o.order_num = oi.order_num
where
    prod_id = "BR01"
order by
    order_date
```

### No.94

[**SQL94** **返回每个顾客不同订单的总金额**](https://www.nowcoder.com/practice/ce313253a81c4947b20e801cd4da7894)

```sql
select
    cust_id,
    sum(item_price * quantity) as total_ordered
from
    OrderItems as oi
    right join Orders as o on o.order_num = oi.order_num
group by
    cust_id
order by
    total_ordered DESC
```

### No.95

[**SQL95** **从 Products 表中检索所有的产品名称以及对应的销售总数**](https://www.nowcoder.com/practice/2b289b78de1546f38fd24e17e56f1bec)

```sql
select
    prod_name,
    sum(quantity) as quant_sold
from
    OrderItems as oi
    right join Products as p on p.prod_id = oi.prod_id
group by
    prod_name
```

### No.96

[**SQL96** **返回顾客名称和相关订单号**](https://www.nowcoder.com/practice/7e7bc361db6a4cb6aa35eefccfe75364)

```sql
select
    cust_name,
    order_num
from
    Customers as c
    inner join Orders as o on c.cust_id = o.cust_id
order by
    cust_name,order_num

select
    cust_name,
    order_num
from
    Customers as c,
    Orders as o
where
    c.cust_id = o.cust_id
order by
    cust_name,order_num

```

### No.97

[**SQL97** **返回顾客名称和相关订单号以及每个订单的总价**](https://www.nowcoder.com/practice/4dda66e385c443d8a11570a70807d250)

```sql
select
    cust_name,
    o.order_num,
    (oi.quantity * oi.item_price) asOrderTotal
from
    Customers as c
    left join Orders as o on c.cust_id = o.cust_id
    left join OrderItems as oi on oi.order_num = o.order_num
order by
    cust_name,
    order_num
```

### No.98

[**SQL98** **确定哪些订单购买了 prod_id 为 BR01 的产品（二）**](https://www.nowcoder.com/practice/999aa31a9a504c60baa088d90d82e64d)

```sql
select
    cust_id,
    order_date
from
    Orders as o
    left join OrderItems as oi on o.order_num = oi.order_num
where
    oi.prod_id = "BR01"
order by
    order_date
```

### No.99

[**SQL99** **返回购买 prod_id 为 BR01 的产品的所有顾客的电子邮件（二）**](https://www.nowcoder.com/practice/c7aa73afc41f4dfc925baebdd175c345)

```sql
select
    cust_email
from
    OrderItems as oi
    inner join Orders as o on oi.order_num = o.order_num
    inner join Customers as c on c.cust_id = o.cust_id
where
    oi.prod_id = "BR01"
```

### No.100

[**SQL100** **确定最佳顾客的另一种方式（二）**](https://www.nowcoder.com/practice/b5766f970ae64ac7944f37f5b47107aa)

```sql
select
    c.cust_name,
    sum(oi.item_price * oi.quantity) as total_price
from
    Customers as c
    inner join Orders as o on c.cust_id = o.cust_id
    inner join OrderItems as oi on oi.order_num = o.order_num
group by
    cust_name
having
    total_price >= 1000
order by
    total_price
```

### No.101

[**SQL101** **检索每个顾客的名称和所有的订单号（一）**](https://www.nowcoder.com/practice/0a876520bd314505b787648e331f5e81)

```sql
select
    cust_name,
    order_num
from
    Customers as c
    inner join Orders as o on c.cust_id = o.cust_id
order by
    cust_name
```

### No.102

[**SQL102** **检索每个顾客的名称和所有的订单号（二）**](https://www.nowcoder.com/practice/4e73c4e770b941c9abc60814601ed498)

```sql
select
    c.cust_name,
    o.order_num
from
    Customers as c
    left join Orders as o on c.cust_id = o.cust_id
order by
    cust_name ASC
```

### No.103

[**SQL103** **返回产品名称和与之相关的订单号**](https://www.nowcoder.com/practice/c369a759436a4e8b80baa9c39e9adf18)

```sql
select
    prod_name,
    order_num
from
    Products as p
    left join OrderItems as oi on p.prod_id = oi.prod_id
order by
    prod_name ASC
```

### No.104

[**SQL104** **返回产品名称和每一项产品的总订单数**](https://www.nowcoder.com/practice/1c64fd9048364a58a8ffa541720359a4)

```sql
select
    p.prod_name,
    count(oi.order_num) as orders
from
    Products as p
    left join OrderItems as oi on p.prod_id = oi.prod_id
group by
    p.prod_name
order by
    p.prod_name ASC
```

### No.105

[**SQL105** **列出供应商及其可供产品的数量**](https://www.nowcoder.com/practice/17f22851cf204019b51a36761a3afc79)

```sql
select
    v.vend_id as vend_id,
    count(p.prod_id) as prod_id
from
    Vendors as v
    left join Products as p on v.vend_id = p.vend_id
group by
    v.vend_id
order by
    v.vend_id ASC
```

### No.106

[**SQL106** **将两个 SELECT 语句结合起来（一）**](https://www.nowcoder.com/practice/a33d5c0ebf434e00b22e2977a5aa3a90)

```sql
select
    prod_id,
    quantity
from
    OrderItems
where
    quantity = 100
union all
select
    prod_id,
    quantity
from
    OrderItems
where
    prod_id like 'BNBG%'
```

### No.107

[**SQL107** **将两个 SELECT 语句结合起来（二）**](https://www.nowcoder.com/practice/ee9ef82f3d6f44b398aedc2fa71db612)

```sql
select
    prod_id,
    quantity
from
    OrderItems
where
    prod_id like 'BNBG%'
    or quantity = 100
order by
    prod_id ASC
```

### No.108

[**SQL108** **组合 Products 表中的产品名称和 Customers 表中的顾客名称**](https://www.nowcoder.com/practice/461077c0ba0f473abecf5ee79c632acd)

```sql
select
    prod_name
from
    Products
union all
select
    cust_name as prod_name
from
    Customers
order by
    prod_name ASC
```

### No.109

[**SQL109** **纠错4**](https://www.nowcoder.com/practice/bde1451b91084c8cab467387a0e0969c)

```sql
SELECT
    cust_name,
    cust_contact,
    cust_email
FROM
    Customers
WHERE
    cust_state = 'MI'
UNION all
SELECT
    cust_name,
    cust_contact,
    cust_email
FROM
    Customers
WHERE
    cust_state = 'IL'
ORDER BY
    cust_name;
```

### No.110

[**SQL110** **插入记录（一）**](https://www.nowcoder.com/practice/5d2a42bfaa134479afb9fffd9eee970c)

```sql
insert into
    exam_record (uid,exam_id,start_time,submit_time,score)
values
    (1001,9001,'2021-9-1 22:11:12','2021-9-1 23:01:12',90),
    (1002, 9002, '2021-09-04 07:01:02', NULL, NULL);
```

### No.111

[**SQL111** **插入记录（二）**](https://www.nowcoder.com/practice/9681abf28745468c8adacb3b029a18ce)

```sql
insert into
    exam_record_before_2021 (uid, exam_id, start_time, submit_time, score)
select
    uid,
    exam_id,
    start_time,
    submit_time,
    score
from
    exam_record
where
    YEAR (submit_time) < '2021'
```

### No.112

[**SQL112** **插入记录（三）**](https://www.nowcoder.com/practice/978bcee6530a430fb0be716423d84082)

```sql
DELETE FROM examination_info
WHERE exam_id=9003;
INSERT INTO examination_info
VALUES(NULL,9003, 'SQL','hard', 90, '2021-01-01 00:00:00')
```

### No.113

[**SQL113** **更新记录（一）**](https://www.nowcoder.com/practice/bfe8ad2bddc540fc911614aa648868b3)

```sql
update
    examination_info
SET
    tag = "Python"
where
    tag = "PYTHON"
```

### No.114

[**SQL114** **更新记录（二）**](https://www.nowcoder.com/practice/0c2e81c6b62e4a0f848fa7693291defc)

```sql
update
    exam_record
set
    submit_time = '2099-01-01 00:00:00',
    score = 0
where
    start_time < '2021-09-01 00:00:00'
    AND score IS NULL;
```

### No.115

[**SQL115** **删除记录（一）**](https://www.nowcoder.com/practice/d331359c5ca04a3b87f06b97da42159c)

```sql
delete from exam_record 
where score < 60 and  timestampdiff(
        MINUTE,
        start_time,
        submit_time
    )<5
```

### No.116

[**SQL116** **删除记录（二）**](https://www.nowcoder.com/practice/964c9f7fffbb4ab18b507cfed4111b4a)

```sql
delete from
    exam_record
where
    submit_time = null
    OR TIMESTAMPDIFF (MINUTE, start_time, submit_time) < 5
ORDER BY
    start_time
LIMIT
    3;
```

### No.117

[**SQL117** **删除记录（三）**](https://www.nowcoder.com/practice/3abefc6fc73e4f219dad0ab66e6b1e3f)

```sql
drop table if EXISTS exam_record;
CREATE TABLE IF NOT EXISTS exam_record (
id int PRIMARY KEY AUTO_INCREMENT COMMENT '自增ID',
uid int NOT NULL COMMENT '用户ID',
exam_id int NOT NULL COMMENT '试卷ID',
start_time datetime NOT NULL COMMENT '开始时间',
submit_time datetime COMMENT '提交时间',
score tinyint COMMENT '得分'
)CHARACTER SET utf8 COLLATE utf8_general_ci;
```

### No.118

[**SQL118** **创建一张新表**](https://www.nowcoder.com/practice/a61ee5519d14444aa99e530309a8e043)

```sql
CREATE TABLE
    IF NOT EXISTS user_info_vip (
        id int PRIMARY KEY AUTO_INCREMENT COMMENT '自增ID',
        uid int UNIQUE NOT NULL COMMENT '用户ID',
        nick_name varchar(64) COMMENT '昵称',
        achievement int DEFAULT 0 COMMENT '成就值',
        `level` int COMMENT '用户等级',
        job varchar(32) COMMENT '职业方向',
        register_time datetime DEFAULT CURRENT_TIMESTAMP COMMENT '注册时间'
    ) CHARACTER
SET
    utf8 COLLATE utf8_general_ci;
```

### No.119

[**SQL119** **修改表**](https://www.nowcoder.com/practice/d08209df6f464cebafda5dfd5de03fce)

```sql
alter table
    user_info add school varchar(15) after level;

alter table
    user_info change job profession varchar(10);

alter table
    user_info modify achievement int (11) default 0;
```

### No.120

[**SQL120** **删除表**](https://www.nowcoder.com/practice/df2f634a53324bbd9369fe6723fedc49)

```sql
drop table
    if EXISTS exam_record_2011;

drop table
    if EXISTS exam_record_2012;

drop table
    if EXISTS exam_record_2013;

drop table
    if EXISTS exam_record_2014;
```

### No.121

[**SQL121** **创建索引**](https://www.nowcoder.com/practice/f2ea9ccf33c740d58576608940981807)

```sql
CREATE INDEX idx_duration ON examination_info (duration);

CREATE UNIQUE INDEX uniq_idx_exam_id ON examination_info (exam_id);

CREATE FULLTEXT INDEX full_idx_tag ON examination_info (tag);
```

### No.122

[**SQL122** **删除索引**](https://www.nowcoder.com/practice/4963f6d63dde48d787aaa2b43460fb4b)

```sql
alter table
    examination_info
drop
    index uniq_idx_exam_id;

alter table
    examination_info
drop
    index full_idx_tag;
    
DROP
    INDEX uniq_idx_exam_id ON examination_info;

DROP
    INDEX full_idx_tag ON examination_info;
```

### No.123

[**SQL123** **SQL类别高难度试卷得分的截断平均值**](https://www.nowcoder.com/practice/a690f76a718242fd80757115d305be45)

```sql
select
    ei.tag,
    ei.difficulty,
    round(
        (sum(er.score) - max(er.score) - min(er.score)) / (count(score) - 2),
        1
    ) as clip_avg_score
from
    exam_record as er
    inner join examination_info as ei on er.exam_id = ei.exam_id
    and ei.tag = "SQL"
    and ei.difficulty = "hard"
group by
    er.exam_id
```

### No.124

[**SQL124** **统计作答次数**](https://www.nowcoder.com/practice/45a87639110841b6950ef6a12d20175f)

```sql
select
    count(distinct id) as total_pv,
    count(submit_time) as complete_pv,
    count(
        distinct exam_id
        and score is not null
    ) as complete_exam_cnt
from
    exam_record
```

### No.125

[**SQL125** **得分不小于平均分的最低分**](https://www.nowcoder.com/practice/3de23f1204694e74b7deef08922805b2)

```sql
select
    e1.score min_score_over_avg
from
    exam_record e1
    left join examination_info e2 on e1.exam_id = e2.exam_id
where
    e2.tag = 'SQL'
    and e1.score >= (
        select
            avg(score)
        from
            exam_record
        where
            exam_id in (
                select
                    exam_id
                from
                    examination_info
                where
                    tag = 'SQL'
            )
    )
order by
    min_score_over_avg
limit
    1
```

### No.126

[**SQL126** **平均活跃天数和月活人数**](https://www.nowcoder.com/practice/9e2fb674b58b4f60ac765b7a37dde1b9)

```sql
select
    date_format (submit_time, '%Y%m') as month,
    round(
        (
            count(distinct uid, date_format (submit_time, '%y%m%d'))
        ) / count(distinct uid),
        2
    ) as avg_active_days,
    count(distinct uid) mau
from
    exam_record
where
    year (submit_time) = 2021
group by
    month
```

### No.127

[**SQL127** **月总刷题数和日均刷题数**](https://www.nowcoder.com/practice/f6b4770f453d4163acc419e3d19e6746)

```sql
select
    date_format (submit_time, '%Y%m') submit_month,
    any_value (count(question_id)) month_q_cnt,
    any_value (
        round(
            count(question_id) / day (LAST_DAY (submit_time)),
            3
        )
    ) avg_day_q_cnt
from
    practice_record
where
    date_format (submit_time, '%Y') = '2021'
group by
    submit_month
union all
select
    '2021汇总' as submit_month,
    count(question_id) month_q_cnt,
    round(count(id) / 31, 3) avg_day_q_cnt
from
    practice_record
where
    date_format (submit_time, '%Y') = '2021'
order by
    submit_month;

```

### No.128

[**SQL128** **未完成试卷数大于1的有效用户**](https://www.nowcoder.com/practice/46cb7a33f7204f3ba7f6536d2fc04286)

```sql
select
    er.uid,
    sum(if (submit_time is null, 1, 0)) as incomplete_cnt,
    sum(if (submit_time is not null, 1, 0)) as complete_cnt,
    group_concat (
        distinct concat_ws (':', date (start_time), tag) separator ';'
    ) as detail
from
    exam_record er
    left join examination_info ei on er.exam_id = ei.exam_id
where
    year (start_time) = 2021
group by
    er.uid
having
    complete_cnt >= 1
    and incomplete_cnt < 5
    and incomplete_cnt > 1
order by
    incomplete_cnt desc;
```

### No.129

[**SQL129** **月均完成试卷数不小于3的用户爱作答的类别**](https://www.nowcoder.com/practice/b1d13efcfa0c4ecea517afbdb9090845)

```sql
SELECT
    b.tag,
    count(*) tag_cnt
FROM
    exam_record a
    LEFT JOIN examination_info b ON a.exam_id = b.exam_id
WHERE
    a.uid IN (
        SELECT
            uid
        FROM
            exam_record
        WHERE
            submit_time IS NOT NULL
        GROUP BY
            uid,
            DATE_FORMAT (submit_time, '%Y%m')
        HAVING
            COUNT(submit_time) > 2
    )
GROUP BY
    b.tag
ORDER BY
    tag_cnt DESC
```

### No.130

[**SQL130** **试卷发布当天作答人数和平均分**](https://www.nowcoder.com/practice/5b58e89556dc4153a79d8cf8c08ba499)

```sql
select
    er.exam_id,
    count(distinct er.uid) as uv,
    round(avg(score), 1) as avg_score
from
    exam_record as er
    left join examination_info as ei on er.exam_id = ei.exam_id
    left join user_info as ui on ui.uid = er.uid
where
    tag = 'SQL'
    and level > 5
    and date_format (submit_time, '%Y%m%d') = date_format (release_time, '%Y%m%d')
group by
    er.exam_id
order by
    uv DESC,
    avg_score ASC
```

### No.131

[**SQL131** **作答试卷得分大于过80的人的用户等级分布**](https://www.nowcoder.com/practice/5bc77e3a3c374ad6a92798f0ead4c744)

```sql
select
    level,
    count(distinct u_i.uid) as level_cnt
from
    exam_record e_r
    join examination_info e_i on e_r.exam_id = e_i.exam_id
    join user_info u_i on e_r.uid = u_i.uid
where
    tag = 'SQL'
    and score > 80
group by
    level
order by
    level_cnt desc,
    level desc
```

### 132

[**SQL132** **每个题目和每份试卷被作答的人数和次数**](https://www.nowcoder.com/practice/203d0aed8928429a8978185d9a03babc)

```sql
select
    exam_id as tid,
    count(distinct uid) as uv,
    count(exam_id) as pv
from
    exam_record
group by
    tid
union all
select
    question_id as tid,
    count(distinct uid) as uv,
    count(question_id) as pv
from
    practice_record
group by
    tid
ORDER BY
    LEFT (tid, 1) DESC,
    uv DESC,
    pv DESC
```

### No.133

[**SQL133** **分别满足两个活动的人**](https://www.nowcoder.com/practice/a126cea91d7045e399b8ecdcadfb326f)

```sql
select
    uid,
    'activity1' as activity
from
    exam_record
where
    year (submit_time) = 2021
group by
    uid
having
    min(score) >= 85
union all
select distinct
    uid,
    'activity2' as activity
from
    exam_record e_r
    join examination_info e_i on e_r.exam_id = e_i.exam_id
where
    year (e_r.submit_time) = 2021
    and e_i.difficulty = 'hard'
    and e_r.score > 80
    and timestampdiff (minute, e_r.start_time, e_r.submit_time) * 2 < e_i.duration
order by
    uid

```

