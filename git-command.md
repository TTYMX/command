## git 命令
git reset HEAD 可以取消add的文件 HEAD~1

git reset --mixed HEAD^ 可以取消commit的文件
默认是--mixed
--mixed 撤销commit和add
--soft  不撤销add
--hard  撤销commit和add并恢复都上一次commit的状态

git commit --amend -m 修改提交文案


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







