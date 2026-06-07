# 岗位JD
![Pasted_20260606102557_SSD FAE工程師（宏芯宇电子）](SSD%20FAE%E5%B7%A5%E7%A8%8B%E5%B8%AB%EF%BC%88%E5%AE%8F%E8%8A%AF%E5%AE%87%E7%94%B5%E5%AD%90%EF%BC%89_assets/Pasted_20260606102557_SSD%20FAE%E5%B7%A5%E7%A8%8B%E5%B8%AB%EF%BC%88%E5%AE%8F%E8%8A%AF%E5%AE%87%E7%94%B5%E5%AD%90%EF%BC%89.png)
根据岗位JD，工作内容包含了 FAE PIE NPI多岗位的职责，不知道后续是否可以接触到产线

# 存储行业


# 存储相关知识

主要分为两类ROM RAM 
## ROM（Read Only Memory）
一开始就代表着只读存储器，但是现在我们生活上的手机或者电脑的硬盘当作ROM，但是现在的ROM不仅仅是只读的，还可以进行反复编程，这是为什么呢？
### 发展历程
BIOS（Basic Input Output System）电脑启动运行的第一个固件 只读不写
PROM（Programmable ROM）可编程只读存储器 写入程序后就不可更改
EPROM（Rrasable Programmable ROM）可抹除可编程只读存储器 需要紫外线进行擦除
EEPROM（Electrically Rrasable Programmable ROM）电可抹除可编程只读存储器
### Flash
Nor Flash（或非门）
主流原厂：兆易创新 GD（GD25Q64），华邦 Winbond（W25Q64）
定位场景：非易失、小容量、嵌入式设备中、存放启动代码、Bootloader、固件、配置参数，

Nand Flash（与非门）
主流原厂：三星、SK 海力士、美光、铠侠（原东芝存储）、长江存储
定位场景：非易失、大容量存储系统、文件、数据（手机存储、SSD、eMMC、U 盘、存储卡）

Nor Flash 是将我们的栅极晶体管并联在一起（每一位都可寻址）
Nand Flash 是将我们的栅极晶体管串联在一起（接线更少，更大容量集成）
![Pasted_20260607143240_SSD FAE工程師（宏芯宇电子）|685](SSD%20FAE%E5%B7%A5%E7%A8%8B%E5%B8%AB%EF%BC%88%E5%AE%8F%E8%8A%AF%E5%AE%87%E7%94%B5%E5%AD%90%EF%BC%89_assets/Pasted_20260607143240_SSD%20FAE%E5%B7%A5%E7%A8%8B%E5%B8%AB%EF%BC%88%E5%AE%8F%E8%8A%AF%E5%AE%87%E7%94%B5%E5%AD%90%EF%BC%89.png)
### Flash内部是如何读写数据的
浮栅mos是在mos管的氧化层又加了一个浮栅层，浮栅层是可以导电的，这样它就可以存储信息了。先说怎么写信息，如果我们给栅极加二十伏的高电压，栅底加零伏电压，p区里面的部分自由电子就会被吸引到浮栅层，这样即是写给它多电，自由电子依旧会存储在浮栅层，因为浮栅层上下都是二氧化硅绝缘层，自由电子根本逃不出去。

逻辑0：
![Pasted_20260607144830_SSD FAE工程師（宏芯宇电子）](SSD%20FAE%E5%B7%A5%E7%A8%8B%E5%B8%AB%EF%BC%88%E5%AE%8F%E8%8A%AF%E5%AE%87%E7%94%B5%E5%AD%90%EF%BC%89_assets/Pasted_20260607144830_SSD%20FAE%E5%B7%A5%E7%A8%8B%E5%B8%AB%EF%BC%88%E5%AE%8F%E8%8A%AF%E5%AE%87%E7%94%B5%E5%AD%90%EF%BC%89.png)
逻辑1：
![Pasted_20260607145358_SSD FAE工程師（宏芯宇电子）](SSD%20FAE%E5%B7%A5%E7%A8%8B%E5%B8%AB%EF%BC%88%E5%AE%8F%E8%8A%AF%E5%AE%87%E7%94%B5%E5%AD%90%EF%BC%89_assets/Pasted_20260607145358_SSD%20FAE%E5%B7%A5%E7%A8%8B%E5%B8%AB%EF%BC%88%E5%AE%8F%E8%8A%AF%E5%AE%87%E7%94%B5%E5%AD%90%EF%BC%89.png)
存储1bit数据就要1个MOS管
1G = 1024 MB = 1048526 KB = 1073741824 Byte = 8589934592 bit

