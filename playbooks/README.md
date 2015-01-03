# Playbooks

Playbooks are Ansible’s configuration, deployment, and orchestration language. They can describe a policy you want your remote systems to enforce, or a set of steps in a general IT process.

Playbooks 是Ansible的配置、部署和编排语言。它能按照你的要求描述远程服务器需要执行的规则，或者在一般IT过程中的执行步骤。

If Ansible modules are the tools in your workshop, playbooks are your design plans.

如果我们吧Ansible模块比作车间里的工具，那么playbooks就是你的设计方案。

At a basic level, playbooks can be used to manage configurations of and deployments to remote machines. At a more advanced level, they can sequence multi-tier rollouts involving rolling updates, and can delegate actions to other hosts, interacting with monitoring servers and load balancers along the way.

Playbooks简单层次使用，可以被用于管理远程服务器的配置和部署。对于更高级的用法，playbooks可以序列化多层次任务，包括：滚动更新、代理其他主机和与监控服务器、负载均衡器交互。

While there’s a lot of information here, there’s no need to learn everything at once. You can start small and pick up more features over time as you need them.

文档中有很多信息，不需要一下子全部学会。你只需要学习少部分，剩余特性在需要的时候再学习。

Playbooks are designed to be human-readable and are developed in a basic text language. There are multiple ways to organize playbooks and the files they include, and we’ll offer up some suggestions on that and making the most out of Ansible.

Playbooks 被设计成易读的文本格式。组织playbooks和其包含的文件有很多种方式，我们也会对此提供一些建议来尽可能充分使用Ansible。

It is recommended to look at Example Playbooks while reading along with the playbook documentation. These illustrate best practices as well as how to put many of the various concepts together.

推荐在阅读playbook文档的同时，看一些示例。这些示例在演示最佳实战的同时，也展示了如何同时使用多种概念。


#### 更新日期: 2015年01月04日
