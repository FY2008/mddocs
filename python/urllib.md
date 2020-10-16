# urllib

`urllib`是Python中请求url连接的官方标准库，在Python2中主要为urllib和urllib2，在Python3中整合成了urllib。

而`urllib3`则是增加了连接池等功能，两者互相都有补充的部分。

## urllib 官方文档

[https://docs.python.org/3/library/urllib.html](https://docs.python.org/3/library/urllib.html)

## urllib 模块划分

1. `urllib.request`
2. `urllib.response`
3. `urllib.parse`
4. `urllib.error`

## urllib.request

urllib中，request这个模块主要负责构造和发起网络请求，并在其中加入Headers、Proxy等。

### GET 请求

使用 urlopen() 方法来发起请求：

```python
from urllib import request

url = "https://www.github.com"
html = request.urlopen(url)

print(html.status)
print(html.read().decode('utf-8'))
```

