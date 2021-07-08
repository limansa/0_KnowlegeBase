[TOC]

## 目錄結構
apps/examples/adc/adc_main.c

nuttx/drivers/analog/adc.c

nuttx/arch/arm/src/kinetis/hardware/kinetis_adc.h
nuttx/arch/arm/src/kinetis/kinetis_adc.c
nuttx/arch/arm/src/kinetis/kinetis_adc.h

boards/arm/kinetis/neo3-k81/src/k81_adc.c

> boards / (arch) / (chip) / (board)
> (arch) : CPU architeture like arm
> (chip) : MCU chip architecture like kinetis
> (board): Bord design like neo3-k81

## Entry code:
```Mermaid
graph TD
k81_adc_initialize-->T3[Register /dev/adc0]-->adc_reset-->T1[Configure system Gating control]-->adc_calibrate_Params --> T2[config gpio]
```

 ```Mermaid
graph TD
k81_adc_measure-->

```

## How to porting:
- boards/arm/kinetis/neo3-k81/configs/vp3350evt/defconfig
```c{.line-numbers}
CONFIG_KINETIS_ADC0=y
CONFIG_KINETIS_ADC=y
CONFIG_ANALOG=y
CONFIG_ADC=y
 ```
- boards/arm/kinetis/neo3-k81/include/board_vp3350.h
```c{.line-numbers}
  #define BOARD_ADC0_NCHANNELS 4
  #define GPIO_ADC0_CH4OUT    PIN_ADC0_SE4B  // PTC2  ALT0
  #define GPIO_ADC0_CH8OUT    PIN_ADC0_SE8   // PTB0  ALT0
  #define GPIO_ADC0_CH9OUT    PIN_ADC0_SE9   // PTB1  ALT0
  #define GPIO_ADC0_CH14OUT   PIN_ADC0_SE14  // PTC0  ALT0

  #define ADC_ID_HW_ID        0              // PIN_ADC0_SE4B
  #define ADC_ID_USB_C_CC1    1              // PIN_ADC0_SE8
  #define ADC_ID_USB_C_CC2    2              // PIN_ADC0_SE9
  #define ADC_ID_BATT_TEMP    3              // PIN_ADC0_SE14
 ```

## Test method
1. make menuconfig
[*] ADC example
(/dev/adc0) ADC device path
(7)   Number of Sample Groups
(1)   Number of Samples per Group

## Question:
- 使用enter critial section的時機
irqstate_t flags;
flags = enter_critical_section();
leave_critical_section(flags);
    - kinetis_adc_measure
    - get_bandgap_vref enable and disable

- Warning: Spec said config HW Average should before auto calibration
  adc_modifyreg(priv, KINETIS_ADC_SC3_OFFSET, 0, ADC_SC3_AVGS_32SMPLS | ADC_SC3_AVGE);
也許拿 新版的K81 Sub-Family Reference Manual, Rev. 4, 09/2015
or NXP default sdk
- Porting的方法 每個project用的adc channel都不太一樣