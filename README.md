# <p align="left">R-Bot⭐</p>
<p align="left">
  <a href="https://t.me/apchyo"><img src="https://img.shields.io/static/v1?label=%E7%BE%A4%E7%BB%84&message=telegram&color=brightgreen"/></a>
  <a href="https://t.me/agentONE_R"><img src="https://img.shields.io/static/v1?label=%E9%A2%91%E9%81%93&message=telegram&color=blueviolet"/></a>
  <a href="https://t.me/radiance_helper_bot"><img src="https://img.shields.io/static/v1?label=%E6%9C%BA%E5%99%A8%E4%BA%BA&message=telegram&color=red"/></a>
 <img src="https://img.shields.io/github/stars/semicons/java_oci_manage.svg?style=flat-square&label=Stars&logo=github"/>
</p>

### 前言
> 本系统目前应用于甲骨文云/azure云的一些快捷操作。
> 
### 声明
> 
> 本系统为双端制，机器人不存储任何敏感数据。
> 
> API私钥在你的客户端服务器本地，由bot驱动你的客户端操作，你可以随时关闭服务。
> 
> 介意请千万勿使用，谢谢。
>
> 以下为 **【免责条款】**
> 
> 本仓库发布的项目中涉及的任何脚本，仅用于测试和学习研究，禁止用于商业用途，不能保证其合法性，准确性，完整性和有效性，请根据情况自行判断.
>
> 所有使用者在使用项目的任何部分时，需先遵守法律法规。对于一切使用不当所造成的后果，需自行承担。对任何脚本问题概不负责，包括但不限于由任何脚本错误导致的任何损失或损害.
>
> 如果任何单位或个人认为该项目可能涉嫌侵犯其权利，则应及时通知并提供身份证明，所有权证明，我们将在收到认证文件后删除相关文件.
>
> 任何以任何方式查看此项目的人或直接或间接使用该项目的任何脚本的使用者都应仔细阅读此声明。本人保留随时更改或补充此免责声明的权利。一旦使用并复制了任何相关脚本或本项目的规则，则视为您已接受此免责声明.
>
> 您必须在下载后的24小时内从计算机或手机中完全删除以上内容.
>
> 您使用或者复制了本仓库且本人制作的任何脚本，则视为`已接受`此声明，请仔细阅读

### Bot使用流程

- 【首先】请关注 [频道](https://t.me/agentONE_R) 和 [机器人](https://t.me/radiance_helper_bot)

- 【然后】[安装与配置](https://github.com/semicons/java_oci_manage/blob/main/md/install.md)(可选公网模式和本地无公网模式)

- 【其次】机器人使用/raninfo命令生成随机信息，然后将它填入client_config(执行完一键安装命令后产生)配置文件内，同时将甲骨文云API参数放入配置文件内(也可机器人上传API参数)

- 【最后】bash sh_client_bot.sh 重新启动机器人，可以使用bot了！

> ps:程序自带开启9527端口功能，如仍未开启可手动开启端口，[测试网站](https://port.ping.pe) 可测试端口是否开放
>
> ps:使用本地模式则无需开端口
> 
> ps:脚本支持传参 bash sh_client_bot.sh 8888 更换默认9527端口

### 卸载
```bash
rm -rf gz_client_bot.tar.gz client_config r_client.jar sh_client_bot.sh log_r_client.log debug-*.log
```
如不需要JDK也可卸载：
```bash 
apt remove openjdk*
```

### 说明与帮助
- [已实现功能](https://github.com/semicons/java_oci_manage/blob/main/md/function.md)

- [机器人操作与命令说明](https://github.com/semicons/java_oci_manage/blob/main/md/BOT-README.md)

- [甲骨文云获取API参数与上传(tip：如只刷机创建API文件时可以限制各种操作权限)](https://github.com/semicons/java_oci_manage/blob/main/md/oracle.md)

- [azure获取API参数与上传](https://github.com/semicons/java_oci_manage/blob/main/md/azure.md)

- [常见问题](https://t.me/agentONE_R/41)



### 更新日志
<details>
<summary>查看Releases说明</summary>
 
> 证明该项目仍然存活


</details>
