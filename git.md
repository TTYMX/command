
## Git主要优点有
1. 分布式存储 , 本地仓库包含了远程仓库的所有内容
2. 安全性高 , 远程仓库文件丢失了也不怕
3. 优秀的分支模型 , 创建/合并分支非常的方便
4. 方便快速 , 由于代码本地都有存储 , 所以从远程拉取和分支合并时都非常快捷
5. 当分支过多时 ,我们采用Git Flow的模式

## git 命令
1. git reset HEAD 可以取消add的文件 HEAD~1

2. git reset --mixed HEAD^ 可以取消commit的文件
    >--mixed 撤销commit和add 默认值<br>
    >--soft  不撤销add<br>
    >--hard  撤销commit和add并恢复都上一次commit的状态

3. git commit --amend -m 修改提交文案

4. git rebase -i start-commit end-commit ***我不是很懂晚点看看***


## 解决git打开慢的方法
在host中添加 13.229.188.59 github.com

## gitignore 语法
1. 所有空行或者以注释符号 ＃ 开头的行都会被 Git 忽略。
2. 可以使用标准的 glob 模式匹配。即为shell中正则表达式
3. 匹配模式最后跟反斜杠（/）说明要忽略的是目录。
4. 要忽略指定模式以外的文件或目录，可以在模式前加上惊叹号（!）取反。
举例如下:
    <<<
        注释所有已a结尾除了lib.a文件
        *.a
        !lib.a

        忽略根目录下的abc文件
        /abc

        忽略abc文件夹
        abc/

    >>>



###需要知道的单词
* repository  仓库
* track 跟踪文件
* storage 暂存
* remote 远程


###创建所需命令
* git init
* git add README.md
* git commit -m "first commit"
* git remote add origin https://github.com/TTYMX/20180815-git-test.git //更改链接远程
* git push -u origin master


###后续改动

* git add
* git commit -m
* git push

###查看命令

* git config --global user.name
* git config user.email
* vim ~/.gitconfig 查看配置文件
* git config --list 查看配置信息
* git config <key> 查看某项配置的信息

###设置命令

所有的操作
* git config --global user.name 'aaa'
* git config --global user.email 'youremail@email,com'
* git config --global push.default

* 一个特定的项目(很少用)
    > 1. git config user.name 'aaa'
    > 2. git config user.email 'email@email.com'

###基本命令

pwd 查看当前所在文件位置
1. 删除本地分支
    > git branch -d <BranchName>
2. 删除远程分支
    > git push origin --delete <BranchName>
3. 查看所有分支
    > git branch -a
4. 克隆代码
    > git clone [url] <br>
    会自动生成.git文件  <br>
    可以自定义仓库的名字 git clone [url] name
5. 查看当前文件的状态
    > git status

###帮助命令

* git help <verb>config
* git <verb> --version  可以使用git --查看可以看那些命令

##详解命令
* git push origin master 将本地分支的更新推送到远程主机
    > 推送 远程主机 本地master分支 如果远程的master分支不存在创建之<br>
    > 本地分支被省略，表示删除远程分支
    git push origin :master等同于git push origin --delete master<br>
    > 如果本地分支和远程分支存在追踪关系,则本地分支和远程分支都可以省略
    git push origin<br>
    > 如果当前分支只有一个追踪分支，那么主机名也可以省略　git push<br>
    > 如果当前分支和多个主机存在追踪关系，可以用-u选项指定一个默认主机
    　git push -u origin master

* git add 开始跟踪一个文件
    > eg: git add README.md

* git status 查看文件状态
    > git status -s 缩减的展示

* git rm 移出跟踪的文件
    > git rm README.md<br>
    git rm --cached README.md

