# Fast-Ngrok  ~~穿透，超速了。~~

[Windows用户点我](https://github.com/coder-yunyi/fast-ngrok/blob/main/README.md)

**所有支持平台版本的ngrok都在bin文件夹里，请对号入座**

- 启动ngrok：cd ./ngrok所在路径

- 启动指定隧道：./ngrok -config ngrok.conf start 隧道名称

- 配置自定隧道：
  配置保存在ngrok.conf中
  
  **不要乱改server_addr和trust_host_root_certs！！！**

  右键记事本 / VSCode打开
  格式如下：
  
  tunnels:
  
  ​    (隧道名称):
  
  ​        remote_port:(映射到服务器上的端口，范围**0-65535**，*必选*)
  
  ​        subdomain:(映射该隧道时使用的子域名，**未配置子域名映射该隧道时要指定子域名**，*可选*)
  
  ​        proto:
  
  ​            (映射类型，*必选*  https/http/tcp/udp): 127.0.0.1:(映射到本地的端口，*必选*)
  
- 穿透指定端口+指定二级域名：

  ./ngrok.exe -config=ngrok.conf -subdomain 子域名 映射到本地的端口

- 穿透指定端口+启动指定隧道：

  ./ngrok -config=ngrok.conf -subdomain 子域名 start 隧道名称

- 使用自己的域名穿透+穿透指定端口：
  ./ngrok.exe -config=ngrok.conf -hostname 自己的域名(xxx.xxx.xxx) 映射到本地的端口

- 使用自己的域名穿透+启动指定隧道：
  ./ngrok.exe -config=ngrok.conf -hostname 自己的域名(xxx.xxx.xxx) start 隧道名称

成功穿透后启动ngrok的shell窗口内会有"<font color=#008000 >online</font>"字样
下面有映射在**外网**的域名 就是那个“**xxx.vaiwan.com**”
*(://前面标的是协议)*

## Q&A

<details>
    <summary>Ngrok安全吗？</summary>
    <br/>
    <p>如果您怀疑fast-ngrok项目内的ngrok.exe有后门，请自行检查src文件夹内的源码，没有进行任何代码混淆，如果仍然有疑虑请自行编译</p>
    <a href="https://github.com/inconshreveable/ngrok">点我查看ngrok1.7开放源代码本尊</a>
</details>
<details>
    <summary>穿透后无法正常访问？</summary>
    <br/>
    <p>1.可能是您的子域名被占用了，请更换子域名(使用自定义域名的请检查解析)</p>
    <p>2.检查您映射的协议和端口</p>
    <p>3.使用自定义域名的请先<strong>在工信部备案</strong>！！！(映射服务器使用阿里云国内线路服务器，所以要备案)</p>
</details>
<details>
    <summary>Fast-ngrok有什么限制？</summary>
    <br/>
    <p>正常使用的情况下，Fast-ngrok不对用户的流量/带宽/会话时间/子域名/映射端口数作任何限制</p>
    <strong>但以下情况例外:</strong>
    <p>1. 3小时内单ip任意隧道上/下行带宽总计超过2GB，将对此ip所有隧道上/下行带宽限制为2Mbps，持续48小时</p>
    <p>2. 15分钟内单ip所有隧道上/下行带宽总计超过2GB，封禁此ip，持续72小时，并强制关闭所有隧道</p>
    <p>3. 搭建任意非法站点，封禁此ip，持续2021年</p>
</details>

