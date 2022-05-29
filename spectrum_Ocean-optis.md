# A simple application of collecting spectra In LabVIEW. 在LabVIEW采集光谱信息，进行简单处理
---   
**摘要**：使用Ocean optics USB2000+的光谱卡以及积分球采集LED的光谱信息，并且获得其基本的光学参数：峰值及其波长、半宽，并储存到tdms文件，同时用一简单的MATLAB脚本进行滤波。 

**目录**：
- [安装驱动](#安装驱动)
- [例程](#在labview中使用例程即可获取光谱的显示图像)
- [峰值、波长、半宽](#峰值波长半宽)
- [滤波](#matlab-script-滤波)  

---  
## 安装驱动
- VISA
- Drive驱动：
  - [驱动下载](http://sine.ni.com/apps/utf8/niid_web_display.download_page?p_id_guid=7833BD4A31DA1274E04400144FB7D21D)  
  - [帮助](https://knowledge.ni.com/KnowledgeArticleDetails?id=kA03q000000YIS2CAO&l=en-US)  
  <div align=center><img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/spectrum/driverINF.png" width="35%" height="35%"></div>
- 驱动安装后，连接USB2000+可以在NI MAX或LabView中看到。  

## 在Labview中使用例程即可获取光谱的显示图像
  <div align=center><img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/spectrum/exampleVI.jpg" width="45%" height="45%"></div>

## 峰值波长半宽
- 峰值：峰值的获取是通过检索光强数组中的最大值。
  - 使用控件：`编程` -> `数组` -> `数组最大最小值`  
  
- 波长：依据检索到峰值，通过这个峰值检索波长数组中对应的下标。  
- 半宽：取峰值的一半，即半峰值，检索数组中最接近半峰的那个值，并由此检索其下标。用峰值对应的下标减去该值并取绝对值，再乘2即为半宽。  

## MATLAB Script 滤波
- 使用固定阈值的小波变化进行滤波，用MATLAB Script控件进行运行matlab脚本，注意要先安装MATLAB。  
<div align=center>
  <img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/spectrum/matlab.png" width="45%" height="45%"></div>
- 也许你会遇到 `0x147` 错误:原因是MATLAB没添加到环境 [解决办法](https://knowledge.ni.com/KnowledgeArticleDetails?id=kA00Z0000019Lk2SAE&l=zh-CN)  

## 最终程序框图
<div align=center>
  <img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/spectrum/spectrum.png" width="75%" height="70%"></div>  
  

 
