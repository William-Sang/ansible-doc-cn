# Intro to Playbooks
# Playbooks 简介

## About Playbooks
## 关于 Playbooks

Playbooks are a completely different way to use ansible than in adhoc task execution mode, and are particularly powerful.

Playbooks 是一种和adhoc任务完全不同的使用ansible的方式，非常强大。

Simply put, playbooks are the basis for a really simple configuration management and multi-machine deployment system, unlike any that already exist, and one that is very well suited to deploying complex applications.

简单来说，playbooks 相对于其他已存在的适合部署复杂应用的管理工具而言，更加适合简单的配置管理和多机器部署系统。

Playbooks can declare configurations, but they can also orchestrate steps of any manual ordered process, even as different steps must bounce back and forth between sets of machines in particular orders. They can launch tasks synchronously or asynchronously.

Playbooks 可以声明配置，也可以编排任何人工组织的流程，甚至一些在一系列机器之间以特定顺序来回反复执行的步骤。Playbooks可以以同步或者异步的方式启动任务(tasks)。

While you might run the main /usr/bin/ansible program for ad-hoc tasks, playbooks are more likely to be kept in source control and used to push out your configuration or assure the configurations of your remote systems are in spec.

你可以是使用/usr/bin/ansible程序运行临时任务(ad-hoc tasks)，然而 playbooks 更加适合放在版本控制系统下，用于推送配置或者固定远程服务器指定位置的配置文件。

There are also some full sets of playbooks illustrating a lot of these techniques in the ansible-examples repository. We’d recommend looking at these in another tab as you go along.

推荐你查看 ansible-example 中的例子，它们很好的解释了这些技术细节。

There are also many jumping off points after you learn playbooks, so hop back to the documentation index after you’re done with this section.

学习 playbooks 后有很多跳转页，所以学习完这一小节后可以翻到文档索引。

# Playbook Language Example
# Playbook 示例

Playbooks are expressed in YAML format (see YAML Syntax) and have a minimum of syntax, which intentionally tries to not be a programming language or script, but rather a model of a configuration or a process.

Playbooks 以YAML格式来表达，有最少的语法，尽量不成为一个编程语言或者脚本，而是配置或者过程模型。

Each playbook is composed of one or more ‘plays’ in a list.

每一个 playbook 都由一组 "plays" 组成。

The goal of a play is to map a group of hosts to some well defined roles, represented by things ansible calls tasks. At a basic level, a task is nothing more than a call to an ansible module, which you should have learned about in earlier chapters.

一个 play 的目标就是映射一组机器(hosts)到一些定义好的角色(roles)上，ansible上称之为tasks。基础使用层次上，一个task就是对某个ansible模块的调用。

By composing a playbook of multiple ‘plays’, it is possible to orchestrate multi-machine deployments, running certain steps on all machines in the webservers group, then certain steps on the database server group, then more commands back on the webservers group, etc.

通过组织多个palys，可以编排多机器部署，在web服务器组和database服务器组分别运行不同的步骤。

“plays” are more or less a sports analogy. You can have quite a lot of plays that affect your systems to do different things. It’s not as if you were just defining one particular state or model, and you can run different plays at different times.

palys 或多或少类似体育运动。你可以定义很多 play 来影响你的系统去做很多事情。而不像定义一个特定系统或者模型。你可以在不同时间运行不同plays。

For starters, here’s a playbook that contains just one play:

接下来我们来看一个只包含一个play的playbook:


```

---
- hosts: webservers
  vars:
    http_port: 80
    max_clients: 200
  remote_user: root
  tasks:
  - name: ensure apache is at the latest version
    yum: pkg=httpd state=latest
  - name: write the apache config file
    template: src=/srv/httpd.j2 dest=/etc/httpd.conf
    notify:
    - restart apache
  - name: ensure apache is running
    service: name=httpd state=started
  handlers:
    - name: restart apache
      service: name=httpd state=restarted
```

Below, we’ll break down what the various features of the playbook language are.

接下来我们会逐个拆开来讲解 playbook 语言的不同特性。

## Basics
## 基础

###  Hosts and Users
### 主机和用户

For each play in a playbook, you get to choose which machines in your infrastructure to target and what remote user to complete the steps (called tasks) as.

Playbook中的每一个play，你都需要选择特定的某些机器作为运行目标，特定的用户来执行这些步骤。

The hosts line is a list of one or more groups or host patterns, separated by colons, as described in the Patterns documentation. The remote_user is just the name of the user account:

hosts 行是主机组或者主机模式列表，以逗号分割。 remote_user 定义执行用户名。

```

---
- hosts: webservers
  remote_user: root
```
