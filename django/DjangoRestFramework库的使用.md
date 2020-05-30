

## 介绍

Django REST framework（以下简称 DRF）是一个开源的 Django 扩展，提供了便捷的 REST API 开发框架，拥有以下特性：

* 直观的 API web 界面。
* 多种身份认证和权限认证方式的支持。
* 内置了 OAuth1 和 OAuth2 的支持。
* 内置了限流系统。
* 根据 Django ORM 或者其它库自动序列化。
* 丰富的定制层级：函数视图、类视图、视图集合到自动生成 API，满足各种需要。
* 可扩展性，插件丰富。
* 广泛使用，文档丰富。

## REST 和 RESTful

REST 全称 REpresentational State Transfer，即“表现层状态转化”，RESTful 架构即符合 REST 风格的架构。 网上关于 REST 的讨论很多，在一些细节的地方却经常稍有出入，不过大体思想都是充分利用 HTTP/HTTPS 协议的特点，比如 HTTP 方法、header 信息、HATEOAS，直接面向资源进行操作。

阮一峰的两篇介绍：

* http://www.ruanyifeng.com/blog/2011/09/restful.html
* http://www.ruanyifeng.com/blog/2014/05/restful_api.html

## 基础组件／基本概念

### 序列化（Serializer）

[序列化](https://www.django-rest-framework.org/api-guide/serializers/)（Serializer）是 DRF 的核心概念，提供了数据的验证和渲染功能，其工作方式类似越 Django Form，当然也提供了对应 ModelForm 的 ModelSerializer。 和 Django Form 类似，Serializer 也是基于 Field 进行字段验证，Field 类都来自于 `rest_framework.fields`。

```python
class YourSerializer(Serializer):
    field1 = Field()
    def save(self, validated_data):
        # save your data here
        return saved_data
    def update(self, instance, validated_data):
        # update your instance
        return instance
```

Serializer 的主要工作是将 Python 数据结构序列化为其它格式（XML／JSON 等等）。

序列化之后的数据保存在 `serializer.data` 中的，可以使用 `SomeRenderer().render(serializer.data)` 将其序列化为字符串对象作为 Response body 返回。

反序列化

```python
data = SomeParser().parse(incoming_stream)
serializer = YourSerializer(data=data)
if serializer.is_valid():     # 这里会根据 Serialzier 的 Field 和自定义验证工具进行数据校验
    logging.info(serializer. validated_data)
    serializer.update()        # 或者 serializer.create()
```

对于自定义 Serializer，你需要自己实现 create 和 update 方法。

你也可以使用 serializer.save(**data)，save 方法的行为取决于初始化的方式：

```python
# .save() 会创建一个新实例
serializer = CommentSerializer(data=data)

# .save() 会更新 `comment` 实例
serializer = CommentSerializer(comment, data=data)
```

反序列化时应该先运行 serializer.is_valid() 判断数据是否合法，serializer.is_valid(raise_exception=True) 会直接返回 400 信息。

### 字段验证

可以通过 Field 类型定义或者 `.validate_<your_field>` 方法来自行判断。字段名已设置 `required=False` 时，`validate_<your_field>` 将自动跳过空字段。

### 部分更新

部分更新和更新不一样，应当是使用 HTTP 的 PATCH 方法发送请求。

### 嵌套对象

DRF 支持数据嵌套创建和修改，不过这样不利于数据的扁平化管理和测试。

### 序列化关联对象

`PrimaryKeyRelatedField` `HyperlinkedRelatedField` `SlugRelatedField` `HyperlinkedIdentityField` `YourSerializer`

对于可写的 Serializer，`queryset` 是必须值。

### HyperLinkedModelSerializer

HyperLinkedModelSerializer 是一个值得推荐的 Serializer，它能够自动为 HTMLRenderer 提供相关外键资源的超链接，便于 web 调试。

但是它的使用也有一些问题，需要注意一下：

### 搜索

可以在 Serializer 中定义 `search_fields` 来指定可以搜索的字段，DRF 的搜索是基于 `like`，因此并不支持模糊搜索，在数据量较大的情况下还会有性能问题。

### View 和 ViewSet

DRF 通过 View 提供 API 接口，一个 View 可以对应多个 Renderer，针对不同的渲染条件提供不同的输出格式（HTML／XML／JSON）。

ViewSet 则是 View 的一个封装，一个 ViewSet 可以为同一个 URL 根据请求方法提供不同的接口。尤其是 ModelViewSet 会自动根据 Model 的定义生成 REST 接口和 URL，能够快速生成网站的一整套 API。

定义一个 ViewSet 需要为其声明 `queryset` 和 `serializer` 属性：

```python
class UserViewSet(viewsets.ModelViewSet):
    """
    API endpoint that allows users to be viewed or edited.
    """
    queryset = User.objects.all().order_by('-date_joined')
    serializer_class = UserSerializer
```

