# Spectre 攻击报告
### 环境
- Ubuntu 7.2.0
- linux veision 4.13.0-38-generic
- gcc version 7.2.0

### 代码
来源论文部分已经标出,主要对论文代码的修改是部分参数

### 使用
```
make
spectre.out
```
然后就会输出被窃取的数据"Spectre attack by drdh"

也可以使用带参数的

### 原理
多次调用victim_function, 前5次为正确的范围，最后一次为攻击的目的地址，当CPU意识到需要回转到未执行分支的状态的时候，窃取的内容已经填充到了cache中，此时只需要比较时间，确定某个特定位置是否是hit来确定是否已窃取到值
