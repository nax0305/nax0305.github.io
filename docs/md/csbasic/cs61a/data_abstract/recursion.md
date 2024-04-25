# 递归

***递归打印***

```python
def print_all(x):
    print(x)
    return print_all

```

***递归打印参数求和***
```python
def print_sums(n):
    print(n)
    def next_sum(k):
        return print_sums(n+k)
    return next_sum
```

***递归求解数字每位的和***

```python
def split(n):
    return n // 10, n % 10

def sum_digits(n):
    if n < 10:
        return n
    else:
        all_but_last, last = split(n)
        return sum_digits(all_but_last) + last
```

***对递归的分析***
- def statement header
- 条件语句，检查是否base case
- base case， 没有递归部分
- recursive case， 带有递归的部分