###状态

 * ?? 没有追踪的文件
 * A  已经追踪的文件
 * 绿M 已经追踪了没有提交过修改的文件
 * 红M 已经提交了修改的文件
 * 结果为空表示很干净了,全部提交了
 * git diff 本身只显示尚未暂存的改动，而不是自上次提交以来所做的所有改动。 所以有时候你一下子暂存了所有更新过的文件后，运行 git diff 后却什么也没有，就是这个原因。

###远程仓库
* git clone [url]
* git remote
* git remote -v 显示需要殂谢远程仓库使用的git保存的简写和其对应的url
* git remote add name url 添加远程仓库
* git remote rename name new_name 更改远程仓库的名字


###恢复文件内容
* git checkout filename 恢复文件到上传时候的内容

###分支的处理
* git branch 查看分支
* git branch -a 查看所有的分支 包括远程分支
* git branch name 创建分支
* git checkout branch_name 切换分支的名字
* git branch -D branch_name 删除分支
* git branch -m name new_name 重命名分支

###checkout的应用
* git checkout filename 恢复到提交的版本
* git checkout filename 如果本地删除,没有添加,可以恢复出来
* 文件名字前面显示D表示删除的文件

###删除分段区域的更改
* 当执行添加操作的时候,文件将从本地存储库移动到暂存区,如果用户意外修改的文件提交到了暂存区则可以使用git checkout命令恢复其修改

* 在git中,有一个HEAD指针重视指向最新的提交.如果要从分段区域中撤销更改,则可以使用git checkout 命令, 必须提供一个附加参数, 即HEAD指针.
附加的提交指针参数指示git checkout命令重置工作树,并删除分段更改

* __<font color=#ff0000 font-size=7 face="黑体">
已经git add 的如果想要撤销更改,
可以使用 git checkout head -- filename 会撤销提交的变化,本地的也会删除</font>__

### 用git复位移动头指针  git reset
* 经过少量更改后, 可以决定删除这些改动. git reset命令可以用于复位或恢复更改. 我们可以执行三种不同类型的复位操作
* --soft选项 每个分支都有一个HEAD指针,他指向最新的提交,如果用--soft选项后跟提交ID的 git reset命令,那么它将重置HEAD指针提交的ID的git reset命令,
那么他将重置HEAD指针而不会破坏任何东西
* .git/refs/heads/master 文件存储HEAD指针的提交ID, 可以使用git log -1命令验证它
###倒退命令
* cat .git/refes/heads/master 查看提交版本
* git log -graph --oneline 查看提交日志
* git reset --hard HEAD^    git reset可以将master引用指向任意一个村子的提交id(-hard参数会破坏工作区未提交的改动)
    >注意: 重置命令很危险,因为重置让提交历史也改变了,通过浏览历史不能恢复

* git提供了一个挽救机制
    > 显示文件的内容<br>
        git reflog show master | head -5 将最新的改变放到最前面显示<br>
        输出中表达式<refname>@{<n>}的含义:引用<refname>之前第<n>次改变时的SHA1哈希值
   <br>
        重置master为两次改变之前值:<br>
        git reset --hard master@{2}




###git 命令
git 有很多优势, 其中之一便是远程操作非常简便.

