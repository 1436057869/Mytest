# Git 初次运行前的配置并通过SSH连接GitHub

每台计算机上只需配置一次，可在任何时候通过运行命令修改。

在 Windows 系统中，Git 会查找 $HOME 目录下（一般情况下是 C:\Users\$USER）的 .gitconfig 文件。
Git 同样也会寻找 /etc/gitconfig 文件，但只限于 MSys 的根目录下，即安装 Git 时所选的目标位置。



## 配置信息

`git config --list`

列出所有 Git 当时能找到的配置。



### 用户信息

`git config --global user.name "Tom"`

`git config --global user.name "tom@example.com"`

注：如果使用了 `--global` 选项，以后 Git 在该系统上都会使用这些信息。当你想针对特定项目使用不同的用户名称和邮件地址时，可在那个项目的目录运行没有 `--global` 的命令。



## 通过 SSH 连接 GitHub

### 生成SSH公钥

完成上述用户信息配置后，使用下面命令生成SSH公钥 (你的个人邮箱)

`ssh-keygen -t rsa -C tom@example.com`

`ssh-keygen` 会确认密钥的存储位置，默认 .ssh/id-rsa，要求你输入两次密钥口令。

如果你不想在使用密钥时输入口令，留空敲击回车即可。

切换到公钥生成的默认目录

`cd ~/.ssh`

目录下存在一对以 id_dsa 或 id_rsa 命名的文件，其中一个带有 .pub 扩展名。 .pub 文件是你的公钥，另一个则是私钥。

`cat ~/.ssh/id-rsa.pub`

复制公钥的==**全部**==内容。（包括开头的 ssh-rsa）= =!

看起来是这样的一串

```
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAklOUpkDHrfHY17SbrmTIpNLTGK9Tjom/BWDSUGPl+nafzlHDTYW7hdI4yZ5ew18JH4JW9jbhUFrviQzM7xlELEVf4h9lFX5QVkbPppSwg0cda3Pbv7kOdJ/MTyBlWXFCR+HAo3FXRitBqxiX1nKhXpHAZsMciLq8V6RjsNAQwdsdMFvSlVK/7XAt3FaoJoAsncM1Q9x5+3V0Ww68/eIFmb1zuUFljQJKprrX88XypNDvjYNby6vw/Pb0rwert/EnmZ+AW4OZPnTPI89ZPmVMLuayrD2cE86Z/il8b+gw3r3+1nKatmIkjn2so1d01QraTlMqVSsbxNrRFi9wrf+M7Q== schacon@mylaptop.local
```



登录到您的 GitHub 上，点击你右上角的头像，**Settings** 选项。

![](images\configuration\1.jpg)

左栏 **SSH and GPG keys**  , **New SSH key**

![](images\configuration\2.jpg)

**Title** 标题，能够区分你的设备

**Key** 将复制的公钥粘贴 

**Add SSH key**



成功后在 Git Bash 执行连接测试

`ssh -T git@github.com`

出现 **Hi somebody ! You've successfully authenticated...** 字样表示连接成功



### 失败了 ?

`cd ~`

删除 .ssh 文件夹

`rm -rf .ssh`

重复生成公钥的环节，继续来一次吧，成功为止

