## 配置基础

`config` 实际上继承于字典，并且可以像修改字典一样修改它:

```python
app = Flask(__name__)
app.config['DEBUG'] = True
```

给定的配置值会被推送到 Flask 对象中，所以你可以在那里读写它们:

```python
app.debug = True
```

你可以使用 dict.update() 方法来一次性更新多个键:

```python
app.config.update(
    DEBUG=True,
    SECRET_KEY='...'
)
```

## 从文件配置

如果你能在独立的文件里存储配置，理想情况是存储在当前应用包之外，它将变得更有用。这使得通过各式包处理工具（ 部署和分发 ）打包和分发你的应用成为可能，并在之后才修改配置文件。

则一个常见模式为如下:

```python
app = Flask(__name__)
app.config.from_object('yourapplication.default_settings')
app.config.from_envvar('YOURAPPLICATION_SETTINGS')
```



## Flask 配置选项

### ENV

---

应用运行于什么环境。 `Flask` 和 扩展可以根据环境不同而行为不同，如打开或 关闭调试模式。 `env` 属性映射了这个配置键。本变量由 `FLASK_ENV` 环境变量设置。如果本变量是在代码中设置的话，可能出 现意外。

在生产环境中不要使用 `development` 。

缺省值： =='production'==



### DEBUG

---

是否开启调试模式。使用 `flask run` 启动开发服务器时，遇到未能处理的 异常时会显示一个交互调试器，并且当代码变动后服务器会重启。 `debug` 属性映射了这个配置键。当 `ENV` 是 `'development'` 时，本变量会启用，并且会被 `FLASK_DEBUG` 环境变量 重载。如果本变量是在代码中设置的话，可能会出现意外。

在生产环境中不要开启调试模式。

缺省值：当 `ENV` 是` 'development' `时，为 `True` ；否则为 `False` 。



### TESTING

---

开启测试模式。异常会被广播而不是被应用的错误处理器处理。扩展可能也会为 了测试方便而改变它们的行为。你应当在自己的调试中开启本变量。

缺省值： ==False==



### PROPAGATE_EXCEPTIONS

---

异常会重新引发而不是被应用的错误处理器处理。在没有设置本变量的情况下， 当 `TESTING` 或 `DEBUG` 开启时，本变量隐式地为真。

缺省值： ==None==



### PRESERVE_CONTEXT_ON_EXCEPTION

---

异常会重新引发而不是被应用的错误处理器处理。在没有设置本变量的情况下， 当 `TESTING` 或 `DEBUG` 开启时，本变量隐式地为真。

缺省值： ==None==



### TRAP_HTTP_EXCEPTIONS

---

如果没有处理 `HTTPException` 类型异常的处理器，重新引发该异常用于被 交互调试器处理，而不是作为一个简单的错误响应来返回。

缺省值： ==False==



### TRAP_BAD_REQUEST_ERRORS

---

尝试操作一个请求字典中不存在的键，如 `args` 和 `form` ，会返回一个 `400 Bad Request error` 页面。开启本变量，可以把这种错误作为一个未处理的 异常处理，这样就可以使用交互调试器了。本变量是一个特殊版本的 `TRAP_HTTP_EXCEPTIONS` 。如果没有设置，本变量会在调试模式下开启。

缺省值： ==None==



### SECRET_KEY

---

密钥用于会话 `cookie` 的安全签名，并可用于应用或者扩展的其他安全需求。本 变量应当是一个字节型长随机字符串，虽然 `unicode` 也是可以接受的。例如， 复制如下输出到你的配置中:

```shell $ python -c 'import os; print(os.urandom(16))'
b'_5#y2L"F4Q8z\n\xec]/'
```

当发贴提问或者提交代码时，不要泄露密钥。

缺省值： ==None==



### SESSION_COOKIE_NAME

---

会话 `cookie` 的名称。假如已存在同名 `cookie` ，本变量可改变。