* git clone

    1.解释

        * 将存储库可控到新目录中

    2.简介

        * git clone [--template=<template_directory>]
                [-l] [-s] [--no-hardlinks] [-q] [-n] [--bare] [--mirror]
                [-o <name>] [-b <name>] [-u <upload-pack>] [--reference <repository>]
                [--dissociate] [--separate-git-dir <git dir>]
                [--depth <depth>] [--[no-]single-branch]
                [--recurse-submodules] [--[no-]shallow-submodules]
                [--jobs <n>] [--] <repository> [<directory>]

    3.描述

        * 将存储库克隆到新创建的目录中, 为克隆的存储库中的每个分支创建远程跟踪分支(使用 git branch -r 可见), 并从克隆检出存储库作为当前活
          动的初始分支
        * 在克隆之后, 没有参数的普通的 git 提取将更新所有远程跟踪分支, 并且没有参数的 git pull 将会把远程分支合并到当前的分支(如果存在)
        * 此默认配置通常在 refs/remotes/origin 下创建远程分支头的引用, 并通过初始化 remoote.origin.url 和 remote.origin.fetch 配置
          变量来实现
        * 执行远程操作的第一步, 通常是从远程主机克隆一个版本库,这时就要用到 git clone 命令: git clone 版本库网址; 例如克隆 jquery 的版
          本库: git clone http://github.com/jquery/jquery.git
        * 该命令会在本地主机生成一个目录, 与远程主机的版本库同名. 如果要指定不同的目录名, 可以将目录名作为 git clone 命令的第二个参数,
          例如: git clone 版本库网址 本地目录名
        * git clone 支持多种协议, 有 https ssh git 本地文件协议

    3.示例

        * git clone https://example.com/path/to/repo.git
        * git clone http://git.oschina.net/yiibai/sample.git
        * git clone ssh://example.com/path/to/repo.git
        * git clone git://example.com/path/to/repo.git
        * git clone /opt/git/project.git
        * git clone file:///ope/git/project.git
        * git clone ftps://example.com/path/to/repo.git
        * git clone rsync://example.com/path/to/repo.git
        * git clone [user@]example.com:path/to/repo.git

    4.应用场景示例

        * 从上游克隆下来 git clone 路径 mydir
        * 从当前目录中使用克隆 git clone -l -s -n . ../copy
        * 从现有的本地目录借用从上游克隆 git clone --reference /git/linux.git 路径 mydir
        * 创建一个裸存储库将更改发布给公众 git clone --bare -l /home/proj/.git /pub/scm/pro.git

* git remote
    >命令管理一组跟踪的存储库
    <br>
    <br>git remote [-v | --verbose]
    <br>git remote add [-t <branch>] [-m <master>] [-f] [--[no-]tags] [--mirror=<fetch|push>] <name> <url>
    <br>git remote rename <old> <new>
    <br>git remote remove <name>
    <br>git remote set-head <name> (-a | --auto | -d | --delete | <branch>)
    <br>git remote set-branches [--add] <name> <branch>…​
    <br>git remote get-url [--push] [--all] <name>
    <br>git remote set-url [--push] <name> <newurl> [<oldurl>]
    <br>git remote set-url --add [--push] <name> <newurl>
    <br>git remote set-url --delete [--push] <name> <url>
    <br>git remote [-v | --verbose] show [-n] <name>…​
    <br>git remote prune [-n | --dry-run] <name>…​
    <br>git remote [-v | --verbose] update [-p | --prune] [(<group> | <remote>)…​]

* git fetch
    >命令用于从另一个存储库下载对象和引用
     <br>git fetch [<options>] [<repository> [<refspec>…]]
     <br>git fetch [<options>] <group>
     <br>git fetch --multiple [<options>] [(<repository> | <group>)…]
     <br>git fetch --all [<options>]
     <br>
     从一个或多个其他存储库中获取分支和/或标签(统称为引用)以及完成其历史所必须的对象<br>
     远程跟踪分支已更新(commit),需要将这些更新取回到本地,这时就要用到git fetche命令

