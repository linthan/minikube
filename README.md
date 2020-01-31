## 目的

快速搭建一个 minikube 的环境

## 实验环境

Ubuntu 18.04

## 步骤

- 安装 ansible

```bash
pip install ansible
```

- 安装角色依赖

```bash
ansible-galaxy install andrewrothstein.kubectl
```

- 创建 inventory 修改成自己需要的目标机器

```
mv hosts.example hosts
```

- 安装 docker 和 minikube
  请将 registry-mirrors":["https://xxx.mirror.aliyuncs.com"] 换成自己的阿里云 docker 镜像加速

```
ansible-playbook -i hosts playbook.yml
```

## 启动 minikube

### 第一种方式

```
minikube delete && minikube start --cpus=2 --memory=4096 --disk-size=10g \
	--registry-mirror=https://registry.docker-cn.com  --vm-driver=none
```

### 第二种方式

```
minikube start --image-mirror-country cn \
    --iso-url=https://kubernetes.oss-cn-hangzhou.aliyuncs.com/minikube/iso/minikube-v1.6.0.iso \
    --registry-mirror=https://xxxx.mirror.aliyuncs.com \
    --vm-driver=virtualbox
```

### 可以参考下面一个博客

- 个人博客 https://www.inlighting.org/2020/install-minikube-in-china.html
- 官方安装方法 https://yq.aliyun.com/articles/221687
