# SourceTree简单介绍
SourceTree 是一个 Git（/Mercurial）图形化客户端，把命令行的版本控制操作做成可视化按钮和列表，方便你管理代码版本、分支与提交记录。

# 前置条件配置
## git-bash 配置

通过以下命令行进行生成 ssh-key

```
ssh-keygen.exe
```

执行命令后，一路按下回车

完成 ssh-key 的生成操作，记住ssh-key的存放位置：c:/Users/xxx/.ssh/id_rsa
![Pasted_20260419112706_Sourcetree 与 Github 进行协作管理代码](Sourcetree%20%E4%B8%8E%20Github%20%E8%BF%9B%E8%A1%8C%E5%8D%8F%E4%BD%9C%E7%AE%A1%E7%90%86%E4%BB%A3%E7%A0%81_assets/Pasted_20260419112706_Sourcetree%20%E4%B8%8E%20Github%20%E8%BF%9B%E8%A1%8C%E5%8D%8F%E4%BD%9C%E7%AE%A1%E7%90%86%E4%BB%A3%E7%A0%81.png)

同时获取ssh-key具体秘钥

```
cat ~/.ssh/id_rsa.pub
```

## 配置 SourceTree

打开 Source Tree → 工具 → 选项

1、将 SSH 客户端选择为 OpenSSH；

2、将 git-bash 中生成的 ssh-key 的地址填入：

# SourceTree 界面功能介绍（TODO）

| 类型       | 描述                        |
| -------- | ------------------------- |
| build    | 发布版本                      |
| chore    | 构建过程或辅助工具的变动              |
| ci       | 持续集成修改                    |
| docs     | 文档修改                      |
| feat     | 新功能（feature）              |
| fix      | 修复bug                     |
| merge    | 代码合并                      |
| perf     | 优化相关，比如提升性能、体验            |
| refactor | 重构（即不是新增功能，也不是修改bug的代码变动） |
| revert   | 回滚到上一个版本                  |
| style    | 代码格式修改                    |
| test     | 增加测试（代码测试，不是测试平台的测试用例）    |

scope(可选)

scope用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视项目不同而不同。

例如在Angular，可以是location，browser，compile，rootScope， ngHref，ngClick，ngView等。如果你的修改影响了不止一个scope，你可以使用*代替。

subject(必须)

subject是commit目的的简短描述，不超过50个字符，切忌模糊、意义不明的描述。

特定测试用例的描述，以_开头，例如BP_101000-修改xxxxx

例子
```
fix(DAO): 用户查询缺少username属性

feat(Controller): 用户查询接口开发

perf: 优化大文件日志解析

refactor: BP_101000-重构xxx测试逻辑
```