# Modle-Code
## 搭建模型的模板中，出现的语法问题和会导致的后果

### 语法问题
```python
class xxxNet ( nn . Module ):
 def _ init _( self )：
 pasS 
 def forward ( x ):
 return x 
```
1、在 _init_ 方法中，_ 应该是双下划线，表示这是一个特殊方法，用于初始化对象的属性。因此应该改为 __init__。

2、在 forward 方法中，缺少 self 参数，应该将 def forward(x): 改为 def forward(self, x):。

### 导致的后果



## ResNet34 模型代码注释
