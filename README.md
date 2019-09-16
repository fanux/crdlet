# crdlet
一个比kubelet kube-proxy更高抽象度的agent

如果需要在node节点上起虚拟机怎么办？ kubelet kube-proxy都是特殊的agent，比较专用。

用户可以通过controller去控制自己CRD，但是却没有一个执行器去真正执行和处理CRD，这就需要crdlet，负责在node节点上监听CRD并执行bind到自己节点上的CRD相关的动作。

以虚拟机为例，假设用户创建一个VM（自定义CRD） 调度器调度到了某个节点上（controller bind到某个节点） 该节点上的crdlet就监听到这个事件，并在该机器上调用libvirt启动虚拟机 配置网络等
