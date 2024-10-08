# Day1
## bugfree
### Bug的状态：
- New：提出bug（测试）
- Open：查看过bug，未解决（开发）
- Resolve：bug已有解决方案，且提交过代码（开发）
- Resolve - 已验证：在固件包中验证通过（开发）
- Resolve - 已审核：开发负责人确认bug已修复或同意bug解决办法（开发负责人）
- Halt：bug挂起，暂不修复（开发）
- Halt - 已审核：同意bug挂起（开发负责人）
- Hold：确认bug被挂起（测试）
- Hold - 已审核：测试负责人同意bug挂起（测试负责人）
- Closed：回归确认bug已通过（测试）
- Closed - 已审核：测试负责人确认bug已通过（测试负责人）
----------------------------------------------------------------------
### Bug的解决方案：
- 1、设计如此（By Design）:功能设计如此。
- 2、重复（Duplicate）：已提过类似的bug。
- 3、外部因素（External）：外部因素引起的bug。
- 4、已修复（Fixed）：已经修复。
- 5、不重现（Not Repro）：无法重现bug。
- 6、推迟（Postponed）：推迟解决该bug。
- 7、不修复（Won't Fix）：不做修复。

----------------------------------------------------------------------

### 解决Bug状态流转（研发）：
new --> open --> resolved --> resolved-已验证 --> resolved-已审核(开发负责人) 

### 挂起Bug状态流转（研发）：
new --> open --> halt --> halt-已审核（开发负责人）

----------------------------------------------------------------------

### 解决Bug流程：
- 1、open -> resloved:
    - 点击解决；
    - 选择bug解决方案；
    - 切换open到resolved后保存，保存后出包自测。
    - 注意！！！若是Fixed，需要填写如下格式的注释内容：
        - 【问题描述】：描述产生的问题，对标题的问题进行补充。
        - 【问题原因】：详细描述引发该问题的原因
        - 【解决方案】：当前提交解决的方案，在此描述该方案
        - 【提交记录】：SVN或者GIT提交记录
        - 【测试建议】：对于改动补充的测试要点，测试步骤等
- 2、resloved -> resloved-已验证：
    - 使用出的新包，验证没有问题后，填写注释；
    - 注释内容：软件验证版本号：V1.0-XXXXXXX；
    - 切换open到resolved后保存，保存后告知研发负责人进行审核
    
----------------------------------------------------------------------
### Bug挂起流程：
- open -> halt:
    - 点击解决;
    - 选择Postponed解决方案，并填写注释，注释内容说明推迟解决，挂起原因;
    - 切换open到halt后保存，保存后告知研发负责人进行审核。


=====================================================================================

## Xshell:
----------------------------------------------------------------------
### 连接本地电脑：打开Xshell窗口后，不连接远程主机或设备，则作用等同于cmd窗口。
### 远程连接其它主机：
#### 支持远程的前提条件：
- ①远程终端（本地主机）能访问到被远程主机的地址，最简单的判断方式是用ping检测。   
- ②被远程设备启用了ssh或telnet相关程序/进程。
#### 连接方式：
- ssh登录方式：
    - 登录的命令格式：  
        - ①ssh 用户名@地址 端口号；  
        - ②ssh 地址 端口号。
    - 端口号：公司内部设备的端口号大多是12580；若命令中不写上端口号，则默认为22。一般服务器默认连接端口是22，但为了安全相关人员可以在服务器中更改端口号。
    - ssh登录可以使用证书，可以不使用证书，实际情况根据远程主机决定。
        - 不需要证书的情况：执行远程命令连接成功后会自动弹出如下窗口，输入密码即可成功登录远程主机。
        - 需要证书的情况：连接成功后会自动弹出如下窗口，先导入证书（证书所在私有云路径：/公共文档/密钥）:
            - ①选择“用户密钥”（也可以选择“文件”，那就是不把证书导入xshell，直接使用电脑上的证书）  
            - ②选择“导入”
            - ③选择电脑上的证书文件   
            - ④输入对应的证书密码，点击“确定”即可导入成功  
            - ⑤导入证书后，在连接成功后弹出的窗口中选择相应的证书，输入与证书对应的密码即可。
    
- telnet登录方式：
    - 登录的命令格式：  
        - ①telnet 用户名@地址 端口号；  
        - ②telnet 地址 端口号。
    - 端口号：使用方式与ssh登录相同，公司目前的路由器等设备telnet都是用默认端口23。命令中不写端口号，则默认用23。
----------------------------------------------------------------------
### 日志记录：
- 对已打开窗口开启日志记录：鼠标点进对应窗口里面，点击xshell左上角的“文件”→“日志”→点击“启动”，选择日志保存路径并命名日志文件后保存即可。
- 快速打开日志文件夹：点击xshell左上角的“文件”→“日志”→点击“打开日志文件夹”即可快速进入日志所在文件夹。
- 记录日志时写入时间戳：鼠标点进对应窗口里面，点击xshell左上角的“文件”→点击“默认会话属性”弹出如下窗口↓勾选“写入日志文件”并“确定”即设置完成。
----------------------------------------------------------------------
### 创建快速输入按钮:
1）点击xshell菜单栏中的“查看”→“快速命令”，勾选“快速命令栏”即可启用快速命令工具。  
2）在窗口左下角点击添加按钮；标签自己命名即可，字串中输入自己常用的命令。

----------------------------------------------------------------------
### 常用快捷键:
1）复制已选中文本：Ctrl+Insert  
2）粘贴文本：Shift+Insert  
3）输入错误指令导致串口无法继续输入时，执行Ctrl+D中断执行

----------------------------------------------------------------------

### 导入/导出文件（！！！重要）:
- 已成功登录设备后台之后：
    - ①设备上导出文件：可使用sz命令导出设备上的文件到电脑上。  
    - ②文件导入设备：可以使用rz命令导入文件或将电脑上的文件拖曳到已连接的窗口即可。

----------------------------------------------------------------------

### 常见问题：
Q:发现一直无法用ssh方式登录设备后台  
A:串口连接设备，进入后台cat /etc/config/dropbear查看ssh服务是否开启或端口号是否正确；如果服务已开启端口号也正确，确认IP地址是否正确。  
B：或者用telnet测试验证相应端口是否开启服务：telnet IP PORT;若能弹出交互，则表示有服务；反之，表示该IP:PORT无服务；


=====================================================================================

## 串口 基础知识：
----------------------------------------------------------------------
### 学习资料：https://blog.csdn.net/fuhanghang/article/details/123274451

----------------------------------------------------------------------
### 串口应用场景：
- 适用场景：
需要访问设备后台，但无法通过ssh/telnet等网络方式访问设备后台时
- 常用场景：
    - 升级或写入uboot；
    - 当系统损坏，可通过串口写入系统固件；
    - 打印系统中的各类日志，日志用于查bug。
