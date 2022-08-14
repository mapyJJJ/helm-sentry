#### 安装

部署安装sentry

集群需要先添加一个nfs类型的 storageclass 名为 `nfsclass`

```bash
kubectl create namesapce sentry

# 拉取repo ，在录目中执行安装

helm install --wait --name sentry -f sentry/values.yaml --namespace sentry sentry/
```

init-db job 有点慢 ，等所有pod起来 ，以及job成功执行后代表成功部署了


#### 访问

```
kubectl get service sentry -n sentry  # 查看nodeport，直接访问该地址


kubectl get secret sentry -n sentry -o jsonpath='{.data}' # 其中的user-password 是sentry admin密码 

用户名为： admin@sentry.local
```
