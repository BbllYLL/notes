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

同时获取ssh-key具体秘钥

```
cat ~/.ssh/id_rsa.pub
```

## 配置 SourceTree

打开 Source Tree → 工具 → 选项

1、将 SSH 客户端选择为 OpenSSH；

2、将 git-bash 中生成的 ssh-key 的地址填入：

# SourceTree 界面功能介绍（TODO）

