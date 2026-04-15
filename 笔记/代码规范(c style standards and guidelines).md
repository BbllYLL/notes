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

1. 结构体名由层级(app/hal/drv/lib)_模块文件名_功能名(可选)_handle_t组成。

2. 使用全局结构，定义结构体需要加上typdef。

3. 定义的变量名使用首字母大写驼峰，物理单位使用下划线（_）隔开，不使用首字母大写驼峰，具体命名使用物理单位缩写表。

4. paramInfo调参表变量使用全大写，单词之间使用下划线（_）隔开。