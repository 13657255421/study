## Docker

#####Docker 是什么

+ Build,ship and Run Any App, Anywhere - 一次封装，到处执行
+ 基于Linux的高效、敏捷、轻量级的容器（轻量虚拟）方案。

> 虚拟技术
>
> + 完全虚拟化 VMware Workstation， VirtualBox
> + 硬件辅助虚拟化 InterVT AMD-V
> + 超虚拟化 Xen
> + 操作系统计 Docker LXC 容器



######部署一个典型的前后端分离系统

+ 前端工程化  - Taro

+ 后端 - NodeJs

+ 数据库 MongoDB

+ Nginx

  + 静态服务
  + 反向代理

  ```
  #https://github.com/su37josephxia/docker_ci
  git clone git@github.com:su37josephxia/docker_ci.git
  docker-compose up
  ```



###### 特点

+ 高效的利用系统资源
+ 快速的启动时间
+ 一致的运行环境
+ 持续交付和部署
+ 更轻松的迁移



###### 对比传统虚拟机总结

| 特性       | 容器               | 虚拟机     |
| ---------- | ------------------ | ---------- |
| 启动       | 秒级               | 分钟级     |
| 硬盘使用   | 一般为 MB          | 一般为 GB  |
| 性能       | 接近原生           | 弱于       |
| 系统支持量 | 单机支持上千个容器 | 一般几十个 |

##### Docker 安装

###### 申请阿里云主机

+ Ubuntu 18.04 64位



```
# apt 升级
sudo apt-get update
# 添加相关软件包
sudo apt-get install \
		apt-transport-https \
		ca-certificates \
		curl \
		software-properties-common
		
		
# 下载软件包的合法性，需要添加软件源的 GPG 密钥
curl -fsSL https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu/gpg | sudo apt-key add -

# source.list 中添加 Docker 软件源
sudo add-apt-repository \
		"deb [arch=amd 64] https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu \
		$(lsb_release -cs) \
		stable"
		
# 安装 Docker CE
sudo apt-get update
sudo apt-get install docker-ce

# 脚本自动安装（不需要）
curl -fsSL get.docker.com -o get-docker.sh
sudo sh get-docker.sh --mirror Aliyun

# 启动 Docker CE
sudo systemctl enable docker
sudo systemctl start docker

# 建立 docker 用户组 （附加）
sudo groupadd docker
sudo usermod -aG docker $USER

# Helloworld 测试
docker run hello-world
```



###### 镜像加速

+ [Azure 中国镜像 `https://dockerhub.azk8s.cn`](https://github.com/Azure/container-service-for-azure-china/blob/master/aks/README.md#22-container-registry-proxy)
+ 阿里云加速器（需登录账号获取）
+ 七牛云加速器 https://reg-mirror.qiniu.com