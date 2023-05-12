# Modle-Code
## 搭建模型的模板中，出现的语法问题和会导致的后果

### 语法问题
```python
import torch 
import torch . nn as nn 
import torch . nn . functional as F  
class xxxNet ( nn . Module ):
    def _ init _( self )：
        pass
    def forward ( x ):
        return x 
```
1、在 ``` _init_``` 方法中，_ 应该是双下划线，表示这是一个特殊方法，用于初始化对象的属性。因此应该改为 ```__init__```。

2、在 forward 方法中，缺少 self 参数，应该将 ```def forward(x): ```改为 ```def forward(self, x):```。

### 导致的后果
这两个语法问题都会导致程序出现语法错误，无法正常运行。在这个例子中，由于模型没有被正确定义，因此无法使用该模型进行训练或推理。

1、当我们创建对象时，__init__ 方法不会被调用，而是会调用默认的构造方法，也就是一个空方法。这会导致对象的属性没有被正确初始化，可能会导致程序出现错误。

## ResNet34 模型代码注释
