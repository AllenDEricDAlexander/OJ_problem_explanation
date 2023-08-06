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

