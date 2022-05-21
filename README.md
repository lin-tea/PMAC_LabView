# PMAC_LabView
我们可以在LabView中通过.AtiveX调用Pcomserver.dll动态链接库，从而与PMAC进行通讯、发送命令、下载文件。  
(Control PMAC in LabView! Connection, Jog and File-Download.)  

---  
目录:
- [AtiveX in LabView](#ativex-in-labview)  

---
## AtiveX in LabView
- **AtiveX**：面向对象程序技术、工具；
  - 主要技术:组件对象模型COM。提供在Win、Mac、Linux环境中都能运行使用的程序，能被大多数应用程序再使用，一个COM组件可以使用不同的开发工具进行开发如C#、C++、VB、Java。主要形式即为动态链接库(DLL)。ActiveX控件一旦被开发出来，设计和开发人员就可以把它当作预装配组件，用于开发客户程序。
  - LabVIEW提供Active控件，可以嵌入ActiveX 控制，使用控件的属性和方法， 与其进行交互。
  - 参考官方[ActiveX and LabVIEW](https://www.ni.com/zh-cn/innovations/white-papers/06/activex-and-labview.html#section-500257886)  
如下图我们可以在程序面板，用`函数`->`互连接口`->`.AtiveX`->`打开自动化`连接COM组件：
