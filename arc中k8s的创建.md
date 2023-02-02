在azure ARM 和 terraform脚本中都没有定义k8s对应的资源信息。

其中缘由是因为，它通过k3s 为management cluster，利用cluster API的方式，创建了对应CAPI kubernetes cluster。

[k3s安装](./k3s安装.md) 

[使用clusterAPI在azure构建k8s集群](./使用clusterAPI在azure构建k8s集群.md) 


安装之后，遇到k8s无法注册到azure 上的问题。

https://github.com/microsoft/azure_arc/issues/1633
ArcBox : the kubernetes cluster of ArcBox-CAPI-Data can not be registered to Azure as a connectedClusters #1633

不管换region还是替换部署方式为terraform都不行。

teams找到Lior Kamrat，他查看了参数，认为是bastonDeploy这个参数为null，而不是true，false导致的。

重新再来一次，确实可以了，看到那个参数为false。 很费解，按理terraform是可以的，如果按照他说的。

不管怎么样，最后可以了。

现在logicApp部署也没有成功，需要继续排查。
