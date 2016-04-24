# vimconfig

## 项目介绍

*vimconfig* 是给我个人设计的，用于管理vim配置，插件，并于各工作平台之间同步。

该项目本体为 Vim 的主配置文件夹及主配置文件，
用来放置插件和相关的帮助文档。
为了方便插件的安装，配置，升级和删除，
使用 [pathogen](https://github.com/tpope/vim-pathogen) 管理插件。

## 使用说明

### 获取代码

* git项目主页：

git clone 项目至 Vim 主配置文件夹，
根据个体差异，
该文件夹位置可能有所不同，
一般来说位于 $HOME/.vim下。
具体位置请使用 vim --version，
或于 vim 环境下执行 :version 查看。

随后，于家目录下建立链接文件指向项目内 .vimrc 配置文件：
    ln $本项目目录/.vimrc ~/vimrc

### 包含插件

#### 中文帮助
Vim 中文帮助下载自 https://sourceforge.net/projects/vimcdoc/files/
放置于 /doc/ 目录下。

以下为中文帮助安装方法之参考，本项目中已安装：

---
在Vim中输入命令:help，即可进入帮助页面，默认是英文帮助，如果你喜欢看中文，可以通过以下方式安装中文帮助内容：
1. 下载中文帮助的文件压缩包
2. 解压，把doc目录下的文件复制到~/.vim/doc下
3. 确认在.vimrc中设置了set helplang=cn
4. 输入命令:help即可进入中文帮助

#### pathogen插件管理
pathogen 下载自 https://github.com/tpope/vim-pathogen
放置于 /autoload/ 目录下

pathogen在.vim目录下建立bundle文件，所有的插件都会在该目录下管理。
当Vim启动时，会自动执行runtimepath(rtp)列表中所包含文件夹下的vim脚本，pathogen会在启动时把./vim/bundle下的文件夹中的插件按照一定顺序递归加载到rtp中，这样Vim启动时，通过pathogen管理的插件就生效了。

有了pathogen之后，一般.vim文件夹下只有三个文件夹：autoload、bundle和doc，其他插件将被安装在bundle文件夹下。

以下为 pathogen 插件安装方法之参考，本项目中已安装：

---
1. 在.vim文件夹下建立autoload和bundle目录
2. 从下载地址获取pathogen.vim文件，将其复制到autoload目录下
3. 在.vimrc文件中增加如下代码：
    call pathogen#infect()

#### NERDTree
NERDTree 下载自 https://github.com/scrooloose/nerdtree
放置于 /bundle/nerdtree/ 目录下

NERDTree是Vim最常用的插件之一，可以在Vim运行时显示目录和文件结构，
类似TextMate左侧的文件浏览器，但操作起来更为方便，
你可以在手不离开键盘的情况下快速浏览文件，并在文件和文件夹之间进行切换。

以下为 pathogen 插件安装方法之参考，本项目中已安装：

---
1. 进入.vim/bundle目录
2. 执行git clone git://github.com/scrooloose/nerdtree.git
3. 下载完成后，在bundle下会多出一个nerdtree的文件夹，所有相关插件都在该文件夹下
4. 在Vim中运行:Helptags来生成NERDTree的在线帮助tags

---
##### 使用说明
打开Vim，输入:NERDTree，即可呼出执行Vim命令的当前目录的文件目录。为了方便使用，我在.vimrc中定义了快捷键，可以用Ctrl+t打开NERDTree，你可以定义自己习惯的快捷键。

NERDTree提供了丰富的键盘操作方式来浏览和打开文件，我简单介绍一些常用的快捷键：

和编辑文件一样，通过h j k l移动光标定位
o 打开关闭文件或者目录，如果是文件的话，光标出现在打开的文件中
go 效果同上，不过光标保持在文件目录里，类似预览文件内容的功能
i和s可以水平分割或纵向分割窗口打开文件，前面加g类似go的功能
t 在标签页中打开
T 在后台标签页中打开
p 到上层目录
P 到根目录
K 到同目录第一个节点
J 到同目录最后一个节点
m 显示文件系统菜单（添加、删除、移动操作）
? 帮助
q 关闭
想了解更多操作方式，可以通过? 查看详细的帮助信息。

### Command-T
Command-T 下载自 https://wincent.com/products/command-t
放置于 /bundle/command-t 目录下。

Command-T是一个基于Ruby和C扩展实现的快速文件浏览的插件，
类似TextMate的Go to File（Command+T呼出）功能，
或Eclipse的Open Resource（Command+Shift+r）功能，
可以通过模糊匹配快速定位并打开文件。

以下为 Command-T 安装方法之参考，本项目中已安装：

---
On Linux and similar platforms, the linked version of Ruby will depend on
your distribution. You can usually find this out by examining the
compilation and linking flags displayed by the |:version| command in Vim, and
by looking at the output of:

  :ruby puts "#{RUBY_VERSION}-p#{RUBY_PATCHLEVEL}"

Some Linux distributions package Ruby development tools separately from Ruby
itself; if you're using such a system you may need to install the "ruby-dev",
"ruby-devel" or similar package using your system's package manager in order
to build Command-T.

If you manage your entire `~/.vim` folder using Git then you can add the
Command-T repository as a submodule:

  cd ~/.vim
  git submodule add https://github.com/wincent/command-t.git bundle/command-t
  git submodule init

Or if you just wish to do a simple clone instead of using submodules:

  cd ~/.vim
  git clone https://github.com/wincent/command-t.git bundle/command-t


Wherever the Command-T files were installed, you can build the extension by
changing to the `ruby/command-t` subdirectory and running a couple of commands
as follows:

  cd ~/.vim/bundle/command-t/ruby/command-t
  ruby extconf.rb
  make

1. ctrl+j/k 上下选择文件，选中后回车打开文件
2. ctrl+t 以tab方式打开文件
3. ctrl+s/v 可以水平或垂直分割窗口打开文件
4. ctrl+c 退出该模式

## 其他

欢迎各位提供关于插件和配置的建议。
由于本项目是出于个人使用的目的建设的，
所以并不接受 push request。

您可以
*	下载 和/或 使用本项目或本项目的任何组成部分；
*	修改 和/或 再发行本项目，不需要署原作者名（不包括插件本身）；

*注：本作者仅享有项目中目录组织以及配置文件的著作权。Vim 及该项目中使用的 Vim 插件的著作权归原作者所有。使用请遵守其版权协议*

