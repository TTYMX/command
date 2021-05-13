
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







