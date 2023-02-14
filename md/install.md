#### 1.Linux一键安装/更新（运行完后使用bash sh_java_oci.sh可重启运行）
```bash
wget -O gz_client_bot.tar.gz  https://github.com/semicons/java_oci_manage/releases/latest/download/gz_client_bot.tar.gz && tar -zxvf gz_client_bot.tar.gz --exclude=client_config  && tar -zxvf gz_client_bot.tar.gz --skip-old-files client_config && chmod +x sh_client_bot.sh && bash sh_client_bot.sh
```
#### 2. 修改配置文件参数
- 按参数说明编辑client_config文件（model填写local为启动本地无公网IP模式）
```text
#在oci=begin和oci=end之间放入你的API配置信息 支持多个配置文件 机器人切换profile可更换操作配置
oci=begin

[DEFAULT]
user=ocid1.user.oc1..aaaaaaaaxxxxgwlg3xuzwgsaazxtzbozqq
fingerprint=b8:33:6f:xxxx:45:43:33
tenancy=ocid1.tenancy.oc1..aaaaaaaaxxx7x7h4ya
region=ap-singapore-1
key_file=写你的API密钥文件路径

[DEFAULT2]
user=ocid1.user.oc1..aaaaaaaaxxxxgwlg3xuzwgsaazxtzbozqq
fingerprint=b8:33:6f:xxxx:45:43:33
tenancy=ocid1.tenancy.oc1..aaaaaaaaxxx7x7h4ya
region=ap-singapore-1
key_file=写你的API密钥文件路径

oci=end



#用户信息 从 https://t.me/radiance_helper_bot 配置(bot可使用/raninfo命令随机生成)
#必传
username=
#必传
password=


#cloudflare 功能参数 非必传
#非必传 cloudflare邮箱
cf_email=
#非必传 cloudflare key 在我的个人资料->API令牌处->API密钥->Global API Key	获取
cf_account_key=


#非必填 本机ip和端口号 (进阶玩家选项 可填写域名) 不写将自动获取本机ip 并使用默认端口号9527 (小白用户建议不填) 如填写 格式为:https://xxx.xx:9527
local_address=
#非必填 url名称(默认为address 可在bot上修改)
local_url_name=

#非必填 启动模式 填写local为启动本地无公网IP模式(只要能联网即可) 不填或填其他 则启动端口模式
model=



#在azure=begin和azure=end之间放入你的azure的API配置信息 支持多个配置文件 机器人切换profile可更换操作配置 上传配置支持使用原格式({"appId":"xxx","password":"xxx"...})上传 
azure=begin

[az001]
appId=551xxxx7-xxxx-xxxx-xxxx-b9xxxx60cc65
password=T618Q~.LIy_xxxxx~jm~xxxxxx
tenant=xxxx3713-xxxx-4cb5-xxxx-3001060xxxxx

azure=end
```

#### 3. 启动、终止、查看日志、卸载
```text
请先在配置文件内输入对应的参数，然后运行下方需要的指令

启动或重启
bash sh_client_bot.sh 

查看日志(ctrl + c退出日志)
tail -f log_r_client.log  

终止程序
ps -ef | grep r_client.jar | grep -v grep | awk '{print $2}' | xargs kill -9  

卸载程序
rm -rf gz_client_bot.tar.gz client_config r_client.jar sh_client_bot.sh log_r_client.log debug-.log 
如也不需要JDK也可卸载：apt-get remove openjdk*

```
