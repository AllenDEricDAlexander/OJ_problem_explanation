# 第一题

[595. 大的国家](https://leetcode.cn/problems/big-countries/)

```python
world[(world['area'] >= 3000000) | (world['population'] >= 25000000)][['name','population','area']]

world.query('area>=3000000 or population >=25000000')[['name','population','area']]
```

# 第二题

[1757. 可回收且低脂的产品](https://leetcode.cn/problems/recyclable-and-low-fat-products/)

```python
products.query('low_fats=="Y" and recyclable=="Y"')[['product_id']]
```

# 第三题

[183. 从不订购的客户](https://leetcode.cn/problems/customers-who-never-order/)

```python
data = customers[~customers["id"].isin(orders["customerId"] )][["name"]]
data.columns = ["Customers"]
return data
```

# 第四题

[1148. 文章浏览 I](https://leetcode.cn/problems/article-views-i/)

```python
id_list = views[views.viewer_id==views.author_id]['author_id'].unique()
return pd.DataFrame(id_list, columns=['id']).sort_values('id')
```



