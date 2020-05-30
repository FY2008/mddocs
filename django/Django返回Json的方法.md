# Django 返回 Json 数据

## 方法一

```python
from django.shortcuts import render
from django.http import JsonResponse

def test(request):
    data = {
        'msg': 'ok',
    }
    return JsonResponse(data)
```