为什么擦除都是按页擦除，在生产工艺中，将mos管的栅极连接到同一块衬底，只需要给这个衬底加20伏的高电压，就能完成擦除整块数据的操作。
闪存一页数据就有65536个存储单元。一块数据当中有512页。
![Pasted_20260607150510_SSD FAE工程師（宏芯宇电子）](SSD%20FAE%E5%B7%A5%E7%A8%8B%E5%B8%AB%EF%BC%88%E5%AE%8F%E8%8A%AF%E5%AE%87%E7%94%B5%E5%AD%90%EF%BC%89_assets/Pasted_20260607150510_SSD%20FAE%E5%B7%A5%E7%A8%8B%E5%B8%AB%EF%BC%88%E5%AE%8F%E8%8A%AF%E5%AE%87%E7%94%B5%E5%AD%90%EF%BC%89.png)

1GB就需要256个闪存数据块，同时芯片的封装尺寸是标准化的，要想在这个芯片里面封装足够多的存储单元，需要把存储单元做的足够小，这样才能装下更多的存储单元。但是缩小之后，很多问题随之而来，最到氧化层也要薄，因为擦写的过程电子需要从这个氧化层进进出出，次数多了，最到氧化层就会损坏，数据也就不能很好的保存。为了解决这个问题，人类发明了3D NAND Flash。
目前为止，3D Flash 闪存已经做到232层对比，存储密度到达了大约15GB 每平方毫米
![Pasted_20260607151232_SSD FAE工程師（宏芯宇电子）](SSD%20FAE%E5%B7%A5%E7%A8%8B%E5%B8%AB%EF%BC%88%E5%AE%8F%E8%8A%AF%E5%AE%87%E7%94%B5%E5%AD%90%EF%BC%89_assets/Pasted_20260607151232_SSD%20FAE%E5%B7%A5%E7%A8%8B%E5%B8%AB%EF%BC%88%E5%AE%8F%E8%8A%AF%E5%AE%87%E7%94%B5%E5%AD%90%EF%BC%89.png)

## RAM（Random Access Memory）
### DRAM（Dynamic RAM）
DRAM 依靠电容存数据，电荷会不断流失，必须动态刷新才能维持数据，因此叫动态
定位场景：临时运行程序、高速数据缓存（电脑内存条 DDR）
### SRAM（Static RAM）
SRAM 通电后数据稳定保持，无需外部干预，因此叫静态
定位场景：小容量、高速、高可靠性（芯片中的缓存）

## SSD硬盘的总线协议与接口
个人认为，硬盘的总线协议与接口的设计都是围绕着解决硬盘的数据传输能力展开
关于设备与硬盘间传输，主要有从以下三个模块进行数据交互：
**协议**：AHCI、NVMe、SCSI
**总线**：SATA、PCle、SAS
**接口**：SATA、mSATA、SATA Express、M.2、PCle、、、
这三者之间相辅相成，如果有一个不行，将会大大降低我们的传输速度
![Pasted_20260607220901_SSD FAE工程師（宏芯宇电子）](SSD%20FAE%E5%B7%A5%E7%A8%8B%E5%B8%AB%EF%BC%88%E5%AE%8F%E8%8A%AF%E5%AE%87%E7%94%B5%E5%AD%90%EF%BC%89_assets/Pasted_20260607220901_SSD%20FAE%E5%B7%A5%E7%A8%8B%E5%B8%AB%EF%BC%88%E5%AE%8F%E8%8A%AF%E5%AE%87%E7%94%B5%E5%AD%90%EF%BC%89.png)