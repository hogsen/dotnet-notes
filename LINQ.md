# LINQ 查询结果的类型

IEnumerable<out T>,泛型使用了 out
说明它允许参数协变，也就是说它可以接收它所有的派生类型

# orderby 排序

orderby<排序字段> ascending 升序
orderby<排序字段> desending 降序

# group by 分组

元素类型
IGrouping<TKey,TElement>
Tkey 表示分组依据
TElement 表示分组的元素

group<要分组的元素> by <分组依据>
根据部门对员工进行分组,并使用 into 将分组的数据存进 eg
group emp by emp.Department into eg

# 联合查询

两张表 on 后面是联合条件
from 元素 1 in 列表 A
join 元素 2 in 列表 B
on 字段 equals 字段

# 嵌套查询

# 补充

LINQ 查询语句必须以 select 或 group 子句结尾
