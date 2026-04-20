# Best Practice for Cross-GFW

English | [中文](README.md)

This project provides a stable, secure, and easy-to-maintain solution for bypassing internet censorship, specifically designed for developers and users who need reliable access to AI tools like ChatGPT.

## Why Choose This Solution?

| Feature | This Solution (GOST + HTTPS) | Typical VPNs | Manual V2Ray (Complex) |
| :--- | :--- | :--- | :--- |
| **Stability** | Excellent (TLS obfuscation) | Easy to block | High |
| **Ease of Use** | One-click script | Simple but unreliable | Complex (Nginx/TLS setup) |
| **Security** | Strong (HTTPS tunnel) | Medium (Provider-dependent) | Strong |
| **AI Support** | Yes (via Warp) | Often blocked by OpenAI | Yes |

---

## Quick Start

### 1. Prerequisites
- **Domain**: Purchase a non-Chinese domain (e.g., `Namecheap`, `GoDaddy`, `Cloudflare`).
- **VPS**: Recommended overseas VPS providers:
  - **AWS**: One year free for new users.
  - **Linode / DigitalOcean**: Reliable and stable.
  - ⚠️ **Warning**: Do NOT use overseas nodes from Chinese providers like Alibaba Cloud or Tencent Cloud.

### 2. Server Setup
Recommended OS: **Ubuntu 20.04+**.

1. **Environment**:
   ```bash
   apt-get update && apt-get install -y wget curl nginx
   systemctl start nginx
   ```
2. **One-Click Script**:
   Execute [haoel's installation script](https://github.com/haoel/haoel.github.io/blob/master/scripts/install.ubuntu.18.04.sh) and follow the prompts.
   > **Key Step**: The script will ask for your domain to apply for an SSL certificate (ensure port 80 is open and handled by Nginx).
3. **Feature Selection**:
   During installation, only select the following:
   - `1` (TCP BBR optimization)
   - `2` (Docker service)
   - `3` (Create SSL certificate)
   - `4` (Install GOST HTTP/2 proxy)
   - `8` (Certificate update CronJob)

### 3. Protection & Optimization (Advanced)
- **Prevent IP Blocking**: Host your domain on **Cloudflare**, enable `Proxied`, and set SSL/TLS to `Full`.
- **OpenAI / Netflix Access**: Use **Cloudflare Warp** to obtain a native IP.

---

## Client Configuration

- **macOS**: [GOST](https://github.com/ginuerzh/gost/releases) + [ShadowsocksX-NG](https://github.com/shadowsocks/ShadowsocksX-NG/releases)
- **iOS**: [Shadowrocket](https://apps.apple.com/us/app/shadowrocket/id932747118) (Requires US App Store account)
- **Android**: [Shadowsocks + GOST Plugin](https://github.com/xausky/ShadowsocksGostPlugin)

---

## License
This project is licensed under the [MIT License](LICENSE).
