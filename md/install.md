# 安装与配置

[English](./en/install.md)

---

## 1. 一键安装 / 更新

```bash
wget -O sh_client_bot.sh https://github.com/semicons/java_oci_manage/releases/latest/download/sh_client_bot.sh && chmod +x sh_client_bot.sh && bash sh_client_bot.sh
```

> 建议先创建目录：`mkdir rbot && cd rbot`

---

## 2. 配置参数

安装后会生成 `client_config` 配置文件，按以下说明编辑。

### 用户凭据（必填）

在 [Telegram 机器人](https://t.me/radiance_helper_bot) 中使用 `/raninfo` 命令生成凭据。

```ini
username=你的用户名
password=你的密码
```

> 请妥善保存凭据。如果 Telegram 账号被封，可以凭此信息重新绑定。

### Oracle Cloud (OCI) 配置

在 `oci=begin` 和 `oci=end` 之间放入 API 配置信息，支持多个 Profile。

```ini
oci=begin

[DEFAULT]
user=ocid1.user.oc1..aaaaaaaaxxxxgwlg3xuzwgsaazxtzbozqq
fingerprint=b8:33:6f:xxxx:45:43:33
tenancy=ocid1.tenancy.oc1..aaaaaaaaxxx7x7h4ya
region=ap-singapore-1
key_file=/root/rbot/xxx.pem

[tokyo]
user=ocid1.user.oc1..aaaaaaaaxxxxgwlg3xuzwgsaazxtzbozqq
fingerprint=b8:33:6f:xxxx:45:43:33
tenancy=ocid1.tenancy.oc1..aaaaaaaaxxx7x7h4ya
region=ap-tokyo-1
key_file=/root/rbot/xxx.pem

oci=end
```

> `key_file` 是服务器上的私钥文件路径。私钥在甲骨文控制台添加 API 密钥时生成下载。详见 → [甲骨文云 API 配置](./oracle.md)

### Azure 配置

在 `azure=begin` 和 `azure=end` 之间放入 API 配置信息，支持多个 Profile。

```ini
azure=begin

[az001]
appId=551xxxx7-xxxx-xxxx-xxxx-b9xxxx60cc65
password=T618Q~.LIy_xxxxx~jm~xxxxxx
tenant=xxxx3713-xxxx-4cb5-xxxx-3001060xxxxx

azure=end
```

> 也可通过机器人 `/oci` 命令上传原始 JSON 格式。详见 → [Azure API 配置](./azure.md)

### SSH 连接配置

在 `ssh=begin` 和 `ssh=end` 之间维护 SSH 连接信息。格式：`ssh_IP=用户名:密码或密钥路径`

```ini
ssh=begin

ssh_192.168.1.10=root:MyPassword123
ssh_129.1.100.55=ubuntu:/root/.ssh/oci_key

ssh=end
```

> 此配置用于 Telegram 机器人的远程命令执行。Web SSH 终端的连接在浏览器界面中管理，无需在此配置。

### SolusVM 配置

在 `solusvm=begin` 和 `solusvm=end` 之间维护 SolusVM 面板配置。

```ini
solusvm=begin

[racknerd-1]
api=https://nerdvm.racknerd.com/api/client/command.php
key=你的API_Key
hash=你的API_Hash

solusvm=end
```

### Cloudflare 配置（可选）

```ini
cf_email=你的Cloudflare邮箱
cf_account_key=你的Global_API_Key
```

> Cloudflare Key 获取路径：我的个人资料 → API 令牌 → API 密钥 → Global API Key

### 网络配置（可选）

```ini
# 本机地址（留空则自动获取，使用默认端口 9527）
local_address=https://xxx.xx:9527

# URL 名称（默认为 address，可在 bot 上修改）
local_url_name=

# 启动模式（填 local 为无公网 IP 模式；留空或填其他为端口模式）
model=
```

---

## 3. 常用命令

| 命令 | 说明 |
|------|------|
| `bash sh_client_bot.sh` | 启动 / 重启（守护进程） |
| `bash sh_client_bot.sh 8888` | 指定端口启动 |
| `bash sh_client_bot.sh status` | 查看运行状态 |
| `bash sh_client_bot.sh log` | 查看日志（Ctrl+C 退出） |
| `bash sh_client_bot.sh stop` | 停止客户端 |
| `bash sh_client_bot.sh restart` | 重启客户端 |
| `bash sh_client_bot.sh upgrade` | 升级到最新版本 |
| `bash sh_client_bot.sh uninstall` | 卸载 |

---

## 4. 访问 Web 界面

启动后通过浏览器访问：

```
https://你的IP:9527
```

- 使用 `username` / `password` 登录，或使用 Telegram 验证码登录
- 默认端口 `9527`，可通过启动参数修改
- 确保端口已开放 — 使用 [端口测试工具](https://port.ping.pe) 检查
- 本地模式（`model=local`）无需开端口，仅通过 Telegram 机器人操作

---

## 5. 支持的架构

| 架构 | 下载包 |
|------|--------|
| Linux x86_64（AVX2） | `gz_client_bot_x86.tar.gz` |
| Linux x86_64（兼容） | `gz_client_bot_x86_compatible.tar.gz` |
| Linux ARM64 | `gz_client_bot_aarch.tar.gz` |
| macOS ARM64（Apple Silicon） | `gz_client_bot_mac_aarch.tar.gz` |

> 启动脚本会自动检测架构并下载对应版本，无需手动选择。
