# A simple application of collecting spectra In LabVIEW. 在LabVIEW采集光谱信息，进行简单处理
---   
**摘要**：使用Ocean optics USB2000+的光谱卡以及积分球采集LED的光谱信息，并且获得其基本的光学参数：峰值及其波长、半宽，并储存到tdms文件，同时用一简单的MATLAB脚本进行滤波。  

---  
## 安装驱动
- VISA
- Drive驱动：
  - [驱动下载](http://sine.ni.com/apps/utf8/niid_web_display.download_page?p_id_guid=7833BD4A31DA1274E04400144FB7D21D)  
  - [帮助](https://knowledge.ni.com/KnowledgeArticleDetails?id=kA03q000000YIS2CAO&l=en-US)  
  <div align=center><img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/spectrum/driverINF.png" width="35%" height="35%"></div>
- 驱动安装后，连接USB2000+可以在NI MAX或LabView中看到。  

## 在Labview中使用例程即可获取光谱的显示图像
  <div align=center><img src="https://github.com/lin-tea/PMAC_LabView/blob/main/images/spectrum/exampleVI.png.jpg" width="45%" height="45%"></div>



