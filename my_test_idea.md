# my test idea



## 有没有ceph相关的repo

没有

## 是否强依赖于云原生

不依赖

## 和商业化版本区别

https://help.aliyun.com/zh/ahas/user-guide/comparison-between-open-source-chaosblade-and-commercial-ahas-chaos

## ChaosBlade是否需要在所有的测试机器上部署执行器？以方便在测试机器上模拟故障

ChaosBlade 的工作原理是在控制节点（或称为管理节点）上发出故障注入命令，然后这些命令会被发送到目标测试机器上执行。为了能够在目标机器上执行故障注入，ChaosBlade 需要在这些机器上部署一个执行器（Executor）。


## 管理节点是否需要目标机器上有ssh免密登录的权限？

ChaosBlade 通常需要管理节点对目标机器具有 SSH 免密登录的权限。这是因为 ChaosBlade 的工作流程涉及到从管理节点远程连接到目标机器，并在目标机器上部署和启动 Executor（执行器）来执行故障注入命令。


## 如果我的执行器已经在目标机器部署好了，是否还需要管理节点到目标机器的ssh免密登录权限

如果执行器已经在目标机器上部署好了，并且能够正常运行，那么 ChaosBlade CLI 与目标机器的 Executor 之间的通信通常就不再依赖于 SSH 免密登录。


## chaosblade是否支持配置文件的方式配置故障规则

支持。

target: disk
action: fill
scope: /home
matchers:
  - name: path
    value: /home
    type: string
  - name: size
    value: "50000"
    type: int

./blade create -f chaosblade-config.yaml


## 比如每10秒杀一次进程

expName: kill-process-example
expDescription: 每10秒终止一次特定名称的进程
targets:
  - target: process
    action: kill
    matchers:
      - name: process_name
        value: "your_process_name"
        type: "string"
      - name: interval
        value: "10"
        type: "int"





























