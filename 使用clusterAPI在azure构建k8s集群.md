1.Cluster API

Kubernetes Cluster API(https://cluster-api.sigs.k8s.io/) :它提供声明式 API 和工具来简化配置、升级和管理多个 Kubernetes 集群。

我们会先创建一个管理其他集群生命周期的 Kubernetes 集群，在这个集群上，我们将安装 Cluster API。

然后我们就可以通过创建 Cluster API 对象来定义新的工作负载集群

Cluster API 提供了一组扩展 Kubernetes API 的 CRD，它们中的每一个都代表 Kubernetes 集群安装的定制，这里不会详细介绍它，

如果你对此感兴趣，可以在其官方文档 https://cluster-api.sigs.k8s.io/user/concepts.html 了解更多信息。

对我们来说重要的是，它提供了一个 CLI 工具来处理 Cluster API 管理集群的生命周期。此外，它还允许在包括 AWS、GCP 或 Azure 在内的多个基础设施上创建集群.


***在这个搭建过程中使用的是K3S，参看K3S的安装***


2. 安装 Clusterctl

```bash
$ curl -L https://github.com/kubernetes-sigs/cluster-api/releases/download/v0.3.12/clusterctl-linux-amd64 -o clusterctl

$ chmod +x ./clusterctl

$ sudo mv ./clusterctl /usr/local/bin/clusterctl

$ clusterctl version

Initialize the management cluster

$ sudo clusterctl init –infrastructure docker
```

3. 初始化集群安装（设置各种参数，节点数，vmsize等，适用于azure平台）

 clusterctl init --infrastructure azure
 
 一旦我们成功初始化了一个管理集群，我们就可以对其进行验证，Cluster API 会创建五个新的命名空间。
 
 <img width="490" alt="Screen Shot 2023-02-02 at 5 10 01 PM" src="https://user-images.githubusercontent.com/7360524/216280675-e48fb512-2e3d-4eba-b028-7c623349b95f.png">

 可以显示已安装 CRD 的列表，现在 Kubernetes Cluster API 正在管理集群上运行了，我们可以继续执行进一步的步骤。
 
 <img width="707" alt="Screen Shot 2023-02-02 at 5 11 02 PM" src="https://user-images.githubusercontent.com/7360524/216280951-9893ca9a-3d66-4022-8246-d7a610dcaf1b.png">

4. 创建集群

clusterctl 命令行工具生成带有新 Kubernetes 集群声明的 YAML 资源清单，直接执行如下所示的命令即可，

它将生成清单并将其保存到 c1-clusterapi.yaml 文件中

<img width="608" alt="Screen Shot 2023-02-02 at 5 13 32 PM" src="https://user-images.githubusercontent.com/7360524/216281564-09621d9d-69d5-4226-9a25-737200b45bdd.png">



