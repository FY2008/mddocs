# 字段类型

| 类型名       |     Python类型     | 说明                                                |
| ------------ | :----------------: | --------------------------------------------------- |
| Integer      |        int         | 普通整数，通常是32位                                |
| SmallInteger |        int         | 取值范围小的整数，通常是16位                        |
| BigInteger   |    int 或 long     | 不限精度的整数                                      |
| Float        |       float        | 浮点数                                              |
| Numeric      |  decimal.Decimal   | 定点数                                              |
| String       |        str         | 变长字符串                                          |
| Text         |        str         | 变长字符串，对较长或不限长度的字符串做了优化        |
| Unicode      |      unicode       | 变长 Unicode 字符串                                 |
| UnicodeText  |      unicode       | 变长 Unicode 字符串，对较长或不限长的字符串做了优化 |
| Boolean      |        bool        | 布尔值                                              |
| Date         |   datetime.date    | 日期                                                |
| Time         |   datetime.time    | 时间                                                |
| DataTime     | datetime.datetime  | 日期和时间                                          |
| Interval     | datetime.timedelta | 时间间隔                                            |
| Enum         |        str         | 一组字符串                                          |
| PickleType   |  任何 Python 对象  | 自动使用 Pickle 序列化                              |
| LargeBinary  |        str         | 二进制 blob                                         |

## 列选项

|   选项名    |                             说明                             |
| :---------: | :----------------------------------------------------------: |
| primary_key |                 如果设为 True，列为表的主键                  |
|   uniquey   |             如果设为 True，列不允许出现重复的值              |
|   indexy    |          如果设为 True，为列创建索引，提升查询效率           |
|  nullabley  | 如果设为 True，列允许使用空值；如果设为 False，列不允许使用空值 |
|  defaulty   |                        为列定义默认值                        |

## 关系选项

| 选项名        | 说明                                                         |
| ------------- | ------------------------------------------------------------ |
| backref       | 在关系的另一个模型中添加反向引用                             |
| primaryjoin   | 明确指定两个模型之间使用的连结条件；只在摸棱两可的关系中需要指定 |
| lazy          | 指定如何加载相关记录，可选值有 select （首次访问时按需加载）、immediate（源对象加载后就加载）、joined（加载记录，但使用连结）、subquery（立即加载，但使用子查询）、noload（永不加载）和 Dynamic（不加载记录，但提供加载记录的查询） |
| uselist       | 如果设为 False，不使用列表，而使用标量值                     |
| order_by      | 指定关系中记录的排列方式                                     |
| secondary     | 指定多对多关系中关联表的名称                                 |
| secondaryjoin | SQLALchemy 无法自行决定时，指定多对多关系中的二级连结条件    |

