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