* git pull
    >命令用于从另一存储库或本地分支获取并集成(整合)<br>
    git pull 命令的作用是: 取回远程主句某个分支的更新,再与本地的指定分支合并,它的完整格式稍稍有点复杂
    <br>
    git pull [options] [<repository> [<refspec>…]]
    <br>
    将远程存储库中的更改合并到当前分支中,在默认模式下,git pull是git fetch后跟gitmerge FETCH_HEAD的缩写
    <br>
    梗准确地说,git pull是用给定的参数运行git fetch, 并调用git merge将检索到的分支头合并到当前分支中
    <br><br>
    实例
    <br>$ git pull <远程主机名> <远程分支名>:<本地分支名>
    <br>比如，要取回origin主机的next分支，与本地的master分支合并，需要写成下面这样
    <br>$ git pull origin next:master
    <br>如果远程分支(next)要与当前分支合并，则冒号后面的部分可以省略。上面命令可以简写为：
    <br>$ git pull origin next
    <br>上面命令表示，取回origin/next分支，再与当前分支合并。实质上，这等同于先做git fetch，再执行git merge。
    <br>$ git fetch origin
    <br>$ git merge origin/next
    <br><br>
    Git也允许手动建立追踪关系。
    <br>上面命令指定master分支追踪origin/next分支。
    <br>$ git branch --set-upstream master origin/next
    <br>如果当前分支与远程分支存在追踪关系，git pull就可以省略远程分支名。
    <br>$ git pull origin
    <br><br>
    git fetch和git pull的区别
    >>git fetch：相当于是从远程获取最新版本到本地，不会自动合并。
    <br>在实际使用中，git fetch更安全一些，因为在merge前，我们可以查看更新情况，然后再决定是否合并。

* git push
    >命令用于将本地分支的更新推送到远程的主机,他的格式和git pull 相似
    <br>
    $ git push <远程主机名> <本地分支名>:<远程分支名>
    <br>git push [--all | --mirror | --tags] [--follow-tags] [--atomic] [-n | --dry-run] [--receive-pack=<git-receive-pack>]
    <br>[--repo=<repository>] [-f | --force] [-d | --delete] [--prune] [-v | --verbose]
    <br>[-u | --set-upstream] [--push-option=<string>]
    <br>[--[no-]signed|--sign=(true|false|if-asked)]
    <br>[--force-with-lease[=<refname>[:<expect>]]]
    <br>[--no-verify] [<repository> [<refspec>…]]
    <br><br>
    __示例__
    <br>git push origin master 将本地分支推送到master上,没有则创建master分支
    <br>git push origin :master 删除远程master分支 等同于 git push origin --delete master
    <br>git push origin 当前分支和远程分支存在追踪关系 则本地和远程分支都可以省略
    <br>git push 将当前分支推动到origin主机的对应分支,如果当前分支只有一个追踪分支,那么主机名也可以省略
    <br>git push -u origin master 将本地分支推送到origin主机,同时制定origin为默认主机,后面就可以git push了

