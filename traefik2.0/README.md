### k8s版本v1.18.2
k8s安装： ![master的工作流程图](https://ngames-dev.cn/2020/05/21/2020-05-21-kubeadm%E5%AE%89%E8%A3%85/)  

### 安装traefik2.0
```sh
kubectl apply -f traefik-crd.yaml
kubectl apply -f traefik-daemonset.yaml
```

### demo测试
- 不使用https
```sh
kubectl apply -f demo-nginx.yaml
```

- 使用https
```sh
kubectl create secret tls ali-tls --cert=/ssl/ngames-dev.pem --key=/ssl/ngames-dev.key #证书自己创建
```
开启demo-nginx.yaml中https,redirect-https和middlewares的配置后：
```sh
kubectl apply -f demo-nginx.yaml
```