### azure云获取API参数
```text
1. 登录Azure后台，选择右上角的Cloud Shell

2. 选择PowerShell，执行如下命令，获取API相关参数

az ad sp create-for-rbac --role contributor --scopes /subscriptions/$(az account list --query [].id -o tsv)

```
![image](https://github.com/semicons/java_oci_manage/blob/main/az.jpg)
