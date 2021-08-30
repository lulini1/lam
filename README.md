# lam
使用linux及其发行版的经验
排列并配置软件源，建议选择中科大源

`sudo pacman-mirrors -i -c China -m rank`

更新软件包

`sudo pacman -Syu`

安装开源字体

`sudo pacman -S wqy-microhel`

增加国内Arch源

`sudo vim /etc/pacman.conf`

```
[archlinuxcn]
SigLevel = Optional TrustedOnly
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
```

vim打开不能输入按i进入编辑模式,按esc,输入:wq退出

再次更新软件源

`sudo pacman -Syy`

安装签名

`sudo pacman -S archlinuxcn-kerying`



常用软件安装

安装yay

首先安装基础包

`sudo packman -S git base-devel`

`sudo pacman -S yay`

更换yay软件源为清华源

`yay --aururl "https://aur.tuna.tsinghua.edu.cn" --save`

`yay -P -g`查看是否更换成功

安装vscode



安装chrome
`sudo pacman -S google-chrome`







安装git
`yay -S git`
由于在我笔记本上使用vmware造成主机无法使用wifi,找不到解决方法,重装才行,因此不提供安装虚拟机的办法
设置个人git信息
`git config --global user.name “github昵称”`
`git config --global user.email “注册邮箱”`
终端配置zsh
`sudo pacman -S zsh`
切换默认shell为zsh
`sudo chsh -s /bin/zsh KaTeX parse error: Expected 'EOF', got '#' at position 6: USER`

安装oh-my-zsh：

`zsh…(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)`

替换zsh配置文件为oh-my-zsh
`cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc`

安装插件

zsh-autosuggestions
`git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/plugins/zsh-autosuggestions`

zsh-syntax-highlighting
`git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.oh-my-zsh/plugins/zsh-syntax-highlighting`

zsh-nvm
`git clone https://github.com/lukechilds/zsh-nvm ~/.oh-my-zsh/custom/plugins/zsh-nvm`

autojump
`sudo pacman -S autojump`

修改配置文件
`sudo vim ~/.zshrc` 在plugins后面添加刚才下载的插件

如果提示raw.githubusercontent.com拒绝连接

`sudo vim /etc/hosts`添加如下内容

`151.101.108.133 raw.githubusercontent.com`

刷新hosts缓存

`sudo source ~/etc/hosts`

然后重新执行下载命令,完成之后执行,然后重启终端

`sudo source ~/.zshrc`

安装谷歌连接互联网工具,chrome如无法访问在chrome找到代理选择qv2ray自动配置的代理

`yay -S qv2ray` (软件使用请自行百度)

安装proxychains让终端可以走代理!!!强烈推荐

`yay -S proxychains`

配置proxychains

`sudo vim /etc/proxychains.conf`

移动到最下面把socks4代理删除,改为你的谷歌连接网络工具的地址和端口

查看端口号

`yay -S net-tools`在这里插入图片描述

然后在执行这个

`netstat -tunlp`

proxychains使用

例如:proxychains wget xxx

验证是否配置成功

`proxychains wget www.google.com`如下载成功说明配置成功,不成功请检查配置文件
