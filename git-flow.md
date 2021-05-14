## GitFlow常用命令

1. git flow init
2. git flow feature start my-feature
3. git flow feature finish my-feature

## GitFlow的常用分支
1. master
    主分支 , 产品的功能全部实现后 , 最终在master分支对外发布
    该分支为**只读分支** , 只能从其他分支(**release/hotfix**)合并 , 不能在此分支修改
    另外所有在master分支的推送应该打标签做记录,方便追溯, 例如release合并到master , 或hotfix合并到master
2. develop
    主开发分支 , 基于master分支克隆, 包含所有要发布到下一个release的代码
    该分支为**只读分支** , 只能从其他分支合并, 不能在此分支修改
    feature功能分支完成 , 合并到develop(**不推送**)
    **develop拉取release分支** , 提测; 例如release/hotfix 分支上线完毕 , 合并到develop并推送
3. feature
    功能开发分支 , 基于develop分支克隆 , 主要用于新需求新功能的开发
    功能开发完毕后合到develop分支(未正式上线之前不推送到远程中央仓库!!!)
    feature分支可同时存在多个 , 用于团队中多个功能同时开发 , 属于临时分支 , 功能完成后可选删除
4. release
    测试分支 , 基于feature分支合并到develop之后  , **从develop分支克隆**
    主要用于提交给测试人员进行功能测试 , 测试过程中发现的BUG在本分支进行修复 , **修复完成上线后合并到develop/master分支并推送(完成功能) , 打Tag**
    属于临时分支 , 功能上线后可选删除
5. hotfix
    补丁分支 , 基于master分支克隆 , 主要用于对线上的版本进行BUG修复
    **修复完毕后合并到develop/master分支并推送 , 打Tag**
    属于临时分支 , 补丁修复上线后可选删除
    所有hotfix分支的修改会进入到下一个release


## 主要工作流程
1. 初始化项目为gitflow , 默认创建master分支 , 然后从master拉取第一个develop分支

2. 从develop拉取feature分支进行编码开发(多个开发人员拉取多个feature同时进行并行开发 , 互不影响)

3. feature分支完成后 , 合并到develop(**不推送** , feature功能完成还未提测 , 推送后会影响其他功能分支的开发)
   合并feature到develop , 可以选择删除当前feature , 也可以不删除 . 但当前feature就不可更改了 , 必须从release分支继续编码修改

4. 从develop拉取release分支进行提测 , 提测过程中在release分支上修改BUG

5. release分支上线后 , **合并release分支到develop/master并推送** 合并之后 , 删除当前release分支

6. 上线之后若发现线上BUG, 从master拉取hotfix进行BUG修改

7. hotfix通过测试上线后 , 合并hotfix分支到develop/master并推送; 合并之后 , 删除当前hostfix

8. 当进行一个feature时 , 若develop分支有变动 , 如其他开发人员完成功能并上线 , 则需要将完成的功能合并到自己分支上
    即合并develop到当前feature分支

9. 当进行一个release分支时 , 若develop分支有变动 , 如其他开发人员完成功能并上线 , 则需要将完成的功能合并到自己分支上
    即合并develop到当前release分支 (!!! 因为当前release分支通过测试后会发布到线上 , 如果不合并最新的develop分支 , 就会发生丢代码的情况)