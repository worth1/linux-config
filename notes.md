# Linux 学习笔记 & 踩坑记录

## 一、常用命令速查

### 系统信息
```bash
# 查看系统版本
cat /etc/os-release
lsb_release -a

# 查看内核版本
uname -r

# 查看CPU/内存使用
top
htop
free -h

### 文件与目录
# 查看文件大小
du -sh ./*

# 查找文件
find / -name "*.log" 2>/dev/null

# 批量解压zip
for file in *.zip; do unzip $file; done

### 网络相关
# 查看端口占用
netstat -tulnp | grep 8080
ss -tulnp | grep 8080

# 测试端口连通性
telnet 192.168.1.1 22
nc -zv 192.168.1.1 22

## 二、环境配置记录
###1. SSH 免密登录配置
# 生成本地密钥
ssh-keygen -t ed25519 -C "your_email@example.com"

# 上传公钥到服务器
ssh-copy-id user@server-ip

# 配置 ~/.ssh/config
Host my-server
  HostName 192.168.1.100
  User root
  IdentityFile ~/.ssh/id_ed25519

###2. Git 全局配置
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
git config --global core.editor vim
