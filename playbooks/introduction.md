# Intro to Playbooks
# Playbooks 简介

About Playbooks
Playbooks are a completely different way to use ansible than in adhoc task execution mode, and are particularly powerful.

Playbooks 是一种和adhoc任务完全不同的使用ansible的方式，非常强大。

Simply put, playbooks are the basis for a really simple configuration management and multi-machine deployment system, unlike any that already exist, and one that is very well suited to deploying complex applications.

简单来说，playbooks 相对于其他已存在的适合部署复杂应用的管理工具而言，更加适合简单的配置管理和多及其部署系统。

Playbooks can declare configurations, but they can also orchestrate steps of any manual ordered process, even as different steps must bounce back and forth between sets of machines in particular orders. They can launch tasks synchronously or asynchronously.

Playbooks 可以声明配置，也可以编排任何人工组织的流程，甚至一些在一系列机器之间以特定顺序来回反复执行的步骤。Playbooks可以以同步或者异步的方式启动任务(tasks)。

While you might run the main /usr/bin/ansible program for ad-hoc tasks, playbooks are more likely to be kept in source control and used to push out your configuration or assure the configurations of your remote systems are in spec.

你可以是使用/usr/bin/ansible程序运行临时任务(ad-hoc tasks)，然而 playbooks 更加适合放在版本控制系统下，用于推送配置或者固定远程服务器指定位置的配置文件。

There are also some full sets of playbooks illustrating a lot of these techniques in the ansible-examples repository. We’d recommend looking at these in another tab as you go along.

推荐你查看 ansible-example 中的例子，它们很好的解释了这些技术细节。

There are also many jumping off points after you learn playbooks, so hop back to the documentation index after you’re done with this section.

学习 playbooks 后有很多跳转页，所以学习完这一小节后可以翻到文档索引。
