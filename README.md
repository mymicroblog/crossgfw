# 正确上网最佳实践


### 为啥有这篇文章
目前依然很多人，包括程序员不会科学上网

购买的vpn容易被封，不够稳定

vps上的vpn被chatgpt封掉，无法使用最新的ai产品

### 购买海外vps
aws, 注册后新用户免费试用一年

Linode

digitalocean

**不要买阿里云等国内的vps，原因你懂的**

### 搭建服务
调研了各种方式,耗子叔的文章介绍的很好，<https://github.com/haoel/haoel.github.io>，我们选择了docker gost+https方式

#### 选择ubuntu系统，我选的版本是ubuntu20

gost+https服务比较简单，而且隐蔽性较强
#### 安装常用工具包
修改时区为东八区 
升级系统最新包apt-get update
安装常用工具 apt-get install wget curl 等

#### 在ubuntu上一键安装gost+https

##### 购买一个国外域名(www.namecheap.com、name.com、www.godaddy.com、cloudflare.com), 并配置解析到你的vps服务器

##### 执行脚本按指引安装<https://github.com/haoel/haoel.github.io/blob/master/scripts/install.ubuntu.18.04.sh>

有如下步骤:

其中第3、4步需要输入你的刚注册的域名生成ssl证书，而证书申请需要访问80端口网站，
所以在这里需要先安装nginx, apt-get install nginx 安装后执行nginx启动,使用nginx的默认配置即可

1) 安装 TCP BBR 拥塞控制算法，自动修改内核参数
2) 安装 Docker 服务程序
3) 创建 SSL 证书，
4) 安装 Gost HTTP/2 代理服务，安装完自动启动，netsat -ntlp，查看端口和服务是否安装ok
5) ~~安装 ShadowSocks 代理服务~~
6) ~~安装 VPN/L2TP 服务~~
7) ~~安装 Brook 代理服务~~
8) 创建证书更新 CronJob
我们只选择1/2/3/4/8,第四部需要输入域名、端口（避开nginx的443）gost认证的账号、密码


### 防止vps被封禁
Cloudflare 是一个 CDN 服务商，目前国内依然能正常的访问，可以作为跳板来实现翻墙。
注册 Cloudflare 帐号，并有一个空闲域名（三级域名即可），交给 Cloudflare 托管并将域名指向被封的 VPS IP，注意开启 Proxied 并且 SSL-TLS 使用 Flexible 选项。
域名套上cloudflare，防止真实ip被抓到

### 访问openai、奈飞等
Cloudflare Warp 原生 IP

### 各种客户端
mac OS, gost<https://github.com/ginuerzh/gost/releases>,注意区分arm和amd+ ShadowSocks client

iOS, ShadowRocket(美区账号付费，可以淘宝苹果gift card)

Android <https://github.com/xausky/ShadowsocksGostPlugin>