----------------------------------------------------------------------
### 操作连接串口并登录系统后台：
- 1、连接物理线路（记得插电！！！）：
    - ①工具：
        - **串口针脚**：用到3个针脚，分别是GND、TXD、RXD；GND表示接地，TXD表示用于发送数据，RXD表示用于接收数据，引脚焊到板子上（TXD和RXD要交叉）；
        - **杜邦线**：需要3根；
        - **串口转USB工具**：一端是usb接口，另一端是一排针脚，我们使用到的针脚是GND、TXD、RXD，功能与主板上的串口同名针脚相同。
        - **USB延长线**：杜邦线长度不够时，转换器可接延长线；
    - ②连接方式（详情图见 -- 串口基础知识）：
        - 用杜邦线将串口和串口转USB工具相连，再将转换器的usb接口接到电脑上。
    - 当主板上没有标识串口针脚的名称时，使用万用表测试，得知GND的位置：
        - 1、万用表开关转向直流电压（V）   
        - 2、万用表的两支测电笔，各接触串口的一只针脚（GND一般为最外侧的针脚）   
        - 3、测出的值为正数时，黑色笔接触的引脚为地线；测出的值为负数时，红色笔接触的引脚为地线
    - 注意！！！千万不要接vcc针脚！
- 2、在xshell上设置串口连接信息：
    - ①选择协议：serial
    - ②选择usb转串口工具所在的端口，进入电脑的设备管理器查看端口，如com21
    - ③设置波特率（大部分设备的波特率是57600、115200，少部分的波特率是9600）Port即是选择端口，Baud Rate便是设置波特率，点击“确定”保存即完成创建。
- 3、设置日志记录
- 4、设置连接信息后，开始连接
----------------------------------------------------------------------
### 其他注意事项：
Q:串口连接成功后打印乱码？  
A:检查杜邦线是否连接稳固、主板上的引脚是否存在虚焊、波特率是否正确。

Q:连接后无法输入文字、无法打印日志？  
A:检查tx和rx是否接反，若确认未接反，则尝试重启xshell。

目前部分设备默认关闭了串口的输入、ssh、telnet功能，可通过工具开启相关功能，具体的开启工具请找导师或相关人员。

=====================================================================================
## IP 基础知识:
----------------------------------------------------------------------
### 概念：把整个因特网看成为一个单一的、抽象的网络。IP 地址就是给每个连接在互联网上的主机（或路由器）分配一个在全世界范围是唯一的 32 位的标识符。（由互联网名字和数字分配机构ICANN进行分配。）IP地址分为公有地址和私有地址。
- 是网络层的地址。
- IP地址是指互联网协议地址（英语：Internet Protocol Address，又译为网际协议地址），是IP Address的缩写。
- IP地址是IP协议提供的一种统一的地址格式，它为互联网上的每一个网络和每一台主机分配一个逻辑地址，以此来屏蔽物理地址的差异。目前还有些ip代理软件，但大部分都收费。
----------------------------------------------------------------------
### IP 地址的编址方法：
- 分类的 IP 地址：最基本的编址方法。
- 子网的划分：对最基本的编址方法的改进。
- 构成超网：比较新的无分类编址方法。

----------------------------------------------------------------------

### 分类 IP 地址：
- 概念：将IP地址划分为若干个固定类。每一类地址都由两个固定长度的字段组成，其中一个字段是网络号**net-id**，它标志主机（或路由器）所连接到的网络，而另一个字段则是主机号**host-id**，它标志该主机（或路由器）。**主机号在它前面的网络号所指明的网络范围内必须是唯一的。**
- IP地址的组成：  
    网络号 + 主机号 (32位)
    - 网络号：是一个网络的标识，俗称网段
        - 一个网络中所分配的IP地址都会带有这个网络的标识，这样`可以保证每个网络的网络号不同`，即可以保证它们分配的IP地址不同
    - 主机号：是一个主机在一个网络中的标识
        - 一个网络中有很多主机，主机号就是用于在一个网络中标识不同的主机
- 这种两级的 IP 地址可以记为：
IP 地址 ::= { <网络号>, <主机号>}  （::=  代表“定义为”）
- IP的划分：
![](img/%E5%9B%BE%E7%89%8721.png)

----------------------------------------------------------------------
### 点分十进制记法：
- 机器中存放的 IP 地址是 32 位二进制代码， 如：10000000 00001011 00000011 00011111。
- 将每 8 位的二进制数转换为十进制数， 为：128.11.3.31。

----------------------------------------------------------------------

### 一般不使用的特殊的 IP 地址。  
![](img/%E5%9B%BE%E7%89%8722.png)

----------------------------------------------------------------------
### 如何判断IP地址是A类B类还是C类?
- 简单的说：
    - A类网络（第一段数字范围为1～126）的IP地址范围为：1.0.0.1－126.255.255.254；
    - B类网络（第一段数字范围为128～191）的IP地址范围为：128.1.0.1－191.255.255.254；
    - C类网络（第一段数字范围为192～223）的IP地址范围为：192.0.1.1－223.255.255.254；
    - D类网络：第一个字节的数字范围为224～239，是多点播送地址，用于多目的地信息的传输，和作为备用；
    - E类网络：第一段数字范围为240～254，E类地址保留，仅作实验和开发用。
    - 特殊：
        - 全零（“0．0．0．0”）地址`对应于当前主机`。全“1”的IP地址（“255．255．255．255”）是`当前子网的广播地址`。
        - 127开头的地址`主要用于测试`。

----------------------------------------------------------------------
### 私有（本地） IP 地址。
- A类地址中，10.0.0.0~10.255.255.255；（`10.的全部`）
- B类地址中，172.16.0.0~172.31.255.255；（`172.16 到 172.31的全部`）
- C类地址中，192.168.0.0~192.168.255.255。（`192.168.的全部`）
- 私有地址只在局域网内部使用.

----------------------------------------------------------------------
### 公有IP地址：
- A类地址中
    - 1.0.0.0~9.255.255.255  
    - 11.0.0.0~126.255.255.255
- B类地址中
    - 128.0.0.0~172.15.255.255
    - 172.32.0.0~191.255.255.255
- C类地址中
    - 192.0.0.0~192.167.255.255
    - 192.169.0.0~223.255.255.255
----------------------------------------------------------------------
### 组播IP地址（详见ppt）。
- D类地址空间，224.0.0.0~239.255.255.255。
- 其中，224.0.0.0~224.0.0.255为路由协议预留的永久组地址。

----------------------------------------------------------------------
### 特殊IP地址：
- $127.x.x.x$ ——— 给本地网地址测试使用。 
- $224.x.x.x$——— 为多播地址段。 
- $255.255.255.255$ ——— 为通用的广播地址。

----------------------------------------------------------------------

### 补充：
- 全局IP要求唯一, 但是私有IP不需要; 在不同的局域网中出现相同的私有IP是完全不影响的；
- 一个路由器可以配置两个IP地址, 一个是WAN口IP, 一个是LAN口IP(子网IP)；
- 路由器LAN口连接的主机, 都从属于当前这个路由器的子网中；
- 每一个家用路由器, 其实又作为运营商路由器的子网中的一个节点. 这样的运营商路由器可能会有很多级, 最外层的运营商路由器, WAN口IP就是一个公网IP了；
- 子网内的主机需要和外网进行通信时, 路由器将IP首部中的IP地址进行替换(替换成WAN口IP), 这样逐级替换, 最终数据包中的IP地址成为一个公网IP. 这种技术称为NAT(Network Address Translation，网络地址转换)。

----------------------------------------------------------------------

### IP址查看：
- PC电脑查看IP/MAC地址：
    - ①ipconfig/all指令；
    - ②网络连接详细信息。
- 嵌入式设备（无线路由器等）查看本身的IP/MAC地址：
    - ifconfig指令

