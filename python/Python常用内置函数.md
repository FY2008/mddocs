## enumerate()

```python
names = ['a', 'b', 'c']
for i, name in enumerate(names):
print(f'{i}->{name}')
```

`enumerate()` 是 `Python` 的一个内置函数，它接收一个“可迭代”对象作为参数，然后返回一个不断生成 `(当前下标, 当前元素)` 的新可迭代对象。这个场景使用它最适合不过。