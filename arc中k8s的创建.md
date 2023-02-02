在azure ARM 和 terraform脚本中都没有定义k8s对应的资源信息。

其中缘由是因为，它通过k3s 为management cluster，利用cluster API的方式，创建了对应CAPI kubernetes cluster。

[k3s安装](./k3s安装.md) 

[使用clusterAPI在azure构建k8s集群](./使用clusterAPI在azure构建k8s集群.md) 
