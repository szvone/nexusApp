## <u>免责声明</u>

代码已开源，自行编译，也可以使用Github自动化编译好的程序！

使用本程序默认你电脑没东西不怕偷！！！

代码完全开源，安全性可自行询问AI！

## <u>NexusApp 节点工具</u>

NexusApp 是一套包含服务端和客户端的节点工具，支持跨系统部署。

## <u>和官方CLI的区别</u>

官方的CLI是开一个窗口使用一个节点NodeId，本程序是魔改CLI，自动切换NodeId，降低429错误出现的频率，自动重试失败的任务。

所以本程序需要运行1个服务端，N个客户端，客户端开的越多，跑的越快，出现429错误的频率也越高，配置也吃的越多。所以自行把握开几个客户端！


| 功能&#xA;   | 官方CLI&#xA;       | 节点工具&#xA;                                |
| ----------- | ------------------ | -------------------------------------------- |
| 分布式&#xA; | `单窗口单Node`     | `输入地址自动获取Node，窗口自动切换node`     |
| 可视化&#xA; | `查看单Node的数据` | `显示账号下所有node的总数据`                 |
| 处理任务    | `一边拉取一边计算` | `服务端拉取，分配给客户端计算，自动重试机制` |

## <u>开源说明</u>

程序已开源：

https://github.com/szvone/nexus_server

https://github.com/szvone/nexus_client

<u>此处为GithubAction自动化编译版本，强烈建议自行下载源码编译后使用。</u>

<u>使用预编译版本请自行确保数据安全，自己保护好自己的私钥还有电脑上的数据。</u>

<u>使用本程序则默认同意已经做好一切措施保护自己的数据。</u>

<u>本程序只需要地址即可运行，不需要私钥。</u>

## <u>工具下载</u>

[服务端](https://github.com/szvone/nexus_server/releases/)

[客户端](https://github.com/szvone/nexus_client/releases/)


## <u>文件说明</u>


| 系统&#xA;         | 服务端程序&#xA;            | 客户端程序&#xA;                    |
| ----------------- | -------------------------- | ---------------------------------- |
| Windows&#xA;      | `nexus_server-windows.exe` | `nexus_client-windows.exe` |
| Linux&#xA;        | `nexus_server-linux`       | `nexus_client-linux`               |
| Mac M芯片&#xA; | `nexus_server-macos-arm`      | `nexus_client-macos-arm`              |
| Mac Intel芯片&#xA; | `nexus_server-macos-intel`   |`nexus_client-macos-intel`              |



## <u>使用说明</u>

1. 下载文件

   -> 根据自己的系统下载好服务端程序[服务端下载](https://github.com/szvone/nexus_server/releases/)

   -> 根据自己的系统下载好客户端程序[客户端下载](https://github.com/szvone/nexus_client/releases/)

   -> 上方的下载链接为GithubAction自动化构建的，如需要更高的安全性，请自行下载源码进行构建。



2. 启动服务端程序（根据系统选择对应文件）。

   -> Win 系统直接双击nexus_server-windows.exe

   -> Linux 在对应目录使用终端输入启动命令 ./nexus_server-linux ,如果报错，可以使用 ./nexus_server-linux-static

   -> Mac-M芯片 在对应目录使用终端输入启动命令 ./nexus_server-macos-arm

   -> Mac-Intel芯片 在对应目录使用终端输入启动命令 ./nexus_server-macos-intel

   -> 服务端会自动弹出监控面板网页，如果没弹出，请手动打开网址[控制面板](http://127.0.0.1:8182)

   -> 如果是首次运行，请点击设置运行参数按钮，根据提示设置好参数，点击确认，会自动生成服务端配置文件(nexus_server.txt)和客户端配置文件(nexus_client.txt)，设置好后请关闭服务端重新打开。

3. 启动客户端程序。

   -> Win 系统直接双击nexus_client-windows.exe

   -> Linux 在对应目录使用终端输入启动命令 ./nexus_client-linux ,如果报错，可以使用 ./nexus_client-linux-static

   -> Mac-M芯片 在对应目录使用终端输入启动命令 ./nexus_client-macos-arm

   -> Mac-Intel芯片 在对应目录使用终端输入启动命令 ./nexus_client-macos-intel

   注意，配置文件nexus_client.txt需要和客户端程序一个目录。



4. 服务端和客户端可跨系统部署（例如 Windows 服务端搭配 Linux 客户端）。



## <u>运行参数</u>

* **程序工作地址**：服务端的 IP 地址，根据部署场景选择：

  * 服务端在**公网服务器**：填写公网 IP。
  * 服务端与客户端在**同一台电脑**：填写 `127.0.0.1`。
  * 服务端与客户端在**局域网内不同电脑**：填写服务端的局域网 IP（如 `192.168.1.100`）。

* **程序工作端口**：端口号，8000-9999，例如8182。若需同时在一台机器上运行多个服务端，请使用不同的端口。
  
* **任务读取线程**：导入了几个钱包地址就填几。
* **任务队列长度**：导入了几个钱包地址就填几。
* **钱包使用间隔**：当前服务端限制2分钟一个任务，所以固定填写120。
* **节点使用间隔**：固定填写1。
* **频繁等待间隔**：固定填写10。
* **任务钱包地址**：填写你的钱包地址。支持多个钱包地址，一行一个。


## <u>注意事项</u>

* 端口号需确保在防火墙中开放，避免被拦截。
* 配置文件需与对应程序放在同一目录下，否则可能导致读取失败。
* 如有问题，欢迎提交 Issue 反馈！



## <u>监控面板</u>

本程序自带运行状态监控面板，使用浏览器打开
网址：http://IP:端口
例如：[http://127.0.0.1:8182](http://127.0.0.1:8182)

![程序状态截图](status.png)
