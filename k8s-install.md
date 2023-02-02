1.k3s（~60MB 二进制文件）

生产 k8s 安装的大小和复杂性各不相同，但上游 k8s 有大量组件和移动部件（etcd、kube-apiserver、kube-scheduler、kubelet、DNS 等）。

可以想象，正确设置很复杂，尤其是在资源有限或单节点集群上。出于必要，

现在有很多轻量级的 k8s 发行版，它们不仅去掉了大多数人不会使用的功能，而且还简化了安装和设置。这里对一些轻量级的 k8s 发行版进行了很好的比较。

    1). k0s（由拥有 Docker, Inc. 的 Mirantis 制作）

    2). MicroK8s（由 Canonical 制造，也制造 Ubuntu）

    3). K3s（由 Rancher 制造，最近被 SUSE 收购）

    4). minikube（“官方”mini-k8s 发行版）

K3s 是因为它似乎拥有最大的社区，它通过了 CNCF 认证，而且它是轻量级的（~60MB 二进制文件）。


2. k3s 安装

  1). curl -sfL https://get.k3s.io | sh -
  
  2). sudo systemctl status k3s.service
  
  3). sudo kubectl cluster-info
  
  4). 查看或者拷贝连接文件： sudo cat /etc/rancher/k3s/k3s.yaml
  
替换API-server的IP地址就可以，在网络联通的客户端访问和使用这个集群了。



