
# <p align="center">oci-bot⭐</p>
<p align="center">暂未开源，介意请勿使用，谢谢✅</P>

## 免责声明
- 本仓库发布的oci-manage项目中涉及的任何脚本，仅用于测试和学习研究，禁止用于商业用途，不能保证其合法性，准确性，完整性和有效性，请根据情况自行判断.

- 所有使用者在使用oci-manage项目的任何部分时，需先遵守法律法规。对于一切使用不当所造成的后果，需自行承担.对任何脚本问题概不负责，包括但不限于由任何脚本错误导致的任何损失或损害.

- 如果任何单位或个人认为该项目可能涉嫌侵犯其权利，则应及时通知并提供身份证明，所有权证明，我们将在收到认证文件后删除相关文件.

- 任何以任何方式查看此项目的人或直接或间接使用该项目的任何脚本的使用者都应仔细阅读此声明。本人保留随时更改或补充此免责声明的权利。一旦使用并复制了任何相关脚本或本项目的规则，则视为您已接受此免责声明.

您必须在下载后的24小时内从计算机或手机中完全删除以上内容.

> 您使用或者复制了本仓库且本人制作的任何脚本，则视为`已接受`此声明，请仔细阅读

## 环境

- [JDK] 1.8

- [LINUX] Ubuntu20.04(已测试).Debian(未测试，但是应该可以).Centos(需手动安装jdk8)
- [Windows]需自行配置jdk环境变量运行

## 已实现功能
* [x] 开机(amd和刷arm 支持root开机)
* [x] 一键查询和更改ip
* [x] 修改硬盘大小和性能
* [x] 升级、降级实例、修改实例名称、打开/关闭实例监控
* [x] 删除硬盘
* [x] tg通知
* [x] 终止实例
* [x] 开放云面板安全组
* [x] 云账户管理（修改租户名、修改邮箱、添加管理员用户、删除用户、重置密码）（由于甲骨文问题，暂缓开通）
* [x] bot操作

## 正在开发的功能
* [ ] CF快捷操作
* [ ] 用户使用习惯快捷操作
* [ ] 上传代理快捷操作
* [ ] 上传API快捷操作
* [ ] 定制功能请TG频道留言

# 此处为客户端配置说明,全流程说明请关注bot /help 获取

## 1.文件说明（**请仔细从上往下阅读文档，你将毫无疑问**）
```text
│  sh_client_bot.sh       # 脚本文件
│  r_client.jar   # 程序主文件 需要跟 脚本文件在同一个目录
   client_config  #配置文件 需跟主程序在同一目录
```

#### 2. ①Linux一键部署/更新(暂未开通)（运行完后使用bash sh_java_oci.sh可再次运行）
```bash
wget -O r_client.tar.gz https://github.com/semicons/java_oci_manage/releases/download/latest/r_client.tar.gz && tar -zxvf r_client.tar.gz --skip-old-files client_config  && chmod +x sh_client_bot.sh
```
体验版如下
```bash
wget -O r_client.tar.gz https://github.com/semicons/java_oci_manage/releases/download/v2.0.0.1/r_client.tar.gz && tar -zxvf r_client.tar.gz --skip-old-files client_config  && chmod +x sh_client_bot.sh
```

#### ②手动安装
```text
  1）下载压缩包 解压文件 tar -zxvf xxx.tar.gz 
  2）sudo chmod +x sh_client_bot.sh
```
##### 3. 使用说明
```text
如何运行？
请先在配置文件内输入对应的参数，然后运行下方需要的指令
需要开启默认9527端口
bash sh_client_bot.sh （正常前台运行指令）
screen -S sh_client_bot bash sh_java_oci.sh （后台运行指令，使用指令后可关闭窗口）
screen -r sh_client_bot （查看后台程序运行详细  可ctrl + c 取消后台运行）
脚本支持传参 bash sh_client_bot.sh 8888  更换默认9527端口
显示 服务已启动成功... 代表客户端已成功启动


参数如何设置？
请在client_config文件 oci=begin  oci=end 中间放入oracle API参数
username 和 password对应填写
```
##### 4. 编辑配置参数
- 编辑脚本文件 sh_java_oci.sh 或复制下面参数到自定义文档
```text

#在oci=begin和oci=end之间放入你的API配置信息
oci=begin

[DEFAULT]
user=ocid1.user.oc1..aaaaaaaaxxxxgwlg3xuzwgsaazxtzbozqq
fingerprint=b8:33:6f:xxxx:45:43:33
tenancy=ocid1.tenancy.oc1..aaaaaaaaxxx7x7h4ya
region=ap-singapore-1
key_file=写你的API密钥文件路径

oci=end

#用户信息 从 配置
username=
password=

```

##### 5. 甲骨文后台获取API参数
- 【操作导航，任意一种均可】
- 1.甲骨文后台=>用户设置>>资源>>API秘钥>>添加API秘钥->(在指纹右侧三个点处查看参数)
- 2.如没有用户设置的请直接搜用户(切中文语言) 点击选择某个用户名 API秘钥>>添加API秘钥->(在指纹右侧三个点处查看参数)
- 3.不会搜的点击左边菜单一栏 找到身份和安全=>用户=>点击选择某个用户名=>API秘钥>>添加API秘钥）->(在指纹右侧三个点处查看参数)
- 说明∶此处配置是连接甲骨文云接口的所必须参数(还不会建议不玩甲骨文)
```text
大致如下↓

[DEFAULT]
user=ocid1.user.oc1..aaaaaaaaxxxxgwlg3xuzwgsaazxtzbozqq
fingerprint=b8:33:6f:xxxx:45:43:33
tenancy=ocid1.tenancy.oc1..aaaaaaaaxxx7x7h4ya
region=ap-singapore-1
key_file=写你的密钥文件路径
```
- 将在甲骨文用户设置添加api密钥的配置文件预览里面的参数 放入到client_config配置文件内(请注意 key_file的私钥位置要正确，私钥文件在你添加api的时候生成下载的，然后放入你想放的位置，如：key_file=/root/oci/oci_api_key.pem)
- ![image](https://github.com/semicons/java_oci_manage/blob/main/1637652579448.jpg)



#### 其他帮助常见问题
- Q:tg频道?
- A:https://t.me/agentONE_R  (关注后点击频道名字可以进行讨论或求助)
- 
- Q:错误 Caused by: java.io.FileNotFoundException: /root/.oci/oci_api_key.pem # TODO (没有那个文件或目录) 
- A:删除后面的# TODO
- 
- Q:如何ssh登录？
- A:使用生成公钥的时候对应的私钥登录
- 
- Q:Unable to locate package openjdk***？
- A:请谷歌搜索centos(对应系统)8(对应系统版本)如何安装openjdk8



#### 更新日志
<details>
<summary>查看Releases说明</summary>
 
> 证明该项目仍然存活


</details>
