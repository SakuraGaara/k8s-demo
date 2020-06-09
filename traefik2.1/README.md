### 安装traefik2.1
```sh
kubectl apply -f crd.yaml
kubectl apply -f rbac.yaml
kubectl apply -f depoyment.yaml

kubectl apply -f dashboard.yaml # dashboard中设置http和https，使用https前需拥有证书并创建secret
```
在v2.1版本中，新增功能，可通过`api@internal`访问dashboard 
访问 http://traefik.ngames-dev.cn

### 访问服务
#### demo
demo-appv1v2.yaml 中创建两个deployment进行测试

- 测试1
ingressroute-1.yaml 访问两个服务，测试前后端分离
访问 http://app.ngames-dev.cn 或 http://app.ngames-dev.cn/v1 则为appv1服务
访问 http://app.ngames-dev.cn/v2 则为appv2服务

- 测试2
ingrssroute-2.yaml 设置服务访问权重
访问 http://wrr.ngames-dev.cn 4次则3次会跳appv1,一次为appv2

- 测试3
ingrssroute-3.yaml 流量复制
访问 http://mirror.ngames-dev.cn 流量100%通过appv1,每访问两次，则一次触发appv2 