缺省值：=='session'==



### SESSION_COOKIE_DOMAIN

---

认可会话 `cookie` 的域的匹配规则。如果本变量没有设置，那么 `cookie` 会被 `SERVER_NAME` 的所有子域认可。如果本变量设置为 `False` ，那么 `cookie` 域不会被设置。

缺省值： ==None==



### SESSION_COOKIE_PATH

---

认可会话 `cookie` 的路径。如果没有设置本变量，那么路径为 `APPLICATION_ROOT` ，如果 `APPLICATION_ROOT` 也没有设置，那么会是 `/` 。

缺省值： ==None==



### SESSION_COOKIE_HTTPONLY

---

为了安全，浏览器不会允许 `JavaScript` 操作标记为“ `HTTP only` ”的 `cookie` 。

缺省值： ==True==



### SESSION_COOKIE_SECURE

---

如果 `cookie` 标记为“ `secure` ”，那么浏览器只会使用基于 `HTTPS` 的请求发 送 `cookie `。应用必须使用 `HTTPS` 服务来启用本变量。

缺省值： ==False==



### SESSION_COOKIE_SAMESITE

---

限制来自外部站点的请求如何发送 `cookie` 。可以被设置为 `'Lax'` （推荐） 或者 `'Strict'` 。参见 `Set-Cookie` 选项.

缺省值： ==None==



### PERMANENT_SESSION_LIFETIME

---

如果 `session.permanent` 为真， `cookie` 的有效期为本变量设置的数字， 单位为秒。本变量可能是一个 `datetime.timedelta` 或者一个 `int` 。

`Flask` 的缺省 `cookie` 机制会验证电子签章不老于这个变量的值。

缺省值： ==timedelta(days=31) （ 2678400 秒）==



### SESSION_REFRESH_EACH_REQUEST

---

当 `session.permanent` 为真时，控制是否每个响应都发送 `cookie` 。每次 都发送 `cookie` （缺省情况）可以有效地防止会话过期，但是会使用更多的带宽。 会持续会话不受影响。

缺省值： ==True==



### USE_X_SENDFILE

---

当使用 `Flask` 提供文件服务时，设置 `X-Sendfile` 头部。有些网络服务器， 如 `Apache` ，识别这种头部，以利于更有效地提供数据服务。本变量只有使用这 种服务器时才有效。

缺省值： ==False==



### SEND_FILE_MAX_AGE_DEFAULT

---

当提供文件服务时，设置缓存，控制最长存活期，以秒为单位。可以是一个 `datetime.timedelta` 或者一个 `int` 。在一个应用或者蓝图上使 用 `get_send_file_max_age()` 可以基于单个文件重载本变 量。

缺省值： ==timedelta(hours=12) （ 43200 秒）==



### SERVER_NAME

---

通知应用其所绑定的主机和端口。子域路由匹配需要本变量。

如果配置了本变量， `SESSION_COOKIE_DOMAIN` 没有配置，那么本变量 会被用于会话 `cookie` 的域。现代网络浏览器不会允许为没有点的域设置 `cookie` 。为了使用一个本地域，可以在你的 `host `文件中为应用路由添加 任意名称。:

`127.0.0.1 localhost.dev`
如果这样配置了， `url_for` 可以为应用生成一个单独的外部 `URL` ，而不是 一个请求情境。

缺省值：==None==



### APPLICATION_ROOT

---

通知应用应用的根路径是什么。这个变量用于生成请求环境之外的 `URL` （请求 内的会根据 `SCRIPT_NAME` 生成；参见 应用调度 ）。

如果 `SESSION_COOKIE_PATH` 没有配置，那么本变量会用于会话 `cookie` 路 径。

缺省值： =='/'==



### PREFERRED_URL_SCHEME

----

当不在请求情境内时使用些预案生成外部 `URL` 。

缺省值： =='http'==



