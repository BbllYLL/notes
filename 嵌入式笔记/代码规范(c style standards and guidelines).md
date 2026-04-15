#  本规范来自[C Style](https://syque.com/cstyle/)

# 1. 文件命名
## 1.1 总述

1. 1.文件名由层级 ___==(app/hal/drv/lib)==___ 模块文件名组成，需要全部小写，若有多个单词组成，使用下划线（）隔开。

2. 文件名要有描述性，少用缩写，如需使用请使用一些广为人知的缩写。

3. 单个文件不超过1000行，若超过1000行，需要给出合理解释。

## 1.2 说明

文件命名示例
``` C
hal_led.c

hal_bms_master.c

lib_commc.c

lib_nvm_core.c
```

# 2. 函数命名
## 2.1总述

1. 函数名由层级 ___==(App/Hal/Drv/Lib)==___ 模块文件+函数功能组成，使用首字母大写驼峰，文件模块与函数功能不需要使用下划线（）隔开。

2. 函数名要清晰、可读性，长度不超过40个英文字符。

3. 函数名长度组成：10：层级+模块名称、30：最长支持5个单词长度。

4. 函数功能名采用动宾结构： ___==SetXxx、GetXxx、XxxLoop、XxxInit==___ 等。

5. 单个函数不超过100行。

## 2.2 说明

函数命名示例
``` C
Hal_BmsMasterLoop();

Hal_ChgSetTgtVolt(); 

Drv_UartIntRxDis();
```

## 2.3 函数指针命名

函数指针由函数名_Fn组成。

函数指针命名示例
``` C
typedef void (*Drv_UartEnIrqTx_Fn)(void *private_data); 

typedef enum Vcp_IRQ_STS_T (*Drv_VcpGetIrqSts_Fn)(void *private_data); 

typedef uint8_t (*Drv_VcpRx_Fn)(void *private_data);
```

# 3. 结构体命名（struct）
## 3.1 总述

1. 结构体名由层级组成。

2. 使用全局结构，定义结构体需要加上typdef。

3. 定义的变量名使用首字母大写驼峰，物理单位使用下划线（_）隔开，不使用首字母大写驼峰，具体命名使用物理单位缩写表。

4. paramInfo调参表变量使用全大写，单词之间使用下划线（_）隔开。

## 3.2 说明

结构体命名示例：
``` C
typedef struct hal_chg_handle_t{
    uint8_t                 Switch;
    uint16_t                BatTgt_mV; 
    uint16_t                BatTgt_mA;
    int16_t                 Volt;
    int16_t                 Curr;
    uint16_t                Offs;
    uint16_t                PwmValue;
    HAL_CHG_PICURR_HANDLE_T CurrPI;
    HAL_CHG_PIVOLT_HANDLE_T VoltPI;
} HAL_CHG_HANDLE_T;
 
typedef struct drv_vcp_info_handle_t {
    Drv_VcpSend_Fn          Send;
    Drv_VcpRx_Fn            Rx;
    Drv_VcpGetIrqSts_Fn     GetIrqSts;
    Drv_VcpEnIrqTx_Fn       EnIrqTx;
    Drv_VcpEnIrqRx_F
} DRV_VCP_INFO_HANDLE_T
```

错误命名示例：
``` C
typedef struct Hal_Chg_Handle_t{        //这里为全小写不使用首字母大写驼峰
    uint8_t                 Switch;
    uint16_t                BatTgtmV;   //单位需要使用下划线隔开
    uint16_t                BatTgt_Ma;  //物理单位缩写错误
    int16_t                 Volt;
    int16_t                 Curr;
    uint16_t                Offs;
    uint16_t                PWMValue;   //首字母大写驼峰，不是全大写
    HAL_CHG_PICURR_HANDLE_T CurrPI;
    HAL_CHG_PIVOLT_HANDLE_T VoltPI;
} HAL_CHG_t;                            //_t需要大写，需要加HANDLE
```

# 4.联合命名（union）
## 4.1 总述