=====================================================================================
## MAC（以太网地址） 基础知识：
----------------------------------------------------------------------
### 概念：MAC地址（Media Access Control Address），直译为媒体访问控制地址，也称为局域网地址（LAN Address），以太网地址（Ethernet Address）或物理地址（Physical Address），它是一个用来确认网上设备位置的地址。
- 是数据链路层的地址。
- MAC地址用来识别数据链路层中相连的节点。
- 在OSI模型中，第三层网络层负责IP地址，第二层数据链接层则负责MAC地址。
- MAC地址用于在网络中唯一标示一个网卡，一台设备若有一或多个网卡，则每个网卡都需要并会有一个唯一的MAC地址。 
- 在网卡出厂时就确定了, 不能修改。mac地址通常是唯一的(虚拟机中的mac地址不是真实的mac地址, 可能会冲突; 也有些网卡支持用户配置mac地址)。
- 请注意，如果连接在局域网上的主机或路由器安装有多个网络适配器，那么这样的主机或路由器就有多个“地址”。更准确些说，这种 48 位“地址”应当是某个接口的标识符。
----------------------------------------------------------------------
### 48 位的 MAC 地址：
- IEEE 802 标准规定 MAC 地址字段可采用 6 字节 ( 48位) 或 2 字节 ( 16 位) 这两种中的一种。
- IEEE 的注册管理机构 RA 负责向厂家分配地址字段 6 个字节中的前三个字节 (即高位 24 位)，称为组织唯一标识符。
- 地址字段 6 个字节中的后三个字节 (即低位 24 位) 由厂家自行指派，称为扩展唯一标识符，**必须保证生产出的网络适配器没有重复地址**。
- 一个地址块可以生成 224 个不同的地址。这种 48 位地址称为 MAC-48，它的通用名称是 EUI-48。
- 生产适配器时，6 字节的 MAC 地址已被固化在适配器的 ROM，因此，MAC 地址也叫做硬件地址 (hardware address)或物理地址。
- “MAC地址”实际上就是适配器地址或适配器标识符 EUI-48。
----------------------------------------------------------------------
### MAC 地址的结构 ：
- MAC地址通常表示为12个16进制数，每2个16进制数之间用冒号隔开。
- 如：08:00:20:0A:8C:6D就是一个MAC地址。其中前6位16进制数08:00:20代表网络硬件制造商的编号，它由IEEE分配，而后6位16进制数0A:8C:6D代表该制造商所制造的某个网络产品（如网卡）的系列号。
- 每个网络制造商必须确保它所制造的每个以太网设备都具有相同的前三字节以及不同的后三个字节。这样就可保证世界上每个以太网设备都具有唯一的MAC地址。 
- 注：内部局域网中的网卡使用的MAC只要不与局域网内的其它网卡地址相同即可。
- 以太网地址的第32 位是组播地址的标识位：
    - 47 ～33位 —— 制造厂商标识
    - 32位 —— 组播标识位
    - 31 ～24位 —— 制造厂商标识
    - 23 ～0位 —— 系列号
----------------------------------------------------------------------
### 单播地址：
- 当组播标识位为1 时表示该MAC 地址是一个组播地址。对于网卡MAC ，这一位必须是0 ，表示一个单播MAC 地址。
- 指第一个字节的最低位是0的MAC地址，如：xxxxxxx0-xxxxxxxx-xxxxxxxx-xxxxxxxx-xxxxxxxx-xxxxxxxx，以下都为合法的单播地址：   
    X0:XX:XX:XX:XX:XX   |   X2:XX:XX:XX:XX:XX  
    X4:XX:XX:XX:XX:XX   |   X6:XX:XX:XX:XX:XX  
    X8:XX:XX:XX:XX:XX   |   XA:XX:XX:XX:XX:XX  
    XC:XX:XX:XX:XX:XX   |   XE:XX:XX:XX:XX:XX  
    其中的X代表0~F中的任一个16进制数。
----------------------------------------------------------------------
### 广播地址：
- 每个比特都是1的MAC地址。
- 地址 FF:FF:FF:FF:FF:FF 为广播地址。
- 只能用在目的地址段，不能作为源地址段。目的地址为广播地址的数据包，可以被一个局域网内的所有网卡接收到。
----------------------------------------------------------------------
### 组播地址：
- 指第一个字节的最低位是1的MAC地址，如：01.xx.xx.xx.xx.xx 。
- 无论MAC地址第1字节是0x01、0xC1或者是0x33都表示这个MAC地址是组播地址。
- 组播只能作为目的地址，不能作为源地址。组播地址可以被支持该组播地址的一组网卡接收到。
- 关于组播地址，有这么个误解：MAC地址第1字节必须是0x01才表示组播地址，连TCP/IP详解上也这么说（见中文版12.4.2第一段）。之所以有这样的误解，是因为到目前为止，大部分组播MAC地址的第1字节都是0x01。
- 01:00:5E:00:00:00 ～ 01:00:5E:7F:FF:FF 用于ip 地址的组播。
- 网卡可以接收以下3 种地址的数据包：
    - 1.目的地址跟自己的网卡地址是一样的数据包。
    - 2.目的地址为FF:FF:FF:FF:FF:FF 广播地址的数据包。
    - 3.目的地址为跟自己的组播地址范围相同的数据包。
- 在以太网的应用当中：
    - 如果你希望你的数据包只发给**一个网卡** —— 目的地址用对方的网卡地址；  
    - 如果你想把数据包发给**所有的网卡** —— 目的地址用广播地址；  
    - 如果你想把数据包发给**一组网卡** —— 目的地址用组播地址。

----------------------------------------------------------------------
### MAC地址查看：
- PC电脑查看IP/MAC地址：
    - ①ipconfig/all指令；
    - ②网络连接详细信息。
- 嵌入式设备（无线路由器等）查看本身的IP/MAC地址：
    - ifconfig指令

=====================================================================================
## ARP协议：
----------------------------------------------------------------------
### 概念：
- ARP（Address Resolution Protocol）即地址解析协议，是用来将对方IP地址解析为MAC地址的一种协议。
- 用于实现从 IP 地址到 MAC 地址的映射。
- 在局域网通信中，当PC或其它网络设备有数据要发送给另一个主机或设备时，它必须知道对方的IP地址。但仅有IP地址是不够的，因为`IP数据报文必须封装成帧才能通过物理网络发送`，因此发送方PC还必须有接收方的物理地址（MAC地址）才可以，ARP就是实现将对方IP地址解析为MAC地址这个功能的协议。
- 主机发送信息时将包含目标IP地址的ARP请求**广播到局域网络上的所有主机**，并接收返回消息，以此确定目标的物理地址。
- 一般的ARP形式是向局域网络上的所有主机发送ARP请求包，其中包含主机 A 想要知道的主机 B 的 IP 地址的 MAC 地址。
- 简而言之，ARP 就是一种解决地址问题的协议，它以 IP 地址为线索，定位下一个应该接收数据分包的主机 MAC 地址。**如果目标主机不在同一个链路上，那么会查找下一跳路由器的 MAC 地址**。
- 如果是不同链路怎么办呢？这就要使用到 代理 ARP 了，通常 ARP 会被路由器隔离，但是采用代理 ARP (ARP Proxy) 的路由器可以将 ARP 请求转发给临近的网段。使多个网段中的节点像是在同一网段内通信。

----------------------------------------------------------------------

