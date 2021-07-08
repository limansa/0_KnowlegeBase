[TOC]

## Get Start

- Install markdown-extension-pack
  ext install doggy8088.markdown-extension-pack

## 基本語法
- Install markdown-extension-pack in Vscode
- 這個是<br />強制斷行
- Markdown 透過簡單的排版做出文件 沒有顏色
- Markdown允許你用html tag

## 程式碼區塊
- 注意結尾要空白 內嵌define前的#要有空白
```c++{.line-numbers}
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

## 清單
- 階層一
  - 階層二
    - 階層三
1. Toggle list 1
1. To do list
2. 至少
- [ ] checklist 1
- [ ] Checklist 2
- [x] Alt+C auto V

## 表格
| Column 1 | Column 2 | Column 3 |
| -------- | -------- | -------- |
| Text     | Text     | Text     |

## 字型
**粗體**

## 分隔線
***
---

## 引言
> 多層引言
>> Makrdown是工程師的浪漫
>>> 學著`快速`寫寫文件

## Insert code
```C
#include <stio.h>
int main()
{
	return 0;
}
```

## 插入超連結和文字
- Step
  1. 複製連結
  2. 選取文字
  3. Ctrl+V
### 超連結
[Markdown](https://marketplace.visualstudio.com/items?itemName=doggy8088.markdown-extension-pack)

### 貼圖
![Markdown picture](https://doggy8088.gallerycdn.vsassets.io/extensions/doggy8088/markdown-extension-pack/0.4.0/1623816281527/Microsoft.VisualStudio.Services.Icons.Default)

- 複製圖片到本地 加到文件
Ctrl + Alt + V
 ![](res/2021-06-23-23-07-47.png)