* git config

    1.解释

        * 获取并设置存储库或全局选项, 这些变量可以控制 git 的外观和操作的各个方面

    2.语法简介

        * git config [<file-option>] [type] [--show-origin] [-z|--null] name [value [value_regex]]
          git config [<file-option>] [type] --add name value
          git config [<file-option>] [type] --replace-all name value [value_regex]
          git config [<file-option>] [type] [--show-origin] [-z|--null] --get name [value_regex]
          git config [<file-option>] [type] [--show-origin] [-z|--null] --get-all name [value_regex]
          git config [<file-option>] [type] [--show-origin] [-z|--null] [--name-only] --get-regexp name_regex [value_regex]
          git config [<file-option>] [type] [-z|--null] --get-urlmatch name URL
          git config [<file-option>] --unset name [value_regex]
          git config [<file-option>] --unset-all name [value_regex]
          git config [<file-option>] --rename-section old_name new_name
          git config [<file-option>] --remove-section name
          git config [<file-option>] [--show-origin] [-z|--null] [--name-only] -l | --list
          git config [<file-option>] --get-color name [default]
          git config [<file-option>] --get-colorbool name [stdout-is-tty]
          git config [<file-option>] -e | --edit

    3.描述

        * 可以使用次命令 查询/ 设置/ 替换/ 取消 设置选项, 该名称实际上是由 . 分割键, 该值将被转义
        * 可以使用 --add 选项将多行添加到选项, 如果要更新或者取消设置多行可能出现的选项则需要给出POSIX正则表达式 value_regex. 只有与正则
          表达式匹配的现有值或已更新或未设置. 如果要处理与正则表达式不匹配的行, 只需要在前面添加一个感叹号 !
        * 类型说明符可以是 --int 或 --bool, 以使 git config 确保变量是给定类型, 并将该值转化为规范形式, int 是简单十进制数, "true" 或
          "false" 是 bool字符串表示, 或者 --path, 它进行一些路径扩展, 如果没有类型说明符传递, 则不会对该值执行检查或者转换.
        * 读取时, 默认情况下是从系统, 全局和存储库本地配置文件读取这些值, 而选项 --system, --global, --local, --file filename 可用于
          告知命令读取和设置的位置
        * 写入时, 默认情况下是将新值写入存储库本地配置(--local)文件, 并且可使用选项 --system, --global, --file filename 来告诉命令写
          入的位置, 成功时命令返回退出代码是0, 如果非零表示命令失败
          部分或键无效(ret = 1)，
          没有提供部分或名称(ret = 2)，
          配置文件无效(ret = 3)，
          配置文件无法写入(ret = 4)，
          尝试取消设置不存在的选项(ret = 5)，
          尝试取消设置/设置多个行匹配的选项(ret = 5)
          尝试使用无效的正则表达式(ret = 6)。

    4.配置文件的存储位置

        * /etc/gitconfig文件:包含了适用于系统所有用户和所有库的值,如果你传递参数选项 --system 它将明确读写这个文件
        * ~/ .gitconfig 文件:具体到你的用户,你可以通过传递 --global 选项读写这个文件
        * .git/config 它里面可以覆盖/etc/gitconfig中的值

    5.配置用户名或者密码

        * git config --global user.name 'name'
        * git config --global user.email 'email'
        * 如果要配置某个特定的项目去除掉 --global 即可

    6.配置编辑器

        * git config --global core.editor.vim
        * git config --global core.editor

    7.配置比较工具

        * git config --global merge.tool vimdiff
        * git config --global merge.tool

    8.检查配置

        * git config --list

    9.添加配置项

        * git config --add site.name yiibai
        * add 后面的section , key , value 一项都不能少

    10.删除配置项

        * git config --local --unset site.name

    11.获取帮助

        * git help config 查看git config如何使用
        * git help config
        * git config --help
        * man git-config 不知道为什么使用不成功

* git help 命令

    1.解释

        * 显示有关 git 的帮助信息

    2.简介

        * git help [-a|--all] [-g|--guide]
                   [-i|--info|-m|--man|-w|--web] [COMMAND|GUIDE]

    3.描述

        * 没有选项, 没有给出任何命令或指导, git命令的概要和最常用的git命令的列表打印在标准输出上
        * 如果给出 --all 或者 -a 选项, 则所有可用的命令都将打印在标准输出上
        * 如果给出了 --guide 或者 -g 选项, 那么在标准输出中也会累出有用的git指南
        * 如果给出了命令或者指南, 则会提出该命令或该指南的手册页,

    4.示例

        * git help help
        * git help config
        * git config --global help.format web
        * git config help.format
        * git config --global web.browser firefox
        * git config web.browser

* git init 命令

    1.解释

        * 创建一个空的git长裤或者重新初始化一个现有的仓库

    2.简介

        *  git init [-q | --quiet] [--bare] [--template=<template_directory>]
                 [--separate-git-dir <git dir>]
                 [--shared[=<permissions>]] [directory]

    3.描述

        * 该命令是床架一个空的git仓库--基本上是一个具有objects, refs/head, refs/tabs和模板文件的.git目录. 还创建了引用主分支的HEAD和
          初始化的一个HEAD文件
        * 如果通过$GIT_OBJECT_DIRECTORY环境变量指定了对象存储目录,那么将在下面创建 sha1 目录, 否则将使用默认的 $GIT_DIR/objects目录
        * 现有存储库中运行 git init 命令是安全的. 它不会覆盖已经存在的东西. 重新运行 git init 的主要原因是拾取新添加的模板(或者如果给出了
          --separate-git-dir , 则将存储库移动到另一个地方)

    4.示例

        * git init

