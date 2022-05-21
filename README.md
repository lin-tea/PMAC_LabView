# PMAC_LabView
我们可以在LabView中通过.AtiveX调用Pcomserver.dll动态链接库，从而与PMAC进行通讯、发送命令、下载文件。  
(Control PMAC in LabView! Connection, Jog and File-Download.)  

---  
目录:
- [AtiveX in LabView](#ativex-in-labview)  
- [调用Pcomserver.dll](#调用pcomserver) 
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
