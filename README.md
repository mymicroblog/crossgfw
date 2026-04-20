# 正确上网最佳实践 (Best Practice for Cross-GFW)

[English](README_EN.md) | 中文

本项目旨在提供一种稳定、安全且易于维护的科学上网方案，特别针对程序员及需要访问 AI 工具（如 ChatGPT）的用户。

## 为什么选择本方案？

| 特性 | 本方案 (GOST + HTTPS) | 常见 VPN / 机场 | 自建 V2Ray (复杂版) |
| :--- | :--- | :--- | :--- |
| **稳定性** | 极高 (TLS 伪装) | 易被封禁 | 高 |
| **易用性** | 脚本一键安装 | 简单但质量参差不齐 | 复杂 (需配置 Nginx/TLS) |
| **安全性** | 强 (HTTPS 隧道) | 中 (取决于服务商) | 强 |
| **AI 支持** | 支持 (配合 Warp) | 经常被 OpenAI 屏蔽 | 支持 |

---

## 快速开始

### 1. 准备工作
- **域名**: 购买一个海外域名 (如 `Namecheap`, `GoDaddy`, `Cloudflare`)。
- **VPS**: 推荐海外 VPS 提供商：
  - **AWS**: 新用户免费一年。
  - **Linode / DigitalOcean**: 稳定可靠。
  - ⚠️ **警告**: 请勿使用阿里云、腾讯云等国内厂商的海外节点。

### 2. 服务端搭建
建议使用 **Ubuntu 20.04+**。

1. **基础环境**:
   ```bash
   apt-get update && apt-get install -y wget curl nginx
   systemctl start nginx
   ```
2. **一键安装脚本**:
   执行 [haoel 的安装脚本](https://github.com/haoel/haoel.github.io/blob/master/scripts/install.ubuntu.18.04.sh) 并按指引操作。
   > **关键步骤**: 脚本运行中会要求输入域名以申请 SSL 证书（需确保 80 端口已开放并由 Nginx 响应）。
3. **功能选择**:
   安装过程中，仅建议选择以下项：
   - `1` (TCP BBR 优化)
   - `2` (Docker 服务)
   - `3` (创建 SSL 证书)
   - `4` (安装 GOST HTTP/2 代理)
   - `8` (证书更新 CronJob)

### 3. 防护与优化 (进阶)
- **防止 IP 被封**: 将域名托管至 **Cloudflare**，开启 `Proxied` (小黄云)，SSL/TLS 选择 `Full`。
- **访问 OpenAI / Netflix**: 使用 **Cloudflare Warp** 获取原生 IP 支撑。

---

## 客户端配置

- **macOS**: [GOST](https://github.com/ginuerzh/gost/releases) + [ShadowsocksX-NG](https://github.com/shadowsocks/ShadowsocksX-NG/releases)
- **iOS**: [Shadowrocket](https://apps.apple.com/us/app/shadowrocket/id932747118) (需美区账号)
- **Android**: [Shadowsocks + GOST Plugin](https://github.com/xausky/ShadowsocksGostPlugin)

---

## 协议
本项目采用 [MIT License](LICENSE)。