1. 联合体体名由 ___==层级(app/hal/drv/lib)_模块文件名_功能名(可选)_handle_t==___ 组成。

2. 使用全局结构，定义结构体需要加上typdef。

3. 定义的变量名使用首字母大写驼峰，如进行位操作则使用全大写，具体分情况定。

## 4.2 说明

union命名示例：
``` C
typedef union app_bms_reg_afe_flg2_handle_t
{
    struct
    {
        uint8_t UTC_FLG   : 1;
        uint8_t OTC_FLG   : 1;
        uint8_t UTD_FLG   : 1;
        uint8_t OTD_FLG   : 1;
        uint8_t VADC_FLG  : 1;
        uint8_t CADC_FLG  : 1;
        uint8_t WAKE_FLG  : 1;
        uint8_t RST_FLG   : 1;
    } Bit;
    uint8_t Val;
} APP_BMS_REG_AFE_FLG2_HANDLE_T
 
typedef union app_bms_reg_afe_flg_total_handle_t
{
    uint8_t Buf[2];
    struct
    {
        APP_BMS_REG_AFE_FLG1_T Flg1;
        APP_BMS_REG_AFE_FLG2_T Flg2;
    } Reg;
} APP_BMS_REG_AFE_FLG_TOTAL_HA
```

# 5.枚举命名(enum)
## 5.1 总述

1. 枚举名由层级(app/hal/drv/lib)_模块文件名_功能名(可选)_e组成。

2. 使用全局结构，定义枚举需要加上typdef。

3. 枚举变量名由 ___==层级(app/hal/drv/lib)模块文件名_功能名==___ 组成，使用全大写，单词之间使用下划线（）隔开。

## 5.2 说明

枚举命名示例：
```C
typedef enum drv_flash_status_e{
    DRV_FLASH_REST,
    DRV_FLASH_WRTIE,
    DRV_FLASH_ESARE
} DRV_FLASH_STATUS_E;
 
typedef enum drv_flash_bool_e{
    DRV_FLASH_FALSE = 0,
    DRV_FLASH_FALSE = 1
}DRV_FLASH_BOOL_E;
```

# 6.变量命名

## 6.1 全局变量总述

全局变量名由层级 ___==(App/Hal/Drv/Lib)_模块文件+功能==___ 组成，使用首字母大写驼峰。

全局变量命名示例：
```C
char Lib_CommcMasterSetFlag;

char Lib_CommcMasterGetFlag;
```

## 6.2 局部变量
### 总述

1.局部变量使用全小写，每个单词之间使用下划线（_）隔开。

2.静态局部变量统一修改为全局变量。

3.大括号中不能含有静态局部变量。

### 说明

局部变量命名示例：
```C
uint8_t Lib_CommcBufCopyBigEndian(const uint8_t *buf_src, uint8_t *buf_dest, uint8_t buf_len)
{
    uint16_t buf_offs = 0;
    for (buf_offs = 0; buf_offs < buf_len; buf_offs++) {
        *(buf_dest + buf_offs) = *(buf_src + buf_len - buf_offs - 1);
    }
    return 0;
}
```
错误命名示例：
```C
void func()
{
    static int a = 2;       // 不能定义静态局部变量，需定义为全局变量
    int b = 5;              // 局部变量
    a += 2;
    b += 5;
}
 
void func()
{   uint16_t i;
    for(i=1;i<10; i++)
    {
        uint16_t j;         //错误，应在函数开头定义，如uint16_t i。
        for(j=0; j<i; j++);
    }
}
```

# 7. 宏命名

## 7.1 总述

1.宏命名由 ___==DEF_层级(App/Hal/Drv/Lib)模块文件+功能==___ 组成，使用全大写，单词之间使用下划线（）隔开

2.宏单位使用全大写。

7.2 说明

宏命名示例：
``` C
#define DEF_APP_COMMC_EWP_HANDLER            0x14
 
#define DEF_APP_COMMC_EWP_MASTER_CTRL        0x15
```