### ARP 工作过程：
- 1、首先检查ARP缓存列表中是否有对应IP地址的目的主机的MAC地址源，如果有，直接发送数据；如果没有，设备`广播`ARP请求包，`该数据包包括的内容有：源主机IP地址，源主机MAC地址，目的主机的IP地址`。这个网络上的`所有设备`都会收到这个ARP请求;
- 2、如果一台设备发现请求中的IP地址与自己的`匹配`，首先会从数据包中`取出源主机的IP和MAC地址`写入到ARP缓存列表中，如果`已经存在，则覆盖`。然后向源设备发送一个`包含自己的MAC地址的ARP响应包`；如果`不匹配`，则将会`丢弃`这个ARP请求。
- 3、源主机收到ARP响应包后，将目的主机的IP和MAC地址`写入ARP缓存`列表，并利用此信息发送数据；如果源主机`一直没有收到ARP响应`数据包，表示`ARP查询失败`。

- ARP查询失败时常见故障排除:https://support.huawei.com/enterprise/zh/doc/EDOC1000079675/de4c5a9b

----------------------------------------------------------------------
### ARP 缓存：
- ARP 高效运行的关键就是维护每个主机和路由器上的 ARP 缓存(或表)。
- 这个缓存维护着每个 IP 到 MAC 地址的映射关系。
- 通过把第一次 ARP 获取到的 MAC 地址作为 IP 对 MAC 的映射关系到一个 ARP 缓存表中，下一次再向这个地址发送数据报时就不再需要重新发送 ARP 请求了，而是直接使用这个缓存表中的 MAC 地址进行数据报的发送。
- 每发送一次 ARP 请求，缓存表中`对应的`映射关系都会被清除。
- 通过 ARP 缓存，降低了网络流量的使用，在一定程度上防止了 ARP 的大量广播。
----------------------------------------------------------------------
### ARP查看：
- windows查看ARP：
    - arp-a指令
- 路由器查看ARP：
    - arp-a指令
----------------------------------------------------------------------
### RARP：
- 与 ARP 相对的，RARP(Reverse Address Resolution Protocol) 是将 ARP 反过来，**从 MAC 地址定位 IP 地址的一种协议**，将打印机服务器等小型嵌入式设备接入网络时会使用到。
- 平常我们设置 IP 地址一般会有两种方式，手动设置 和 DHCP 动态获取，但是对于嵌入式设备来说，它**没有任何输入接口**，也**无法通过 DHCP 获取动态地址**, 在这种情况下，就要使用到 RARP 了。
- 你需要准备一个 RARP 服务器，在这个服务器上注册设备的 MAC 地址和 IP 地址，然后将设备接入网络，设备会发出一条 IP 和 MAC 地址的查询请求给服务器，服务器会告诉设备其 IP 地址和 MAC 地址。
----------------------------------------------------------------------
### ARP 攻击：
- ARP 是一种非常不安全的协议，目前已经有很多涉及 ARP 的攻击，最主要的就是使用**代理 ARP** 功能**假扮主机**，对 ARP 请求作出应答，通过伪造 ARP 数据包来窃取合法用户的通信数据，造成影响网络传输速率和盗取用户隐私信息等严重危害。
- ARP 攻击分类：
    - `ARP 泛洪攻击`：通过向网关发送大量 ARP 报文，导致网关无法正常响应。首先发送大量的 ARP 请求报文，然后又发送大量虚假的 ARP 响应报文，从而造成网关部分的 CPU 利用率上升难以响应正常服务请求，而且网关还会被错误的 ARP 缓存表充满导致无法更新维护正常 ARP 缓存表，消耗网络带宽资源。
    - `ARP 欺骗主机攻击`：ARP 欺骗主机的攻击也是 ARP 众多攻击类型中很常见的一种。攻击者通过 ARP 欺骗使得局域网内被攻击主机发送给网关的流量信息实际上都发送给攻击者。主机刷新自己的 ARP 使得在自己的ARP 缓存表中对应的 MAC 为攻击者的 MAC，这样一来其他用户要通过网关发送出去的数据流就会发往主机这里，这样就会造成用户的数据外泄。
    - `欺骗网关的攻击`: 欺骗网关就是把别的主机发送给网关的数据通过欺骗网关的形式使得这些数据通过网关发送给攻击者。这种攻击目标选择的不是个人主机而是局域网的网关，这样就会攻击者源源不断的获取局域网内其他用户韵数据．造成数据的泄露，同时用户电脑中病毒的概率也会提升。
    - `中间人攻击`: 中间人攻击是同时欺骗局域网内的主机和网关，局域网中用户的数据和网关的数据会发给同一个攻击者，这样，用户与网关的数据就会泄露。
    - `IP地址冲突攻击`: 通过对局域网中的物理主机进行扫描，扫描出局域网中的物理主机的 MAC 地址，然后根据物理主机的 MAC 进行攻击，导致局域网内的主机产生 IP 地址冲突，影响用户的网络正常使用。

----------------------------------------------------------------------

### ARP应用——检测IP地址冲突
- 何时？
    - 网络中新增设备时，例如添加新的路由器或者电脑。
- 在给`主机分配IP地址或更改了IP地址后`，主机可以`以自己的IP地址作为目的IP地址，进行ARP Request广播`。如果`该网段下有重复的IP`地址，则会`接收到ARP reply报文`，并且可以知道`哪个网卡与此IP重复`了，从而可以`避免IP的复用`。
- 指令：arping IP——当同一个ip返回是同一个mac地址时，没有冲突；如果`同时返回多个mac地址时，表示地址冲突`。
    - arping 命令安装: apt-get install iputils-arping

----------------------------------------------------------------------
### 总结：
- ARP 是 TCP/IP 实现中的一个基本协议，它通常在应用程序或用户没有察觉到的情况下运行。ARP 可以用于映射 IP 地址为 MAC 地址。

=====================================================================================
## IP地址和MAC地址的总结：
----------------------------------------------------------------------
### `一个设备需要同时拥有IP地址和MAC地址!!`。
----------------------------------------------------------------------
### MAC地址和IP地址的区别：
- IP地址可变，MAC地址不可变。
- IP 地址和 MAC 地址虽然都是“地址”，但它们并不相同，在网络通信中发挥的作用也不一样。总的来说，IP 地址解决的是数据在外网（因特网、互联网）的传输问题，MAC 地址解决的是数据在内网（局域网）中的传输问题。
- 如果两台通信的计算机处于同一个局域网，那么理论上只凭借 MAC 地址就可以找到对方；如果两台计算机跨网传输数据，那么 IP 地址和 MAC 地址缺一不可。
----------------------------------------------------------------------
### 对比理解MAC地址和IP地址：
- IP地址描述的是路途总体的 起点 和 终点;
- MAC地址描述的是路途上的每一个区间的起点和终点;  
举例说明：  
唐僧西天取经，别人会问唐僧从哪来，要到哪里去。唐僧都会回答道，贫僧是从东土大唐而来，要到西方拜佛求经。  
这里的东土大唐就是：源IP  
西方雷音寺就是：目的IP    
有人问：和尚，你上一站从哪里来，下一站要到哪里去。唐僧回答：贫僧上一站从火焰山来，下一站要到女儿国去。  
火焰山和女儿国就是：源MAC地址，目的MAC地址，在途中，所以是一直在改变的。

