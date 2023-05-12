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

1、当我们创建对象时，```__init__``` 方法不会被调用，而是会调用默认的构造方法，也就是一个空方法。这会导致对象的属性没有被正确初始化，可能会导致程序出现错误。

2、在 forward 方法中缺少 self 参数会导致无法访问当前实例的属性和方法，从而导致运行时错误。因为 forward 方法是类的实例方法，需要通过实例来调用，而缺少 self 参数则无法访问当前实例。

### 正确的写法
```python
import torch 
import torch . nn as nn 
import torch . nn . functional as F  
class xxxNet ( nn . Module ):
    def__init__( self )：
        pass
    def forward ( self,x ):
        return x 
```

## ResNet34 模型代码注释






## 对ResNet模型进行打断点调试
在```x = self.maxpooling(x)```处打断点的调试结果

![image](https://github.com/lichunying20/Modle-Code/assets/128216499/1c0d0af1-85aa-48c9-a948-5fb1c0931be4)

在```x = self.layer1(x)```处打断点的调试结果
 
![image](https://github.com/lichunying20/Modle-Code/assets/128216499/43838797-1b5f-46ca-b6c5-689be2e54fb1)

在```x = self.layer2(x)```处打断点的调试结果

![image](https://github.com/lichunying20/Modle-Code/assets/128216499/32ef907a-5466-49e3-9933-5c59f804d806)

在```x = self.layer3(x)```处打断点的调试结果

![image](https://github.com/lichunying20/Modle-Code/assets/128216499/8248c5be-1246-49f0-8a20-2fa47440d11d)

在```x = self.layer4(x)```处打断点的调试结果

![image](https://github.com/lichunying20/Modle-Code/assets/128216499/bf5769ef-3472-4768-854c-12c376b8a1ac)

在```x = self.avgpooling(x)```处打断点的调试结果
       
![image](https://github.com/lichunying20/Modle-Code/assets/128216499/bccbd72d-2d11-4ef0-b79f-934209e96f97)

在```x = x.view(x.shape[0], -1)```处打断点的调试结果 
 
 
在```x = self.classifier(x)```处打断点的调试结果


在```output = F.softmax(x)```处打断点的调试结果


## 了解ResNet34模型和ResNet32模型
### ResNet34模型
ResNet34是一个深度卷积神经网络，其结构基于残差学习的思想。与ResNet32相比，ResNet34在网络深度上更深，包含34个卷积层。

ResNet34同样采用残差块来解决深度神经网络中梯度消失和梯度爆炸的问题，同时也增强了模型的表达能力和泛化能力。与ResNet32不同的是，ResNet34采用了更多的残差块来增加网络深度，从而提高模型的性能。

具体来说，ResNet34包含了3个卷积块和16个残差块。每个卷积块包含两个卷积层和一个批量归一化层，每个残差块由两个卷积层、两个批量归一化层以及一个跨层连接组成。最后，ResNet34通过全局平均池化层和softmax分类器实现对输入图像的分类。

总的来说，ResNet34是一个更深、更强大的深度神经网络模型，能够在图像分类、目标检测等任务中取得更好的性能。

### ResNet32模型
ResNet32是一个深度卷积神经网络，其结构基于残差学习的思想。在传统的深度神经网络中，随着层数的增加，模型的性能往往会出现退化现象，即模型的精度无法继续提升，反而会出现下降的情况。这是因为在深度网络中，信息传递过程中会出现梯度消失或梯度爆炸等问题，导致模型无法很好地拟合训练数据。

ResNet32通过引入残差块（residual block）来解决这个问题。残差块包含了跨层连接（shortcut connection），使得信息可以直接从输入层传递到输出层，避免了信息在传递过程中的损失。同时，残差块还包含了两个卷积层和批量归一化层，可以有效地增强模型的表达能力和泛化能力。

ResNet32的具体结构包含32个卷积层，其中包括3个卷积块（convolutional block）和9个残差块（residual block）。每个卷积块包含两个卷积层和一个批量归一化层，而每个残差块由两个卷积层、两个批量归一化层以及一个跨层连接组成。最后，ResNet32通过全局平均池化层和softmax分类器实现对输入图像的分类。

总的来说，ResNet32是一个非常强大的深度神经网络模型，能够在图像分类、目标检测等任务中取得很好的性能。





