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

   -> 在上方点击绿色按钮Code，点击 Download ZIP ,下载后解压，得到配置文件，nexus_server.txt和nexus_client.txt

   -> 根据下方配置说明修改好内容。

   -> 根据自己的系统下载好服务端程序[服务端下载](https://github.com/szvone/nexus_server/releases/)

   -> 根据自己的系统下载好客户端程序[客户端下载](https://github.com/szvone/nexus_client/releases/)

   -> 上方的下载链接为GithubAction自动化构建的，如需要更高的安全性，请自行下载源码进行构建。



2. 先启动服务端程序（根据系统选择对应文件）。

   -> Win 系统直接双击nexus_server-windows.exe

   -> Linux 在对应目录使用终端输入启动命令 ./nexus_server-linux ,如果报错，可以使用 ./nexus_server-linux-static

   -> Mac-M芯片 在对应目录使用终端输入启动命令 ./nexus_server-macos-arm

   -> Mac-Intel芯片 在对应目录使用终端输入启动命令 ./nexus_server-macos-intel

   注意，配置文件nexus_server.txt需要和程序一个目录

3. 再启动客户端程序。

   -> Win 系统直接双击nexus_client-windows.exe

   -> Linux 在对应目录使用终端输入启动命令 ./nexus_client-linux ,如果报错，可以使用 ./nexus_client-linux-static

   -> Mac-M芯片 在对应目录使用终端输入启动命令 ./nexus_client-macos-arm

   -> Mac-Intel芯片 在对应目录使用终端输入启动命令 ./nexus_client-macos-intel

   注意，配置文件nexus_client.txt需要和程序一个目录



4. 服务端和客户端可跨系统部署（例如 Windows 服务端搭配 Linux 客户端）。



## <u>配置说明</u>

### 1. 服务端配置（`nexus_server.txt`）&#xA;

服务端配置文件需填写以下信息：

```
address: 0x4917a3442E37844423075021fF02e6b4Ea111e6f,0x4917a3442E37844423075021fF02e6b4Ea111e62

port: 8182

queue: 20

worker: 5
```

* **address**：填写你的钱包地址（替换示例中的默认地址）。支持多个钱包地址，使用英文的逗号“ , ”分隔。
* **port**：端口号，需与客户端配置的 `port` 保持一致（示例为 8182，可自定义）。
* **queue**：取值为「计划开启的客户端数量 × 3」（示例中 5 个客户端对应 15，可根据实际数量调整，不需要严格一致，可以小点，尽量不要太大以免429）。
* **worker**：填写计划开启的客户端总数量（示例为 5，即同时运行 5 个客户端，不需要严格一致，可以小点，尽量不要太大以免429）。

### 2. 客户端配置（`nexus_client.txt`）&#xA;

客户端配置文件需填写以下信息，请直接修改文件内容，不要新建文件：

```
host: 127.0.0.1

port: 8182
```

* **host**：服务端的 IP 地址，根据部署场景选择：

  * 服务端在**公网服务器**：填写公网 IP。
  * 服务端与客户端在**同一台电脑**：填写 `127.0.0.1`。
  * 服务端与客户端在**局域网内不同电脑**：填写服务端的局域网 IP（如 `192.168.1.100`）。
* **port**：端口号，需与服务端配置的 `port` 完全一致（示例为 8182）。

### 3. 多开说明&#xA;

若需同时在一台机器上运行多个服务端，请使用不同的端口。

## <u>注意事项</u>

* 端口号需确保在防火墙中开放，避免被拦截。
* 配置文件需与对应程序放在同一目录下，否则可能导致读取失败。
* 如有问题，欢迎提交 Issue 反馈！



## <u>监控面板</u>

本程序自带运行状态监控面板，使用浏览器打开网址：http://IP:端口，例如：http://127.0.0.1:8182

![程序状态截图](status.png)

