* `.py` Python 源文件
* `.py3` Python3 脚本（Python3 脚本通常以 .py 而不是 .py3 结尾，很少使用）`.pyc` 这是编译好的字节码。如果您导入一个模块，python 将生成一个 *.pyc 包含字节码的文件，以便以后再次导入它更容易(也更快)。.pyc 二进制文件可以反编译成 .py 文件，反编译软件叫 Easy Python Decompiler。*
* `.pyo`：这是在优化 (-O) 时创建的 *.pyc 文件,从 Python3.5 开始，Python 将只使用 pyc 而不是 pyo 和 pyc
* `.pyd`：这基本上是一个 Windows DLL 文件。
* `.pyi` : MyPy 存根,存根文件（PEP 484）.
* `.pyw` : 用 pythonw.exe 执行的 Windows 的 Python 脚本
* `.pyx` : 将 Cython src 转换为 C/C++
* `.pyz` : Python 脚本归档（PEP 441）（这是一个包含标准 Python 脚本头之后的二进制形式的压缩 Python 脚本（ZIP）的脚本）
* `.pywz` : 用于 MS-Windows 的 Python 脚本归档（PEP 441）（这是一个包含标准 Python 脚本头之后的二进制形式的压缩 Python 脚本（ZIP）的脚本）
* `.py [cod]` : .gitignore 中的通配符表示该文件可能是 .pyc，.pyo 或 .pyd
* `.rpy` : 包含应用程序或框架特定功能的 RPython 脚本或 Python 脚本
* `.pyde` : 处理使用的 Python 脚本
* `.pyp` : Py4D Python 插件
* `.pyt` : Python 声明文件

