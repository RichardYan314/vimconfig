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

## 其他

欢迎各位提供关于插件和配置的建议。
由于本项目是出于个人使用的目的建设的，
所以并不接受 push request。

您可以
*	下载 和/或 使用本项目或本项目的任何组成部分；
*	修改 和/或 再发行本项目，不需要署原作者名（不包括插件本身）；

*注：本作者仅享有项目中目录组织以及配置文件的著作权。Vim 及该项目中使用的 Vim 插件的著作权归原作者所有。使用请遵守其版权协议*

