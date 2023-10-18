### 第一题

[1757. 可回收且低脂的产品](https://leetcode.cn/problems/recyclable-and-low-fat-products/)

```sql
select 
	product_id 
from 
	Products 
where p.low_fats = 'Y' and recyclable = 'Y';
```

### 第二题

[584. 寻找用户推荐人](https://leetcode.cn/problems/find-customer-referee/)

```sql
SELECT name FROM customer WHERE  ifnull(referee_id,0) <> 2;

SELECT name FROM customer as c WHERE referee_id <> 2 or referee_id is null;
```

### 第三题

[595. 大的国家](https://leetcode.cn/problems/big-countries/)

```sql
SELECT
  	name,population,area
FROM
  	World
WHERE
  	area >= 3000000 OR population >= 25000000;

# or会导致不走索引，大数据量情况下，用union代替or更高效

select t.name, t.population, t.area from world t
    where t.area >= 3000000
    union
select t.name, t.population, t.area from world t
    where t.population >= 25000000;
```

### 第四题

[1148. 文章浏览 I](https://leetcode.cn/problems/article-views-i/)

```sql
SELECT 
	DISTINCT author_id AS id 
FROM  
	Views 
where 
	author_id = viewer_id 
order by id;
```

### 第五题

[1683. 无效的推文](https://leetcode.cn/problems/invalid-tweets/)

```sql
SELECT 
	tweet_id 
FROM 
	Tweets 
WHERE CHAR_LENGTH(content) > 15;
```

### 第六题

[1378. 使用唯一标识码替换员工ID](https://leetcode.cn/problems/replace-employee-id-with-the-unique-identifier/)

```sql
select eu.unique_id,e.name from Employees e left join  EmployeeUNI eu on e.id = eu.id;
```

### 第七题

[1068. 产品销售分析 I](https://leetcode.cn/problems/product-sales-analysis-i/)

```sql
select p.product_name ,s.year,s.price from Sales s left join Product p on s.product_id = p.product_id
```

### 第八题

[1581. 进店却未进行过交易的顾客](https://leetcode.cn/problems/customer-who-visited-but-did-not-make-any-transactions/)

```sql
select 
  Visits.customer_id,count(customer_id) as count_no_trans 
from 
  Visits left outer join Transactions 
on
  Visits.visit_id=Transactions.visit_id 
where 
  Transactions.visit_id is null 
group by 
  customer_id;
```

### 第八题

[197. 上升的温度](https://leetcode.cn/problems/rising-temperature/)

```sql
select w1.id from Weather w1,Weather w2  where w1.Temperature > w2.Temperature and DATEDIFF(w1.recordDate,w2.recordDate) =1;
```

### 第九题

[1661. 每台机器的进程平均运行时间](https://leetcode.cn/problems/average-time-of-process-per-machine/)

```sql
select a1.machine_id, round(avg(a2.TIMESTAMP - a1.TIMESTAMP ), 3) as processing_time
from activity a1, activity a2
where a1.machine_id = a2.machine_id
and a1.process_id = a2.process_id
and a1.activity_type = 'start'
and a2.activity_type = 'end'
GROUP BY a1.machine_id;
```

### 第十题

[577. 员工奖金](https://leetcode.cn/problems/employee-bonus/)

```sql
select e.name , b.bonus from Employee as e left outer join Bonus as b  on e.empid = b.empid where b.bonus < 1000 or b.bonus is null
```

### 第十一题

[1280. 学生们参加各科测试的次数](https://leetcode.cn/problems/students-and-examinations/)

```sql
select s.student_id,  s.student_name, sub.subject_name, IFNULL(grouped.attended_exams,0) as attended_exams  
from Students as s Cross Join Subjects as sub left join (
    Select 
        student_id, subject_name, COUNT(*) AS attended_exams
    From 
        Examinations
    Group By
        student_id, subject_name
) grouped 
ON s.student_id = grouped.student_id AND sub.subject_name = grouped.subject_name
group by s.student_id, sub.subject_name order by s.student_id; 
```

### 第十二题

[570. 至少有5名直接下属的经理](https://leetcode.cn/problems/managers-with-at-least-5-direct-reports/)

```sql
select e1.name from employee as e1 inner join employee as e2 on e1.id = e2.managerId group by e2.managerId having count(*)>=5 
```

### 第十三题

[1934. 确认率](https://leetcode.cn/problems/confirmation-rate/)

```sql
select signups.user_id,ifnull(confirmation_rate,0) as confirmation_rate 
from signups left join 

(select t1.user_id,round(t2.rage/t1.rage,2) as confirmation_rate  
from (select count(*) as rage ,user_id from Confirmations group by user_id) as t1 
,(select count(*) as rage ,user_id,action from Confirmations group by action,user_id) as t2  
where t1.user_id = t2.user_id and t2.action = 'confirmed') 

as s2 on signups.user_id = s2.user_id 
```

```sql
SELECT
    s.user_id,
    ROUND(IFNULL(AVG(c.action='confirmed'), 0), 2) AS confirmation_rate
FROM
    Signups AS s
LEFT JOIN
    Confirmations AS c
ON
    s.user_id = c.user_id
GROUP BY
    s.user_id
```

### 第十四题

[620. 有趣的电影](https://leetcode.cn/problems/not-boring-movies/)

```sql
select * 
from cinema
where description != 'boring' and id % 2 =1
order by rating DESC
```

### 第十五题

[1251. 平均售价](https://leetcode.cn/problems/average-selling-price/)

```sql
select p.product_id ,round(sum(u.units * p.price)/sum(u.units),2) as average_price 
from Prices  as p left join UnitsSold  as u 
on p.product_id = u.product_id and u.purchase_date >= p.start_date and u.purchase_date <= end_date
group by product_id
```

### 第十六题

[1075. 项目员工 I](https://leetcode.cn/problems/project-employees-i/)

```sql
select project_id  , round(sum(experience_years)/count(*),2) as average_years 
from Project LEFT JOIN Employee on Project.employee_id  = Employee.employee_id
group by project_id  
```

### 第十七题

[1633. 各赛事的用户注册率](https://leetcode.cn/problems/percentage-of-users-attended-a-contest/)

```sql
select contest_id ,round(count(*)/(select count(*) from users) * 100,2) as percentage  
from register left join users on users.user_id = register.user_id
group by contest_id
order by percentage DESC, contest_id
```

### 第十八题

[1211. 查询结果的质量和占比](https://leetcode.cn/problems/queries-quality-and-percentage/)

```sql
select query_name,round(AVG(rating  / position),2) as quality,ROUND(SUM(IF(rating < 3, 1, 0)) * 100 / COUNT(*), 2) as poor_query_percentage
from Queries
group by query_name
```

### 第十九题

[1193. 每月交易 I](https://leetcode.cn/problems/monthly-transactions-i/)

```sql
select 
	DATE_FORMAT(trans_date, '%Y-%m') AS month, 
	country, count(*) as trans_count,
	sum(if(state = 'approved',1,0)) as approved_count,
	sum(amount) trans_total_amount,
	sum(case when state = 'approved' then amount else 0 end) as approved_total_amount 
from Transactions
group by DATE_FORMAT(trans_date, '%Y-%m'),country
```

### 第二十题

[1174. 即时食物配送 II](https://leetcode.cn/problems/immediate-food-delivery-ii/)

```sql
select round (
    sum(order_date = customer_pref_delivery_date) * 100 /
    count(*),
    2
) as immediate_percentage
from Delivery
where (customer_id, order_date) in (
    select customer_id, min(order_date)
    from delivery
    group by customer_id
)
```

### 第二十一题

[550. 游戏玩法分析 IV](https://leetcode.cn/problems/game-play-analysis-iv/)

```sql
select round(avg(a.event_date is not null), 2) fraction
from 
    (select player_id, min(event_date) as login
    from activity
    group by player_id) p 
left join activity a 
on p.player_id=a.player_id and datediff(a.event_date, p.login)=1
```

### 第二十二题

[1174. 即时食物配送 II](https://leetcode.cn/problems/immediate-food-delivery-ii/)

```sql
select round (
    sum(order_date = customer_pref_delivery_date) * 100 /
    count(*),
    2
) as immediate_percentage
from Delivery
where (customer_id, order_date) in (
    select customer_id, min(order_date)
    from delivery
    group by customer_id
)
```

### 第二十三题

[550. 游戏玩法分析 IV](https://leetcode.cn/problems/game-play-analysis-iv/)

```sql
select round(avg(a.event_date is not null), 2) fraction
from 
    (select player_id, min(event_date) as login
    from activity
    group by player_id) p 
left join activity a 
on p.player_id=a.player_id and datediff(a.event_date, p.login)=1
```

### 第二十四题

[2356. 每位教师所教授的科目种类的数量](https://leetcode.cn/problems/number-of-unique-subjects-taught-by-each-teacher/)

```sql
select teacher_id ,count(distinct subject_id ) as cnt from Teacher group by teacher_id;
```

### 第二十五题

[596. 超过5名学生的课](https://leetcode.cn/problems/classes-more-than-5-students/)

```sql
select class from courses group by class having(count(student)) > 4
```

### 第二十六题

[1729. 求关注者的数量](https://leetcode.cn/problems/find-followers-count/)

```sql
select user_id , count(*) as followers_count from followers group by user_id order by user_id
```

### 第二十七题

[1141. 查询近30天活跃用户数](https://leetcode.cn/problems/user-activity-for-the-past-30-days-i/)

```sql
select activity_date  as day , count(distinct user_id) as active_users  from Activity where activity_date  >= DATE_SUB('2019-07-27', INTERVAL 29 DAY) AND activity_date <= '2019-07-27' group by activity_date
```

### 第二十八题

[1084. 销售分析III](https://leetcode.cn/problems/sales-analysis-iii/)

```sql
select p.product_id, product_name
from product p join sales s
on p.product_id = s.product_id
group by product_id
having min(sale_date) >= '2019-01-01' and max(sale_date) <= '2019-03-31';
```

### 第二十九题

[619. 只出现一次的最大数字](https://leetcode.cn/problems/biggest-single-number/)

```sql
select max(num) as num
from MyNumbers
where num not in(select num
from MyNumbers
group by num
having count(num) > 1)
```

### 第三十题

[1045. 买下所有产品的客户](https://leetcode.cn/problems/customers-who-bought-all-products/)

```sql
select customer_id  from Customer group by customer_id  having(count(distinct product_key) = (select count(distinct product_key) from Product))
```

### 第三十一题

[1731. 每位经理的下属员工数量](https://leetcode.cn/problems/the-number-of-employees-which-report-to-each-employee/)

```sql
SELECT
a.employee_id, a.name, COUNT(*) AS reports_count, ROUND(AVG(b.age)) AS average_age
FROM Employees AS a
    LEFT OUTER JOIN Employees AS b
ON a.employee_id = b.reports_to
WHERE b.employee_id IS NOT NULL
GROUP BY a.employee_id
ORDER BY a.employee_id;
```

