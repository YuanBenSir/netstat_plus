# netstat++
一款适用于辅助Linux应急响应小工具，可优化输出netstat的结果，提取出外网IP、端口号、进程PID、进程名称、路径、状态等信息
## **功能点：**

1、提取出外网地址，忽略本地和内网地址。

2、显示连接对应的进程 PID、名称和路径。

3、显示进程当前的运行状态（例如运行、休眠、僵尸等）。

4、输出包含原始 netstat 输出及优化输出的内容，方便对比。

5、识别进程中正在外连的内网穿透工具，例如nps、frp、tailscale、WireGuard、ngrok。


## **使用方法**

使用的时候要添加可执行权限

```
chmod +x 文件名
```

运行

```
./文件名
```

运行后会自动在当前目录输出文件，里面包含原始的netstat的输出结果，和经过优化的信息

**状态说明：**

​	•	**R**：运行中 (Running)

​	•	**S**：休眠 (Sleeping)

​	•	**D**：磁盘等待 (Disk sleep)

​	•	**Z**：僵尸进程 (Zombie)

​	•	**T**：暂停 (Stopped)

​	•	**X**：已终止 (Dead)

优化后的输出信息示例

```
------------------------

外网地址: 3.78.132.46:443

进程 PID: 9329

进程名称: tailscaled

进程路径: /usr/sbin/tailscaled

进程状态: S

------------------------
```

如果识别到内网穿透的情况：

```
------------------------
检测到以下内网穿透工具：
内网穿透工具: tailscale
外连 IP: 3.78.132.46:443
进程路径: /usr/sbin/tailscaled
------------------------
```

## **使用须知**

1、请确定你的机器中有net-tools，因为此工具依靠的是netstat命令，如果没有可以使用下面的命令安装

Debian_ubuntu系列

```
sudo apt install net-tools
```

centos系列

```
yum install net-tools
```

2、建议以root权限运行 这样root权限能看到的信息很全。