----------------------------------------------------------------------
### 有MAC地址为什么还需要IP地址呢：
- MAC地址用来`唯一地标识`一个`网络接口`，但它`没有寻址功能`。
- 不同的网络使用不同的硬件地址，要使这些网络能够互相通信，就必须进行非常复杂的硬件地址转化工作，由用户或用户主机来完成这项工作几乎是不可能的事。
- IP编址就就是来解决这个问题的，连接到互联网的主机只需要各自拥有一个IP地址，它们之间的通信就像连接在同一个网络那么简单方便。

----------------------------------------------------------------------
### 为什么有了MAC地址还要有IP地址：
- 只拥有MAC地址的话，只有在同一网络区域内，才能进行数据传输，不能跨网络区域。
- 如果想跨网络区域进行数据传递，最现实的方法就是借助ISP提供的网络区域
    - 网络业务提供商(Internet Service Provider，简称ISP)
- ISP能提供全球互联的网络——因特网，借助因特网可以传输数据给连接因特网上的机器。
- 有一个村落（局域网），它很封闭，与世隔绝，如同陶渊明讲的世外桃源。但是他的建筑非常美丽，几乎都是四合院，好几户人家居住在一个四合院里。(**同一IP地址接入多个设备，每个设备都有一个MAC地址。**)

=====================================================================================
## DHCP 基础知识：

----------------------------------------------------------------------

### DHCP服务进程名:
- 进程名是`DNSmasq`

----------------------------------------------------------------------
### 概念：
- DHCP（Dynamic Host Configuration Protocol，动态主机配置协议）通常被应用在**大型的局域网络环境**中，主要作用是**集中的管理、分配IP地址，使网络环境中的主机动态的获得IP地址、Gateway地址、DNS服务器地址等信息，并能够提升地址的使用率**。
- 是一个局域网的网络协议，使用UDP协议工作，常用的2个端口：67(DHCP server),68(DHCP client)。
- DHCP协议采用客户端/服务器（C/S）模型，主机地址的动态分配任务由网络主机驱动。当DHCP服务器接收到来自**网络主机**申请地址的信息时，才会向网络主机发送相关的地址配置等信息，以实现网络主机地址信息的动态配置。DHCP具有以下功能：
    - 1、保证任何IP地址在同一时刻只能由一台DHCP客户机所使用。  
    - 2、DHCP应当可以给用户分配永久固定的IP地址。  
    - 3、DHCP应当可以同用其他方法获得IP地址的主机共存（如手工配置IP地址的主机）。  
    - 4、DHCP服务器应当向现有的`BOOTP客户端`提供服务。
        - BOOTP（Bootstrap Protocol）客户端是一种用于自动配置网络设备的网络协议。它是在没有可用的静态IP地址的情况下，通过网络自动获取配置信息的一种方式。
- 由于DHCP是C/S模式运行的，所以**使用DHCP**的设备为**客户端**，而**提供DHCP服务**的为**服务端**。DHCP客户端可以让设备**自动地**从DHCP服务器获得IP地址以及其他配置参数。服务器控制一段IP地址范围，客户端登录服务器时就可以自动获得服务器分配的IP地址和子网掩码。
----------------------------------------------------------------------
### 常用端口：
- DHCP Server端，使用UDP端口：67
    - DHCP Server可以在很多设备上部署，如Cisco、H3C、Juniper、Windows、Linux……都可以
- DHCP Client端，使用UDP端口：68
    - 客户端（主机、路由器、交换机、网络打印机、网络摄像头……都可以作为DHCP客户端）

----------------------------------------------------------------------
### 动态分配机制：
- 1、自动分配方式：在这种方式下DHCP服务器会给主机一个永久性的IP地址，只要DHCP的客户端第一次能够成功的从DHCP服务端获得IP地址，那么它就可以永久性的的使用该地址了。
- 2、动态分配方式：是指主机会获得一个**有时间限制**的IP地址，当时间到期或者主机主动放弃该地址的时候，这个地址才能被其它地址使用。
- 3、手工分配方式：客户端的IP地址由网络管理员指定的，DHCP服务器只是将指定的IP地址告诉给客户端主机。  

只有“动态分配方式”可以**重复使用**客户端不再需要的地址!!!

----------------------------------------------------------------------

### 静态分配机制：
- 出于某些原因，联网设备需要固定局域网IP，例如，局域网内的服务器必须固定IP，以便局域网内其他用户可以正常的访问。
- 这时，就需要DHCP服务设置静态地址分配，通过Mac地址绑定的方式，将指定设备的Mac地址与要分配的IP绑定。绑定后，路由器只会将被绑定的IP分配给对应的Mac地址的设备上，避免了其他设备收到这些IP地址，进而避免了IP冲突的问题。
- 注：使用了静态分配后，动态分配的地址池中不应包含静态分配的IP，否则可能造成网络地址冲突（两台客户端有相同的IP地址）。

#### 概念：
- 分配给户端的IP：由于DHCP地址池可用IP受限或者IP租约到期的原因，在客户端发起DHCP请求之后，分配的IP可能会变化。
- 在此种情况下，`同一个客户端的IP地址是可能发生变化的`，但`客户端的MAC地址是不会变`的，所以我们可以`通过IP和MAC绑定`，`实现`为客户端`分配静态IP`的目的。

#### 作用：
- 使用DHCP静态地址，就是让某个主机每次连接到这个路由器都使用同一个IP地址。DHCP识别主机靠的是MAC地址。
- 绑定后，路由器只会将被绑定的IP分配给对应的Mac地址的设备上，避免了其他设备收到这些IP地址，进而避免了IP冲突的问题。

----------------------------------------------------------------------
### DHCP地址池:
- 服务器分配给客户端的地址应在地址池范围内。
- 设置地址池时结束IP不应超过当前网段的最大主机地址，如起始地址为172.16.0.1/16，则最大允许设置分配172.16.0.1~172.16.255.255这个范围内的地址，当然也可在这个范围内设置更少的地址，如172.16.0.1~172.16.1.1，则是256个地址可用于分配，或172.16.0.10~172.16.0.15，则是6个地址可用于分配。
- 设置地址池时，地址池中**不应当包含DHCP服务器自身的LAN地址**，否则可能造成地址冲突。

----------------------------------------------------------------------
### DHCP租期：
- 当一个IP分配给MAC地址（指客户端网卡，每一个网卡都有对应的MAC地址作为网络中的唯一标识）后，在租期内，默认这个MAC地址的IP为该地址，不再进行分配。 当到期后，该地址被回收，重新分配。
- 设置地址租期，对于减轻DHCP压力，网络稳定有一定的好处，但是有些时候网络会因此出现诸如IP地址不够等一些问题。 

----------------------------------------------------------------------

### DHCP服务中有三个非常重要的参数：
- 1）地址池：IP地址范围，代表了服务器可以分配哪些IP地址给终端；
- 2）网关和DNS：固定参数，代表终端连接internet的出口和域名解析服务；
- 3）租期：时间参数，代表终端单次申请可以使用IP地址多长时间。

----------------------------------------------------------------------

### DHCP状态机：

如下图所示是比较常见的DHCP状态机:

DHCP的实现分为4步，分别是：
- 第一步：Client端`在局域网内`发起一个DHCP　Discover包，目的是想发现能够给它提供IP的DHCP Server。

- 第二步：可用的DHCP Server接收到Discover包之后，通过发送DHCP Offer包给予Client端应答，意在告诉Client端它可以提供IP地址。

- 第三步：Client端接收到Offer包之后，发送DHCP Request包请求分配IP。

- 第四步：DHCP Server发送ACK数据包，确认信息。