### MAX_CONTENT_LENGTH

---

在进来的请求数据中读取的最大字节数。如果本变量没有配置，并且请求没有指 定 `CONTENT_LENGTH` ，那么为了安全原因，不会读任何数据。

缺省值： ==None==



### JSON_AS_ASCII

---

把对象序列化为 `ASCII-encoded JSON` 。如果禁用，那么 `JSON` 会被返回为一个 `Unicode` 字符串或者被 `jsonify` 编码为 `UTF-8` 格式。本变量应当保持 启用，因为在模块内把 `JSON` 渲染到 `JavaScript` 时会安全一点。

缺省值： ==True==



### JSON_SORT_KEYS

---

按字母排序 `JSON` 对象的键。这对于缓存是有用的，因为不管 `Python` 的哈希种 子是什么都能够保证数据以相同的方式序列化。为了以缓存为代价的性能提高可 以禁用它，虽然不推荐这样做。

缺省值： ==True==



### JSONIFY_PRETTYPRINT_REGULAR

---

`jsonify` 响应会输出新行、空格和缩进以便于阅读。在调试模式下总是启用 的。

缺省值： ==False==



### JSONIFY_MIMETYPE

---

`jsonify` 响应的媒体类型。

缺省值： =='application/json'==



### TEMPLATES_AUTO_RELOAD

---

当模板改变时重载它们。如果没有配置，在调试模式下会启用。

缺省值： ==None==



### EXPLAIN_TEMPLATE_LOADING

---

记录模板文件如何载入的调试信息。使用本变量有助于查找为什么模板没有载入 或者载入了错误的模板的原因。

缺省值： ==False==



### MAX_COOKIE_SIZE

---

当 cookie 头部大于本变量配置的字节数时发出警告。缺省值为 `4093` 。 更大的 cookie 会被浏览器悄悄地忽略。本变量设置为 `0` 时关闭警告。

## Flask_SQLALChemy 配置选项

| 名字                      | 备注                                                         |
| ------------------------- | ------------------------------------------------------------ |
| SQLALCHEMY_DATABASE_URI   | 用于连接的数据库 URI 。例如:sqlite:tmp/test.dbmysql://username:password@server/db |
| SQLALCHEMY_BINDS          | 一个映射 binds 到连接 URI 的字典。更多 binds 的信息见用 Binds 操作多个数据库。 |
| SQLALCHEMY_ECHO           | 如果设置为Ture， SQLAlchemy 会记录所有 发给 stderr 的语句，这对调试有用。(打印sql语句) |
| SQLALCHEMY_RECORD_QUERIES | 可以用于显式地禁用或启用查询记录。查询记录 在调试或测试模式自动启用。更多信息见get_debug_queries()。 |
| SQLALCHEMY_NATIVE_UNICODE | 可以用于显式禁用原生 unicode 支持。当使用 不合适的指定无编码的数据库默认值时，这对于 一些数据库适配器是必须的（比如 Ubuntu 上 某些版本的 PostgreSQL ）。 |
| SQLALCHEMY_POOL_SIZE      | 数据库连接池的大小。默认是引擎默认值（通常 是 5 ）           |
| SQLALCHEMY_POOL_TIMEOUT   | 设定连接池的连接超时时间。默认是 10 。                       |
| SQLALCHEMY_POOL_RECYCLE   | 多少秒后自动回收连接。这对 MySQL 是必要的， 它默认移除闲置多于 8 小时的连接。注意如果 使用了 MySQL ， Flask-SQLALchemy 自动设定 这个值为 2 小时。 |

## 数据库连接

```python
app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://postgres:sandz123456@127.0.0.1/flask_db'
app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql://scott:tiger@localhost/mydatabase'
app.config['SQLALCHEMY_DATABASE_URI'] = 'oracle://scott:tiger@127.0.0.1:1521/sidname'
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:////absolute/path/to/foo.db'
```

