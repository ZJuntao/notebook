# 遇到的函数
## find函数
**描述**
find() 方法检测字符串中是否包含子字符串 str ，如果指定 beg（开始） 和 end（结束） 范围，则检查是否包含在指定范围内，如果指定范围内如果包含指定索引值，返回的是索引值在字符串中的起始位置。如果不包含索引值，返回-1。

**语法**
> `str.find(str, beg=0, end=len(string))`

**参数**
* str--指定检索的字符串
* beg --开始索引，默认为0
* end --结束索引，默认为字符串长度

**返回值**
如果包含子字符串返回该字符串起始位置的索引值，否则返回-1。

## str.format()

## os.path.join()
* 一般用来路径拼接
```python3
a = '/home/user'
p = os.path.join(a, 'client')    # p:/home/user/client
```