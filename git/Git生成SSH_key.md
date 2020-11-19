# Windows

  1.创建SSH Key。在windows下查看[c盘->用户->用户名->.ssh]下是否有id_rsa、id_rsa.pub文件，如果没有需要手动生成。

打开git bash，在控制台中输入以下命令： $ ssh-keygen -t rsa -C "victordu6694@gmail.com"。

  密钥类型可以用 -t 选项指定。如果没有指定则默认生成用于SSH-2的RSA密钥。这里使用的是rsa。

  同时在密钥中有一个注释字段，用-C来指定所指定的注释，可以方便用户标识这个密钥，指出密钥的用途或其他有用的信息。所以在这里输入自己的邮箱或者其他都行。

  输入完毕后程序同时要求输入一个密语字符串(passphrase)，空表示没有密语。接着会让输入2次口令(password)，空表示没有口令。3次回车即可完成当前步骤，此时[c盘>用户>自己的用户名>.ssh]目录下已经生成好了。

    2.登录github。打开setting->SSH keys，点击右上角 New SSH key，把生成好的公钥id_rsa.pub放进 key输入框中，再为当前的key起一个title来区分每个key。

# Mac

1.终端输入：cd ~/ .ssh

    2.终端输入：sudo ssh-keygen -t rsa -C "victordu6694@gmail.com"
    
    3.回车后提示输入密码, 此处密码可以不填, 直接回车，提示再次输入密码, 直接回车,生成成功
    
    4.前往 /Users/victor/.ssh/id_rsa.pub 找到SSH key