* git add

    1.解释

        * 将文件内容添加到索引(将修改添加到暂存区). 也就是将要提交的文件的信息添加到索引库中

    2.简介

        * git add [--verbose | -v] [--dry-run | -n] [--force | -f] [--interactive | -i] [--patch | -p]
                [--edit | -e] [--[no-]all | --[no-]ignore-removal | [--update | -u]]
                [--intent-to-add | -N] [--refresh] [--ignore-errors] [--ignore-missing]
                [--chmod=(+|-)x] [--] [<pathspec>…​]

    3.描述

        * 此命令将要提交的文件的信息添加到索引库中(将修改添加到暂存区), 以准备下一次提交分段的内容. 它通常将现有路径的当前内容作为一个整体添加,
          但是通过一些选项, 它可以用户添加内容, 只对所应用的工作树文件进行一些更改,或删除工作树中不存在的路径
        * "索引"保存工作树内容的快照, 并且将该快照作为下一个提交的内容. 因此, 在对工作树进行任何更改之后, 并且在 git commit 命令之前, 必须
          使用 git add 命令将任何新的修改的文件添加到索引
        * 该命令可以在提交之前多次执行. 它只在运行 git add 命令时添加指定文件的内容; 如果希望随后的更改包含在下一个提交中, 那么必须要再次运行
          git add 将新内容添加到索引
        * git status 命令可用于获取哪些文件具有为下一次提交分段的更改的摘要.
        * 默认情况下, git add 命令不会添加忽略的文件. 如果在命令行上显示指定了任何忽略的文件, git add 命令都将失败, 并显示一个忽略的文件列表.
          由git执行的目录递归或者文件名遍历所导致的忽略文件都将被默认忽略. git add 命令可以用 -f(force) 选型添加被忽略的文件

    4.示例

        * git add documentation/*.txt 添加documentation目录以及其子目录下的所有的*.txt内容

    5.基本用法

        * git add path
        * 这个命令可以把 path 中的文件添加到索引库中, path 可以是文件也可以是目录. git 不仅可以判断出修改的文件, 还可以判断出添加的文件,
          但是不能判断出删除的文件
        * git add . 将所有的修改添加的暂存区
        * git add *Controller 将以 Controller 结尾的文件添加
        * git add Hello* 将以 Hello 开头的文件添加
        * git add Hello? 将 Hello1.txt添加 Hello12.txt, Hello.txt 不会添加
        * git add -u path 将跟踪的文件中修改或删除的文件添加到索引库 省略 path 表示 .
        * git add -A path 将所有的文件添加到索引库 省略 path 表示 .
        * git add -i 查看所有修改或已经删除文件但是没有提交的文件, 通过 revert 子命令可以看 path 中为跟踪的文件

* git status

    1.解释

        * 用于显示工作目录和暂存区的状态. 使用此命令能看到哪些修改被暂存到了, 哪些没有, 哪些文件没有被 git tracked 到. git status 不显示
          已经 commit 到醒目历史中去的信息. 看项目历史信息要使用 git log

    2.简介

        * git status [<options>…​] [--] [<pathspec>…​]

    3.描述

        * 显示索引文件和当前HEAD提交之间的差异, 在工作树和索引文件之间有差异的路径以及工作树中没有被 git 跟踪的路径.
        * 没有 tracked 的文件分为两类, 1,已经放在工作目录没有 git add 的; 2, 编译的程序文件 例如: .pyc .obj .exe
        * 在项目的根目录下有 .gitignore 文件, 其中加入下面的内容能阻止文件出现在 git status 中 *.pyc *.tmp
        * 每次在 git commit 之前使用 git status 检查文件状态是个好习惯
        * git status -uno 可以只显示已经被 git 管理的并且被修改但没有提交的文件






