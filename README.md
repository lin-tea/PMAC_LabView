# PMAC_LabView
我们可以在LabView中通过.AtiveX调用Pcomserver.dll动态链接库，从而与PMAC进行通讯、发送命令、下载文件。  
(Control PMAC in LabView! Connection, Jog and File-Download.)  

---  
目录:
- [AtiveX in LabView](#ativex-in-labview)  
- [调用Pcomserver.dll](#调用pcomserver) 
- [通讯](#通讯)
- [PMAC基本实时执行命令](#pmac基本实时执行命令)
- [Jog实现](#jog实现)  

---
## AtiveX in LabView
- **AtiveX**：面向对象程序技术、工具；
  - 主要技术:组件对象模型COM。提供在Win、Mac、Linux环境中都能运行使用的程序，能被大多数应用程序再使用，一个COM组件可以使用不同的开发工具进行开发如C#、C++、VB、Java。主要形式即为动态链接库(DLL)。ActiveX控件一旦被开发出来，设计和开发人员就可以把它当作预装配组件，用于开发客户程序。
  - LabVIEW提供Active控件，可以嵌入ActiveX 控制，使用控件的属性和方法， 与其进行交互。
  - 参考官方[ActiveX and LabVIEW](https://www.ni.com/zh-cn/innovations/white-papers/06/activex-and-labview.html#section-500257886)  
如下图我们可以在程序面板，用`函数`->`互连接口`->`.AtiveX`->`打开自动化`连接COM组件：
<div align=center><img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/ativeX.png" width="75%" height="75%"></div>

## 调用Pcomserver
- 使用`打开自动化`控件，选择AtiveX类，并且选择Pcomserver
<div align=center><img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/chooseCOM.png" width="30%" height="30%"> <img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/choosePcom.png" width="55%" height="55%"></div>  

- 使用函数->`编程`->`应用程序控制`->`调用节点`：使用COM中的函数，如下，选择*SelectDevice()* 选择PMAC卡通讯连接方式，得到PMAC卡号。

<div align=center><img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/funcCall.png" width="35%" height="35%"> <img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/selectDev.png" width="40%" height="40%"></div>  

- 对于函数的使用，参考[使用手册](https://github.com/lin-tea/PMAC_LabView/blob/main/Sources/PcommServer%20Library%20of%20PMAC%20Functions%20.pdf)

- **主要函数使用**:

  |函数|功能|手册页数|
  |---|---|---|
  |SelectDevice()|选择PMAC卡|p38|
  |Open()|连接PMAC卡|p39|
  |**GetResponseEx()**|发送命令到PMAC卡|p41|

## 通讯
- 使用函数 `SelectDevice` 选择PMAC卡，用得到的PMAC卡号通过 `Open` 函数进行连接。(参考使用手册的38页，以及在LabView中的调用控件，我们可以获取函数的使用方式)，最终通讯程序框图如下：  
<div align=center><img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/connectPMAC.png" width="100%" height="75%"></div>  

触发连接，会弹出一以下界面，选择连接方式进行连接，(连接成功后，得到的连接状态为: True):

<div align=center><img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/connectPMAC2.png" width="30%" height="30%"></div>   

## PMAC基本实时执行命令  
  |命令|功能|
  |---|---|
  |#nj+|正向连续点动|
  |#nj-|反向连续点动|
  |#nj/|停止、闭环|
  |#nj={*C*}|到C位置,单位脉冲|
  |#nj^{*C*}|运动C个脉冲|
  |#nP|获取位置，单位脉冲|
  |#nHOMEZ|置当前位置为0点|  
  
其中(n表示电机号，C表示常数)
## Jog实现
- **Jog功能**：电机正向、反向点动、移动到某位置、移动一定步长。
  - **思路**：使用事件结构，在循环中添加事件处理分支处理按钮按下、松开。
  - **正向点动示例**：
<div align=center><img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/plusDotMove.png" width="35%" height="35%"></div>  
 
  最终实现功能:

  <div align=center><img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/Jog.png" width="45%" height="45%"></div>   
  
  单步点动为True,则按下按钮只会移动相应步长。
  - (注意)：
    - 循环中，一定要事件触发才会进行下一次执行；
    - 按钮的机械动作与触发事件相匹配。；
    - 当有事件结构时，文本框的改变也需要作为事件触发，更新文本框。  
   
## 位置读取
- 思路同上，使用 `GetResponseEx()` 函数；用一个定时循环，定时采集位置，进行显示。

<div align=center>
  <img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/posVI.png" width="25%" height="25%">  <img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/readPosition.png" width="50%" height="50%">
</div>   


## 文件下载
- 使用函数 `Download()` 函数

<div align=center>
  <img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/fileDownload.png" width="10%" height="10%">
</div>  

---
## Reference  
[1]  [避免在同一个循环中放置两个事件结构](https://zone.ni.com/reference/zhs-XX/help/371361R-0118/lvhowto/twoevntstrctonelp/)  
