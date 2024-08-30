# Windows下常用的嵌入式工具
|名字|版本|下载地址|
|:-|:-|:-|
|make||
|CMake||
|gcc||
|LLVM||
|arm-none-aebi-gcc||
|OpenOCD|0.12.0|[参考链接1](https://www.cnblogs.com/wanower/articles/17653065.html)|
|niaja||
|git||
|tree||[参考文档](https://www.cnblogs.com/ricolee/p/cmd-tree.html)|

## OpenOCD
- 添加到环境变量(`D:\Program Files\OpenOCD-20230712-0.12.0/bin`)
- `openocd -version` 查看版本号
### 使用OpenOCD下载
- 获取对应下载器(STLink-v3,-v2.1-v2)的配置文件
    - 目录:`OpenOCD-20230712-0.12.0\share\openocd\scripts\interface`
- 获取芯片(STM32G4/STM32F4)的配置文件
    - 目录:`OpenOCD-20230712-0.12.0\share\openocd\scripts\target`
- 移动文件至工程目录下，同makefile在同一级目录
- makefile文件修改
```
stlinkdown:
	openocd -f stlink.cfg -f stm32g4x.cfg -c "init" -c "reset halt" -c \
	"flash write_image erase $(BUILD_DIR)/$(TARGET).hex" -c reset -c shutdown
```
### OpenOCD常用命令
`-f`指定文件
`-c`指定命令



