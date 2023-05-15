## 引言
为了方便广大国内开发者体验最新的 AI 能力，天空工作室搭建了一个AI平台, 包裹AI聊天, AI应用, AI绘画等。（[立即体验](https://aifuntk.com)）

&nbsp;

## 启动
首先需要安装docker, 然后在项目根目录执行以下命令

开启服务
```shell
cd docker-compose
docker compose up -d
```

停止服务
```shell
cd docker-compose
docker compose down
```

&nbsp;

## 运行地址
管理平台: http://你的IP:8080/admin/  
帐号: admin  
密码: 123456

H5前台: http://你的IP:8080/h5/

&nbsp;

## 注意事项
启动后, 需要填入你自己的API KEY, 填入位置
```
模型管理->KEY管理
```

&nbsp;

## 关于本程序

本程序仅是编译好的Docker镜像, 如需要源码请联系微信 Ke-Carrey～ 

&nbsp;

## Docker安装方法
CentOS / Debian / Ubuntu 服务器执行以下命令
```shell
curl -fsSL https://get.docker.com | sh
```

Windows 服务器请自行搜索安装 Docker Desktop

&nbsp;

## Nginx配置

```nginx
location ~ ^/(app|h5|admin|public|static)/ {
    proxy_pass http://localhost:8080;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header REMOTE-HOST $remote_addr;
    
    proxy_read_timeout 300;
    proxy_connect_timeout 300;
    proxy_send_timeout 300;
}
```
