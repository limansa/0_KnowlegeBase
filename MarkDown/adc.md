# ADC driver design document


## 目錄結構
```mermaid
graph TD;
apps/examples/adc/adc_main.c
nuttx/drivers/analog/adc.c
nuttx/arch/arm/src/kinetis/hardware/kinetis_adc.h
nuttx/arch/arm/src/kinetis/kinetis_adc.c
nuttx/arch/arm/src/kinetis/kinetis_adc.h
boards/arm/kinetis/neo3-k81/src/k81_adc.c
```

## Entry code:
```mermaid

k81_adc_measure-->
```

k81_adc_initialize

# How to porting:
boards/arm/kinetis/neo3-k81/configs/vp3350evt/defconfig
boards/arm/kinetis/neo3-k81/include/board_vp3350.h

