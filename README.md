# 在k8s里部署etcd集群，按顺序启动：
1. kubectl apply -f storageClass.yaml
    - 动态pv使用的是ali的nas服务，创建时记得填写server地址， ali的存储方式有两种，这种是csi方式，如果是Flexvolume需要查阅相关技术文档：
    - https://help.aliyun.com/document_detail/157025.html
2. kubectl apply -f service-etcd.yaml
    - statefulset模式依赖service，必须先启动service
3. kubectl apply -f statefulset-etcd.yaml
    - 部署etcd， yaml内的启动命令会先检查集群状态，并添加节点.最小集群数为3个.
#部署consul集群，server and client：
1. 启动service-consul-server.yaml
2. 启动service-consul-client.yaml
3. 启动statefulset-consul-server.yaml
4. 启动daemonset-consul-client.yaml