![](img/%E5%9B%BE%E7%89%8724.png)  

正常来说，一次DHCP过程只需要上面状态机的前四步，后面的`续约`是在DHCP的`租期到达1/2和7/8的时候`进行的。

### `DHCP协议在客户机和服务器运行一个状态机`:

![](img/%E5%9B%BE%E7%89%8726.png)

- 1.客户机开始处于`Init`状态：没有信息，并`广播DHCPDISCOVER消息`
- 2.`选择`状态：客户机`接收DHCPOFFER消息`，`直到决定使用哪个服务器和地址`
- 3.`请求`状态：当它做出选择，发出`DHCPREQUEST消息`来响应时，进入请求状态
- 4.接收ACK：
    - 可能会收到来自不需要的地址的ACK。如果`没有`发现它`需要的地址`，发送一个`DHCPDECLING消息`，并`转化到Init`状态
    - 接收到一个自己需要的地址的DHCPACK消息，`接受`它，`获得超时值T1(T/2)和T2(3T/4)`，并`进入绑定`状态，这是就能`使用这个地址直至过期`
- 5.IP续期:
    - 客户端从服务器租用IP地址会有一个`固定的租约期`。除了租约期限外，还有两个时间值T1和T2。其中，`T1定义为租约期限的一半，而T2定义为租约期限的3/4`。
    - 当`到达T1`定义的时间期限时，客户端会`向提供租约的原始服务器`发送`DHCP Request包（单播）`，尝试`重新建立租约`。
        - 如果`服务器接受`此请求，则`回复DHCP ACK`消息，`包含更新后的租约期限`，`续租后就会立刻更新T1和T2`；
        - 如果`不接受`租约更新请求，就`会发送DHCP NAK包`,此时DHCP客户端`立即`发起`DHCP DISCOVER`进程以寻求IP地址；
        - 如果`没有`从DHCP服务器`得到任何回复`，则继续使用此IP地址直到到达T2定义的时间限制。
    - 此后（假设此时仍未接收到任何回复），DHCP`客户端`会`定时`发送`DHCP Request包（单播）`。如果`一直都没有得到确认`，则`继续使用此IP地址`，`直到T2`定义的时间限制。
    - 此时(T2)，客户端会`发送DHCP Request包(广播)`，尝试`重新建立租约`。
    - 如果`租期到达`时，`仍然未更新租约`，则`地址自动释放`，`客户端既不能更新自己的租期，也无法从其他的DHCP服务器获得新的租期`，客户端`必须停止使用这个IP地址`，从而`停止常规的TCP/IP网络操作`。

- `T1和T2时间段都是发送DHCP Request包，只不过T1是单播发送，而T2是广播发送`。
        
----------------------------------------------------------------

### 报文类型（重要!!!!）：
- DHCP DISCOVER（广播） ： 客户端开始 DHCP 过程发送的包，是 DHCP 协议的开始
    - `源IP地址：0.0.0.0(指当前设备的IP)；目的IP地址：255.255.255.255`
    - `源MAC地址：自身MAC地址；目的MAC地址：ff:ff:ff:ff:ff:ff`
- DHCP OFFER（广播） ： 服务器接收到 DHCP DISCOVER 之后做出的响应，它`包括了给予客户端的 IP（yiaddr）、客户端的 MAC 地址、租约过期时间、服务器的识别符`以及其他信息：（`此时DHCP客户端没有IP地址，所以DHCP服务器同样使用广播进行通讯`）
    - `源IP地址：DHCP服务器的地址又或者是DHCP中继代理服务器的IP地址；目的IP地址：255.255.255.255（广播时）`
    - `源MAC地址：DHCP服务器的MAC地址；目的MAC地址：ff:ff:ff:ff:ff:ff（广播时） `
- DHCP REQUEST（REQUEST`首次`必须是`广播`——`为了告诉所有DHCP服务器自己已经做出选择，接受了某个DHCP服务器的租约`。之后可单播） ： 客户端对于服务器发出的 DHCP OFFER 所做出的响应，包含了`DHCP客户端的MAC地址、接受的租约中的IP地址、提供此租约的DHCP服务器地址`等信息。在`续约租期的时候同样会使用`。
    - `源IP地址：0.0.0.0（首次，此时没有得到DHCP服务器最后确认，DHCP客户端仍然不能使用租约中提供的IP地址）或者 分配到的IP地址（续租时）；目的IP地址：255.255.255.255（首次） 或者 DHCP服务器的地址（续租时）`
    - `源MAC地址：自身MAC地址；目的MAC地址：ff:ff:ff:ff:ff:ff（首次）或者 DHCP服务器的MAC地址（续租时）`
- DHCP ACK（广播） ： 服务器在接收到客户端发来的 DHCP REQUEST之后发出的成功确认的报文，包含了`租约期限及其他TCP/IP选项信息`。在建立连接的时候，客户端在接收到这个报文之后才会`确认`分配给它的` IP `和其他信息可以`被允许使用`（ACK包中`包含了客户端的MAC地址`）。
    - `源IP地址：DHCP服务器的地址又或者是DHCP中继代理服务器的IP地址；目的IP地址：255.255.255.255（广播时）`
    - `源MAC地址：DHCP服务器的MAC地址；目的MAC地址：ff:ff:ff:ff:ff:ff（广播时）`
- DHCP NAK ： DHCP ACK 的相反的报文，表示服务器拒绝了客户端的请求。
- DHCP RELEASE ： 一般出现在客户端关机、下线等状况。这个报文将会使 DHCP 服务器释放发出此报文的客户端的 IP 地址
- DHCP INFORM ： 客户端发出的向服务器请求一些信息的报文
- DHCP DECLINE ： 当客户端发现服务器分配的IP地址无法使用（如 IP 地址冲突时），将发出此报文，通知服务器禁止
使用该 IP 地址。

----------------------------------------------------------------

### DHCP Request和Offer报文什么时候广播什么时候单播？（不重要）
- 客户端发`DISCOVER报文`的时候，`bootp flage位`如果为`1`，代表`后续`以`广播`形式和`服务器`进行`交互`，为`0`代表后续`单播`。  
![](img/%E5%9B%BE%E7%89%8728.png)
- DHCP `request可以广播，也可以单播`:
    - 在`首次获取`地址时，request通过`广播`发送（`目的是为了拒绝其他给出响应的服务器`）。
    - 在`续租地址`时，request采用`单播或者广播（取决于discover的bootp flage）`。
- DHCP `Offer 可以广播，也可以单播`。
    - 如果discover报文，`bootp flags = 1`，则通过`广播`交互，`bootp flags = 0` 则通过`单播`交互。
    - 如果DHCP服务器使用MAC和IP绑定分配的方式，也可以单播交互。

----------------------------------------------------------------

### DHCP中继
- 1.简单网络中，`一个DHCP服务器可供一个局域网使用(由于广播的缘故)`
- 2.复杂网络中，可以通过`一个或更多DHCP中继代理`来中继DHCP流量。
- 3.中继代理`用于将DHCP操作扩展到跨越多个网段`。  
![](img/%E5%9B%BE%E7%89%8725.png)
- 4.使用中继的时机
    - 在一般情况下,中继`不会参与`客户机和服务器之间的所有DHCP流量交换。
    - 相反,它仅中继那些 广播消息(或IPv6中的组播)。这种消息通常在客户机`首次获得自已的地址时`交换。
    - 当一台客户机获得一个IP地址,并且服务器的IP地址使用服务器标识选项时,它可与服务器进行单播通信而不经过中继。
