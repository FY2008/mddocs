# Django 简介

**Django** 使用 **Python** 开发的 **web** 框架，也是 **Python** 中最火的 **Web** 框架。



## Django 环境安装

要使用 **Django** 进行开发，首先我们的电脑上要有 **Python**，其次是安装 **Django** 框架：

`pip install django`

## 创建一个项目

`django-admin startproject project-name`

## 创建一个应用

`python manage.py startapp app-name`

## 项目的一些设定

### 语言

`LANGUAGE_CODE = 'zh-hans'` 把语言改为中文。

### 时区

`TIME_ZONE = 'Asia/Shanghai'` 把时区改为**上海**

### templates 模板

```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR, 'templates')], // 在Django 项目更目录下查找模板
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

### 静态文件设定

```python
STATIC_ROOT = os.path.join(BASE_DIR, 'static')
STATICFILES_DIRS = (
    os.path.join(BASE_DIR, 'static_1'),
    # 其他路径...
)
```

收集静态文件命令：`python manage.py collectstatic`



## 用户上传路径 Media

```python
# Media 配置
# settings.py
MEDIA_URL = '/media/'
MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
```

```python
# urls.py
from django.contrib import admin
from django.urls import path
from django.conf import settings
from django.conf.urls.static import static

urlpatterns = [
    path('admin/', admin.site.urls),
]

if settings.DEBUG:
    urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```

