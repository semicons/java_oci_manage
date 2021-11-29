
# <p align="center">oci-manage⭐</p>
<p align="center">暂未开源，介意请勿使用，谢谢✅(目前为公测版，公测时间截止至21年底)</P>

## 免责声明
- 本仓库发布的oci-manage项目中涉及的任何脚本，仅用于测试和学习研究，禁止用于商业用途，不能保证其合法性，准确性，完整性和有效性，请根据情况自行判断.

- 所有使用者在使用oci-manage项目的任何部分时，需先遵守法律法规。对于一切使用不当所造成的后果，需自行承担.对任何脚本问题概不负责，包括但不限于由任何脚本错误导致的任何损失或损害.

- 如果任何单位或个人认为该项目可能涉嫌侵犯其权利，则应及时通知并提供身份证明，所有权证明，我们将在收到认证文件后删除相关文件.

- 任何以任何方式查看此项目的人或直接或间接使用该项目的任何脚本的使用者都应仔细阅读此声明。本人保留随时更改或补充此免责声明的权利。一旦使用并复制了任何相关脚本或oci-manage项目的规则，则视为您已接受此免责声明.

您必须在下载后的24小时内从计算机或手机中完全删除以上内容.

> 您使用或者复制了本仓库且本人制作的任何脚本，则视为`已接受`此声明，请仔细阅读

## 环境

- [JDK] 1.8

- [LINUX] Ubuntu20.04(已测试).Debian(未测试，但是应该可以).Centos(需手动安装jdk8)
- [Windows]不支持

## 已实现功能
* [x] 开机(amd和刷arm)
* [x] 一键查询和更改ip
* [x] 修改硬盘大小和性能
* [x] 删除硬盘
* [x] tg通知
* [x] 终止实例
* [x] 开放安全组

## 正在开发的功能
* [ ] 开机支持更多CPU
* [ ] 批量oci config
* [ ] 使用代理进行操作
* [ ] 修改用户信息（密码，邮箱之类）
* [ ] bot操作
* [ ] 定制功能请TG频道留言


## 文件说明
```text
│  sh_java_oci.sh       # 脚本文件 内置参数可修改 bash sh_java_oci.sh执行 
│  jar_oci_manage.jar   # 程序主文件 需要跟 脚本文件在同一个目录 如不在一个目录 请执行 bash sh_java_oci.sh /xx/xx/xx.jar(程序文件的绝对路径)
│  README.md            # 说明文档
```

#### 一、Linux一键部署或更新（运行完后使用bash sh_java_oci.sh可再次运行）
```bash
sudo rm -rf linux-oci-semicons.tar.gz sh_java_oci.sh jar_oci_manage.jar && wget -O linux-oci-semicons.tar.gz https://github.com/semicons/java_oci_manage/releases/download/latest/linux-oci-semicons.tar.gz && tar -zxvf linux-oci-semicons.tar.gz && sudo chmod +x   sh_java_oci.sh && ./sh_java_oci.sh
```

#### 二、手动安装
```text
  1）下载压缩包 解压文件 tar -zxvf xxx.tar.gz 
  2）sudo chmod +x sh_java_oci.sh
```
##### 使用说明
```text
如何运行？
bash sh_java_oci.sh （正常运行指令）
screen -S sh_java_oci bash sh_java_oci.sh （后台运行指令，使用指令后可关闭窗口）
screen -r sh_java_oci （查看后台程序运行详细）

参数如何设置？
编辑本脚本或复制下面配置参数到任意自定义文档进行开机设定（不开机填不填无影响）
指令支持传参 
如：bash sh_java_oci.sh -m <你的配置文件路径,不写取本文档配置>
-o <oci config路径 不写取默认路径 ~/.oci/config>
-j <自定义jar包路径,不写取默认当前路径>
```
##### 编辑配置参数
- 编辑脚本文件 sh_java_oci.sh 或复制下面参数到自定义文档
```text

#此参数勿动 为参数读取的开始
begin=begin

#cpu类型 请填写ARM或AMD （必填）
cpuType=ARM

#cpu数量 （必填）
cpus=2

#内存数量 （必填）
memorySize=12

#硬盘数量 （必填）
volumeSize=50

#公钥内容 非路径 提示:注意保存对应私钥 （必填）
sshPublicKey=""

#要刷的vps的数量 （非必填，默认为1）
vpsNum=2

#vps名称 非必填
vpsName=""


#非必填项
#tg bot key
bot_key=""

#用户id
chat_id=""

#最小延迟时间（单位：秒）
lowTime=6

#最大延迟时间 （单位：秒）
highTime=15

#此参数勿动 为参数读取的结束
end=end
```

##### oci（甲骨文）变量
- 【操作导航】甲骨文后台=>用户设置>>资源>>API秘钥>>添加API秘钥 （没有用户设置的请直接搜用户 点击用户 或者 点击左边菜单身份和安全=>用户=>点击用户=>API秘钥>>添加API秘钥）
- 说明∶此处配置是连接甲骨文云接口的所必须参数，获取位置看↑操作导航
```text
大致如下↓

[DEFAULT]
user=ocid1.user.oc1..aaaaaaaaxxxxgwlg3xuzwgsaazxtzbozqq
fingerprint=b8:33:6f:xxxx:45:43:33
tenancy=ocid1.tenancy.oc1..aaaaaaaaxxx7x7h4ya
region=ap-singapore-1
key_file=<写你的密钥文件路径>
```
- 将在甲骨文用户设置添加api密钥的配置文件预览里面的参数 在用户根目录创建 vim或者vi ~/.oci/config并粘贴进去(请注意 config文件内的私钥位置要正确，私钥在你添加api的时候生成下载的，一般放到跟config同路径，如：key_file=/root/.oci/oci_api_key.pem)
- ![image](https://github.com/semicons/java_oci_manage/blob/main/1637652579448.jpg)



#### 其他帮助
- Q:tg频道?
- A:https://t.me/agentONE_R  (关注后点击频道名字可以进行讨论或求助)


#### 更新日志
<details>
<summary>查看Releases说明</summary>
 
> 证明该项目仍然存活


</details>