- 5.注意,中继代理在传统上是第3层设备,并且通常结合了路由功能。


----------------------------------------------------------------------

### 常见的应用场景：
- 咖啡厅、网吧、私人公司等规模较小的小型场所内的网络主机通过出口网关接入Internet网络。通过在出口网关上部署DHCP服务器，实现为网络主机自动分配IP地址等网络参数，方便统一管理和维护。
- 园区网中不同部门规划了不同网段，每个网段内的主机可以通过DHCP服务器动态获取IP地址等网络参数。如果主机与DHCP服务器不在同一网段，还需要部署DHCP中继。


=====================================================================================

## WIFI 基础知识：
----------------------------------------------------------------------
### WLAN定义：
- WLAN: Wireless Local Area Networks,无线局域网。
- 利用射频（RF）技术取代有线传输介质（双绞线/光纤等）构成的局域网。
- 摆脱了有线连接的束缚。
- 在真正意义上，WIFI它只是一个商标。随着无线的大量使用，我们在某种程度上，把WLAN和WIFI等价起来。
- 几种常见的无线局域网：  
![](img/%E5%9B%BE%E7%89%877.png)

----------------------------------------------------------------------
### 2.4GHZ 频段信道（图示见——无线基础知识）：
![](img/%E5%9B%BE%E7%89%879.png)
- 2.4GHz中国频段中，`同一信号最多`可提供`（1,6,11）`这样`三个互不干扰`的信道，以此类推
- 每信道占用22MHz频带带宽（信道带宽只有20Mhz，2Mhz作为隔离频段）;
- 该频段是免费使用，但是不同国家支持的信道不一样，2.4Ghz频段共分为14个信道，目前中国只支持1-13信道。![](img/%E5%9B%BE%E7%89%878.png)

### 5GHZ 频段信道（以高频段的149-165频段举例，图示见——无线基础知识）：
![](img/%E5%9B%BE%E7%89%8710.png)
- 5.8GHz中国频段中，可提供`五个互不干扰`的信道，5G频段内，`每一个信道，都是独立无干扰的`
- 每信道占用20MHz频带带宽;
- 该高频段是无限制性免费使用的，当然，`目前中国还有36-48信道也是免费使用，52-64是有限制性免费使用`

----------------------------------------------------------------------

### 2.4G与5.8G的差别是什么？
- 1、传输速度：2.4G传输速度慢，5G传输速度快(频率不同导致)。
- 2、距离范围：2.4G传输距离远，5G传输距离近。
- 3、抗干扰性：2.4G较5G而言抗干扰能力更强。
- 4、穿透性：2.4G频率比5G的穿透性更强，在有墙体或其他障碍物的情况下，2.4G穿透性方面的优势更为明显。
- 5、兼容性：
    - 虽然大多数现代设备都支持5GHz频段，但仍有一些较老的设备只支持2.4GHz频段。
    - 一般而言，支持5G的设备是肯定支持2.4G的，但是支持2.4G的就不一定支持5G了。

----------------------------------------------------------------------

### 2.4G与5.8G的应用场景？
- 2.4G：
    - 2.4GHz频段的主要优点是其`覆盖范围更广`，因此适合用于`大型家庭或办公室网络`中。它也`更加兼容老设备`，并且`可以穿透墙壁和其他障碍物`，从而使其在大范围内传输信号成为可能。
- 5.8G：
    - 5GHz频段的主要优点是其`传输速度更`快，因此适合用于高速数据传输的应用程序，例如`在线游戏、高清视频流和大型文件下载等`。它还具有`更少的干扰和更好的安全性`，因为其频段在市场上并不常见，所以不容易被他人干扰。5GHz频段的无线信号`传输范围相对较小`，因此更`适合`在`小范围内使用`，例如`小型家庭或办公室网络`。
----------------------------------------------------------------------

### WLAN组成及连接
![](img/%E5%9B%BE%E7%89%8711.png)
- STA：无线终端设备，通常是指接收无线信号的设备，在我们的WIFI系统中，通常是指，手机、ipad等连接WIFI信号的终端
- AP：Access Point，无线接入点，通常是指发射WIFI信号的设备，比如我们的无线路由器
- STA连接AP的过程：
    - 发现与接入：无线终端发现AP，发现成功后，再连接相应的WIFI信号
    -  认证：双方之间交换密钥之类的信息，判断是否通过，最常见的为无线密码，当然，没有密码的也是一种认证方式。
    - 关联：认证通过后，STA向AP发起关联请求，只有收到关联回复OK后，关联成功，即可开始收发数据  
    ![](img/%E5%9B%BE%E7%89%8712.png)



----------------------------------------------------------------------
### WLAN扫描：
- STA发现AP的过程：
    - Passive Scanning:即被动扫描，终端通过侦听AP定期发送的Beacon帧来发现网络  
        - AP会每隔一段时间向周围广播Beacon帧，如同心跳，表明自己alive的状态，STA就会收到这个帧，从而知道AP的一些信息
        - Beacon包含了什么：BSSID、SSID、Channel、RSSI、Beacon interval、Country、Vendor Specific(供应商)。。。
        - 如图：使用 wlan.fc.type_subtype == 0x08 筛选，把所有Beacon帧过滤出来，Source列就可以找到我们的路由器  
        ![](img/%E5%9B%BE%E7%89%8720.png)
    - Active Scanning:即主动扫描，终端主动在每个信道上发送Probe requset报文，从Probe response回复报文中获取BSS的基本信息
- 以上提到的，是指搜索到了这个AP，要连接这个AP，`还要制定（specify）这个SSID去扫描一次，确保这个AP存在`  。

----------------------------------------------------------------------
### WLAN认证（Authentication）：
- 注意认证和加密的区别：
    - 认证：就是确认凭证、检查身份，比如你是警察，你要确认对方是不是警察，那就的确认对方的身份、凭证等
    - 加密：就是通过有规律的把原始数据打乱或重组等方式再呈现出新的数据。比如你是警察，对方是卧底，你们就需要通过暗号进行交流，避免暴露
- 两种认证方式：
    - 开发系统（Open System）：  
    ![](img/%E5%9B%BE%E7%89%8713.png)
        - 就是很简单的发送身份声明跟认证请求，也就是通过Mac地址为身份证明，而MAC地址又是独一无二的，所以AP在这种方式中就直接按802.11最原始的方式，有身份证且唯一就OK，然后AP侧只有成功或者失败，没有更多的交流，AP也不Care其他，只有Yes or No！
    - 共享密钥（Share Key）:
        - 必须使用WEP的加密方式，通信双方要使用相同的密钥去对一个“code”进行加密和解密  
        ![](img/%E5%9B%BE%E7%89%8714.png)
        - 1.STA发一个认证请求给到AP
        - 2.AP利用随机密钥（Random key）和初始向量生成一个Challenge Text ，我们就叫“Code1.0”给回STA
        - 3.STA用STA端已知密钥加密得到“Code2.0”，发给AP（就是我们输入的密码的过程）
        - 4.AP使用AP端已知的密钥去解密“Code2.0”，然后比较“Code1.0”是否一致
        - 5.AP比对完成，发送认证答复，成功/失败

----------------------------------------------------------------------

