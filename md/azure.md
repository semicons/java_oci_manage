### azure云获取API参数和上传配置
```text
1. 登录Azure后台，选择右上角的Cloud Shell
2. 选择PowerShell，执行如下命令，获取API相关参数
az ad sp create-for-rbac --role contributor --scopes /subscriptions/$(az account list --query [].id -o tsv)
3. 使用/oci 命令直接上传你的配置 如：
  /oci {
  "appId": "xxxxx-xxx-xx-xxx-xxxx",
  "displayName": "azure-cli-11111-12-111-11-222-22",
  "password": "xxxxx~oxjTxxxxxxxxb_I",
  "tenant": "xxxx-xxxx-xxxx-xxxx-xxxxxxxx"
  }
```
![image](https://github.com/semicons/java_oci_manage/blob/main/az.jpg)
