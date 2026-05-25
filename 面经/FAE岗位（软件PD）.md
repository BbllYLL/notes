# 北高智PD快充产品线

## BOBhonestar北高智

[深圳市好上好信息科技股份有限公司](https://www.bobholdings.com/cn)  
[深圳市北高智电子有限公司](https://www.honestar.com/)  

**简介**
北高智成立于2000年，聚焦电子元器件分销业务，是深圳市好上好信息科技股份有限公司（股票简称：好上好，股票代码：001298）旗下全资子公司。  
[2025 年年度报告.PDF](https://disc.static.szse.cn/disc/disk03/finalpage/2026-03-13/b71aeb58-9224-4e79-8c00-7fecc881f462.PDF)  
[2025 年度审计报告.PDF](https://file.finance.sina.com.cn/211.154.219.97:9494/MRGG/CNSESZ_STOCK/2026/2026-3/2026-03-13/11993120.PDF)

**与该公司是否有交集？**  
[Nordic中国区巡回技术研讨会圆满收官- 深圳市北高智电子有限公司](https://www.honestar.com/productinfo/121282.html)  
在seeed（矽递科技）中，担任模组MCU产品线的FAE，2025年11月中旬，同事参加了Nordic巡回技术研讨会，回来进行分享研讨会的内容

**关于北高智PD快充芯片主要代理厂商？**  
INJOINIC (英集芯)  
SILERGY（矽力杰）  
SGMICRO （圣邦）  
Nexperia (安世)  
Microchip （微芯）  
PI（帕沃英蒂格盛）  
O2Micro(凹凸 )  

# Type-C接口简介
![Pasted_20260525083946_FAE岗位（软件PD）](FAE%E5%B2%97%E4%BD%8D%EF%BC%88%E8%BD%AF%E4%BB%B6PD%EF%BC%89_assets/Pasted_20260525083946_FAE%E5%B2%97%E4%BD%8D%EF%BC%88%E8%BD%AF%E4%BB%B6PD%EF%BC%89.png)  

| 引脚编号 | 引脚名称 | 功能描述                          | 信号类型  |
| ---- | ---- | ----------------------------- | ----- |
| A1   | GND  | 接地                            | 电源    |
| A2   | TX1+ | USB 3.1 超高速发送差分对（正）           | 高速数据  |
| A3   | TX1- | USB 3.1 超高速发送差分对（负）           | 高速数据  |
| A4   | VBUS | 总线电源（默认5V，PD可协商至48V）          | 电源    |
| A5   | CC1  | 配置通道1（连接检测、方向识别、PD通信）         | 配置/通信 |
| A6   | D+   | USB 2.0 差分数据线（正）              | 低速数据  |
| A7   | D-   | USB 2.0 差分数据线（负）              | 低速数据  |
| A8   | SBU1 | 边带使用通道1（用于音频或DisplayPort备用模式） | 辅助信号  |
| A9   | VBUS | 总线电源                          | 电源    |
| A10  | RX2- | USB 3.1 超高速接收差分对（负）           | 高速数据  |
| A11  | RX2+ | USB 3.1 超高速接收差分对（正）           | 高速数据  |
| A12  | GND  | 接地                            | 电源    |

1. **VBUS（引脚A4/A9/B4/B9）：** 电源引脚。默认电压为5V，通过PD协议可协商至最高48V，最大电流5A，从而实现高达240W的充电功率。
2. **CC1/CC2（引脚A5/B5）：** 配置通道。这是Type-C的灵魂引脚，负责：
    - 连接检测与方向识别
    - 供电角色（Source/Sink）协商
    - PD协议通信（BMC编码）
    - Alternate Mode（备用模式）协商
3. **SBU1/SBU2（引脚A8/B8）：** 边带使用通道。在DisplayPort或音频配件模式下，用于传输辅助信号。
4. **TX/RX差分对：** 用于USB 3.1/3.2 Gen 1/2超高速数据传输，速率可达10Gbps甚至20Gbps。

# PD协议简介（USB Power Delivery）  

[USB Power Delivery | USB-IF](https://www.usb.org/document-library/usb-power-delivery)  
官网文档  

[专为USB Type-C及功率传输而设的STM32解决方案 - 意法半导体](https://www.st.com.cn/content/st_com/zh/ecosystems/stm32-usb-c.html)  

![Pasted_20260525085656_FAE岗位（软件PD）|697](FAE%E5%B2%97%E4%BD%8D%EF%BC%88%E8%BD%AF%E4%BB%B6PD%EF%BC%89_assets/Pasted_20260525085656_FAE%E5%B2%97%E4%BD%8D%EF%BC%88%E8%BD%AF%E4%BB%B6PD%EF%BC%89.png)  

# PD协议分层模型  

![Pasted_20260525090503_FAE岗位（软件PD）|332](FAE%E5%B2%97%E4%BD%8D%EF%BC%88%E8%BD%AF%E4%BB%B6PD%EF%BC%89_assets/Pasted_20260525090503_FAE%E5%B2%97%E4%BD%8D%EF%BC%88%E8%BD%AF%E4%BB%B6PD%EF%BC%89.png)  

- Type-C接口层：负责底层的连接检测（Attach）、端口角色（Source/Sink）确定、VBUS供电控制等。这是PD通信的物理基础。

- 物理层 (PHY)：使用双相标记码（BMC，Biphase Mark Coding）在CC（Configuration Channel）线上进行半双工串行通信。负责位的编码、解码和时钟恢复。

- 协议层：核心层。定义数据包结构（消息头、数据对象）、通信规则（GoodCRC、Accept、Reject等）、电源协商的状态机（如Source Capabilities, Request, Power Ready）。

- 应用层：基于协议层协商的结果，执行具体的策略。例如，控制电源调整电压电流（PPS）、管理替代模式（如DisplayPort）、处理设备策略（如充电策略切换）。

# 电源角色与数据角色  

## 电源角色(Port Power Role)  
Source   
Sink   
DRD角色互换  
## 数据角色(Port Data Role)  

| 角色                   | 全称                     | 功能                  | 典型设备        |
| -------------------- | ---------------------- | ------------------- | ----------- |
| DFP<br>下行端口(Host)    | Downstream Facing Port | 数据主机，枚举并管理UFP设备     | 电脑、充电器（仅供电） |
| UFP<br>上行端口 (Device) | Upstream Facing Port   | 数据设备，响应DFP的枚举       | U盘、手机、外设    |
| DRD                  | Dual-Role Data         | 双重数据角色，可在DFP/UFP间切换 | 智能手机、平板     |


# 基本通信机制  

USB PD通信是基于连接的、有序的、可靠的消息交换过程，全部通过CC线完成。

1. **连接建立**：Type-C检测到连接后，建立VBUS供电，并启动PD通信。
2. **能力通告**：Source端发送 _Source_Capabilities_ 消息，告知支持的电压/电流组合（PDO）。
3. **功率请求**：Sink端根据自身需求，回复 _Request_ 消息，选择一种供电配置。
4. **协商确认**：Source端回复 _Accept_ 消息，然后调整电源输出，最后发送 _PS_RDY_ 消息。
5. **动态调整**：在连接过程中，可以根据需要重新协商功率（如PPS调整）。

CC线上采用BMC编码，每个数据包都以同步序列（Preamble）开始，以CRC校验结束，确保数据可靠性。  
每个消息都有一个Message ID，接收方必须回复GoodCRC消息确认。若未收到确认，发送方会重试（通常最多2次）。  
当通信出现严重错误时，可以发送Hard Reset信号（将VBUS拉低）来重启PD协商。Soft Reset则通过协议消息重置协议层。  
允许Sink端以20mV/50mA的步进精细请求电压电流，实现高效直充。  

# PD协议消息格式  

详细见手册《USB_PD_R3.2_V1.2_2026_05_20_redline》第6章  

主要大致分为  
1. 消息头 (Message Header)：包含消息类型、数据对象数量、消息ID等信息。
2. 数据对象 (Data Objects)：0到7个可变数量的数据对象，承载具体信息。
3. CRC (Cyclic Redundancy Check)：用于校验消息完整性的循环冗余校验码。

# PDO与RDO  

详细见手册《USB_PD_R3.2_V1.2_2026_05_20_redline》第6.4章  

PDO (Power Data Object) 是源端（如充电器）向宿端（如手机）宣告其供电能力的结构化数据对象。每个PDO代表一种可用的电源配置。  
RDO (Request Data Object) 是宿端向源端请求特定电源配置的数据对象，用于响应源端的PDO列表。  

# PD协议状态机  

详细见手册《USB_PD_R3.2_V1.2_2026_05_20_redline》第9.2章  
## Source端状态机  

## Sink端状态机  

# CC线通信原理  

详细见手册《USB_PD_R3.2_V1.2_2026_05_20_redline》第5.1章  

在USB Type-C接口中，CC（Configuration Channel）线是实现连接检测、方向识别、角色确定和功率协商的关键通道。它完全不同于传统的USB数据线（D+/D-），是一条专用的双向通信通道。  

>Type-C接口中有两个CC引脚，但同一时间只有一条CC线用于通信，具体由插入方向决定。  

| 角色         | CC引脚配置     | 电阻值                                               | 含义               |
| ---------- | ---------- | ------------------------------------------------- | ---------------- |
| 电源（Source） | 上拉电阻 Rp    | 默认：56kΩ ±5%  <br>1.5A：22kΩ ±5%  <br>3.0A：10kΩ ±5% | 广播供电能力           |
| 设备（Sink）   | 下拉电阻 Rd    | 5.1kΩ ±20%                                        | 标识为受电设备          |
| 双角色电源（DRP） | Rp 与 Rd 交替 | 动态切换                                              | 可在Source/Sink间切换 |
| 音频配件       | 下拉电阻 Ra    | 800Ω - 1200Ω                                      | 标识音频设备           |
**检测过程**
* Source端在CC引脚上提供上拉电压（通常为5V），并通过测量CC引脚电压来检测是否连接了Rd。
* 当Sink插入后，CC引脚电压被Rd拉低，Source检测到这个电压变化，确认连接建立。
* Source根据CC引脚电压值（由Rp和Rd分压决定）判断Sink的插入方向，并识别Sink的电流能力。

# BMC编码(Biphase Mark Coding, BMC)  
BMC编码是USB Power Delivery（PD）协议中用于在CC线上传输消息的物理层编码方案。它是一种自同步、直流平衡的编码方式，确保数据在单线通信中的可靠传输。
![Pasted_20260525101903_FAE岗位（软件PD）](FAE%E5%B2%97%E4%BD%8D%EF%BC%88%E8%BD%AF%E4%BB%B6PD%EF%BC%89_assets/Pasted_20260525101903_FAE%E5%B2%97%E4%BD%8D%EF%BC%88%E8%BD%AF%E4%BB%B6PD%EF%BC%89.png)

详细见手册《USB_PD_R3.2_V1.2_2026_05_20_redline》第5.3章  