### WLAN关联（Association）：
- 如图可以看到，一来一回的交流，到了最后关联的阶段，如果通过认证，STA就会向AP端发一个Association Request帧去请求关联
![](img/%E5%9B%BE%E7%89%8715.png)  
![](img/%E5%9B%BE%E7%89%8716.png)
- AP收到了Association Request，是怎么处理的呢？
    - 这里就要注意到Association Request里面包含的Listen Interval，意思就是STA会定期聆听beacons帧，为什么要定期，因为要省电节能，STA可以暂时关闭802.11 网络介面的天线，这个Listen interval间隔就是STA的休眠时间（这里指的是WLAN，而不是我们说的待机休眠），是通过AP送来的Beacons Interval计算出来的，也就是说，STA不需要一直监听每个beacons，只需要间隔多个beacons周期后聆听一次，达到省电目的；
    - 802.11规范AP端因为要为STA暂存一些帧，当STA处于休眠阶段，AP将这些帧暂存起来等待STA苏醒，然后发送出去，这就涉及到AP的容量了，当好多个STA连接后，能不能继续给新的STA分配资源去暂存就是AP要考虑的事情了，如果做不到，那可能就会在Association Response返回失败了

- Listen interval可以说是STA开给AP的一个价格，AP有足够的空间给STA暂存帧，则交易成功，如果没有那交易失败  
![](img/%E5%9B%BE%E7%89%8717.png)

----------------------------------------------------------------------
### 关联之后：
- WPA/WPA2的四次握手：
    - 上面除了WEP共享密钥的认证方式，看到有我们输入密码的过程，我们输入的密码又是在哪里用到呢？答案是WPA的四次握手！
    - 我们**输入的密码**并不是用来连接上AP的，而**是用来**作为跟AP**沟通时加密数据**的，通过使用四次握手的方式来**产生所需要的密钥**。  
    ![](img/%E5%9B%BE%E7%89%8718.png)
    - PMK：Pairwise Master Key, 成对主密钥，认证者用来生成组临时密钥（GTK）的密钥
    - PTK：Pairwise Transient Key, 成对临时密钥，最终用于加密单播数据流的加密密钥
    - Nonce：一个随机生成的值，只使用一次
    - MIC：Message Integrity Code，消息完整性校验码，针对一组需要保护的数据计算出的散列值，用来防止数据遭篡改
    - GTK：Group Temporal Key, 组临时密钥，最终用于加密广播和组播数据流的加密密钥。
- 使用抓包工具抓包可以看到4次握手过程：
![](img/%E5%9B%BE%E7%89%8719.png)

- WPA/WPA2使用4次握手的方式来产生所需要的密钥。即通过一系列的交互，从PMK（Pairwise Master Key）生成PTK（Pairwise Transient Key）

----------------------------------------------------------------------



----------------------------------------------------------------------

## WIFI产品中的常见名词参数

### STA：
- 无线终端设备，通常是指接收无线信号的设备，在我们的WIFI系统中，通常是指，手机、ipad等连接WIFI信号的终端

### AP：
- Access Point，无线接入点，通常是指发射WIFI信号的设备，比如我们的无线路由器。

### SSID：
- Service Set Identifier的简写，中文名叫服务集标识符，在不同厂家的产品中，WEB设置页面中的叫法不一样。
- 也可以叫做无线局域网(WLAN)的名称。
- 举例：我们手机打开WIFI开关，扫描到的的那些WIFI 名字，就是AP设备发射出来的SSID。当我们修改了无线设备中关于这一项的配置，手机扫描到的无线名字就会发生变化。

### 无线协议：
- 设备的无线射频工作在哪一个协议上。
- 比如我们要设置AP的2.4G的WIFI部分，2.4G的WIFI协议，它经历了11B、11G、11n、	11AX，那么就可以选择这些不同协议，不同协议，支持的最大速率不同。
- 注意：设备支持的最高协议，是由芯片决定的，不是所有的芯片都支持所有的协议。

### 信道：
- 指设备的WIFI工作时，当前使用的无线射频使用的频率点。
- 比如我们要设置AP的2.4G的信道时，中国有1-13信道。
- 如果我们要设置AP的5G的信道时，中国有36-48,52-64,149-165。


### 信道带宽：
- 指设备的WIFI工作时，占用的频率宽度。
- 设备支持的信道带宽，是由无线协议和芯片共同决定的。


### 加密方式：
- STA和AP在认证过程中，会通过预设的加密方式来确定是否认证通过。
- 常见的加密方式：
    - 开放式（不加密）；
    - WEP（早期）；
    - WAP-PSK；
    - WAP2-PSK；
    - WAP/WAP2-PSK混合；
    - WAP-企业。

### 功率：
- 指的是设备的WIFI发射功率，在相同天线下，设备的发射功率越强，覆盖范围越广。
- 我们的MTK方案产品中，WEB页面有时提供（强、中、弱）或者
（穿墙、普通、节能）等各种等级的功率设置。这个不同的等级，
最终代表的功率是代码里面可以定义的。
- 注意：任何设置的WIFI功率等级，不可能超过设备的校准功率。按照百分比的话，最多100%。

### 无线用户数限制：
- 指的该射频的WIFI信号，能够连接的无线终端数。超过这个数值，拒绝连接。
- 在设置2G的WIFI时，如果设置了该值为6，代表2G这个无线信号，只能连接6个无线终端，第7个无线终端连接时，会连接不上。
- 注意：设置这个值时，通常无线射频的2G和5G都有单独的配置项。

### 双频合一：
- 开启该功能，指设备的2G和5G WIFI的SSID是一个相同的名字。包括他们的加密方式、密码。有些设备的WEB页面支持设置，有些不支持。
- 注意：开启该项功能后，我们使用手机扫描，会发现只能扫描到一个SSID，此时无法区分这个这个时候是2G还是5GSSID。但是可以通过专用的无线扫描工具扫描分辨出来。

### 隐藏SSID：
- 开启该功能，手机等无线终端扫描不到改WIFI的无线名称。
- 但是通过借助第三方工具，可以查看该WIFI是否正常启动了（如果第三方工具也不显示该SSID，但是可以通过后台查看参数来判断）
- 注意：开启该项功能后，如果我们的无线终端要连接该SSID，只能通过在无线终端里面，配置该SSID的信息，才能连接成功。


----------------------------------------------------------------------

### 网桥和路由器的区别:
- 1.网桥工作在`链路层`，路由器工作在`网络层`；
- 2.网桥`基于MAC地址`转发，路由器`基于IP地址`转发；
- 3.网桥`不隔离`广播，而路由器可以`隔离`广播;
    - 网桥在转发广播帧的时候会将广播帧转发到`所有的端口`上，这样就使得广播域仍然存在，如果`广播帧过多则容易出现广播风暴`。
        - 广播风暴：简单的讲是指当广播数据充斥网络无法处理，并占用大量网络带宽，导致正常业务不能运行，甚至彻底瘫痪。
    - 而路由器不同，路由器在转发广播帧的时候`不会无目的的转发`，只有`指向特定网络地址`的网络流量`才能够通过路由器`，因此`可以防止广播帧的泛滥`。
- 4.网络性质不同：
    - 用网桥连接起来的网络从性质上来说仍然`属于同一性质`的网络。
    - 用路由器连接的网络`仍然保持各自性质的独立性`并`拥有自己的网络地址`。


----------------------------------------------------------------------
=====================================================================================
### 计算机网络学习网站：https://developer.aliyun.com/article/1153503

=====================================================================================













