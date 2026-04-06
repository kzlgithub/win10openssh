OpenSSH下载地址：https://github.com/PowerShell/Win32-OpenSSH/releases/download/10.0.0.0p2-Preview/OpenSSH-Win64.zip
<br>
OpenSSH发布地址：https://github.com/powershell/win32-openssh/releases

### 下载解压到C:\Program Files，名称改为OpenSSH。用powershell打开(不要用cmd)
```
cd "C:\Program Files\OpenSSH"
```

### 执行安装命令
```
.\install-sshd.ps1
```

### 启动SSH服务
```
Start-Service sshd
```

### 设置开机启动
```
Set-Service -Name sshd -StartupType 'Automatic'
```

### 验证服务是否正在运行 (Status 应该是 Running)
```
Get-Service sshd
```

### 开启22端口
```
New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
```

### 登录
ssh -p 端口 用户名@ip
<br>
ssh 用户名@ip
