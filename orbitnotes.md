# 轨道学知识点总结

## 1 两行轨道要素 Two-line element set(TLE)
或三行，新轨道编码方式，给定时间（纪元），对轨道要素列表进行编码。
使用合适的预测公式，可以以一定的精度估计过去或未来任何点的状态（位置和速度）。
特定于简化扰动模型（SGP、SGP4、SDP4、SGP8 和 SDP8）
参见维基百科[两行轨道要素](https://en.wikipedia.org/wiki/Two-line_element_set "TLE")
以中国空间站TLE为例，自2023年2月12日起中国载入航天办公室每日都会更新中国空间站的TLE数据，可在<http://www.cmse.gov.cn/gfgg/zgkjzgdcs>查询到。大部分航天器的TLE数据可以在<https://www.space-track.org/>下载到（需先注册），Space-Track是由美国维护的公共数据库，用于跟踪所有在轨卫星和空间碎片。<https://celestrak.org/>网站也可以获取TLE数据。

### 1.1 轨道六根数与TLE的相互转换
待补充，csdn有付费C++源码 <https://download.csdn.net/download/weixin_42659194/86227380?utm_medium=distribute.pc_relevant_download.none-task-download-2~default~LANDING_RERANK~Rate-1-86227380-download-87228947.257%5Ev14%5Epc_dl_relevant_base1_b&depth_1-utm_source=distribute.pc_relevant_download.none-task-download-2~default~LANDING_RERANK~Rate-1-86227380-download-87228947.257%5Ev14%5Epc_dl_relevant_base1_b&spm=1003.2020.3001.6616.1>

### 1.2 STK导入TLE卫星数据
教程参见CSDN <https://blog.csdn.net/weixin_43475160/article/details/132609434?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171006448316800215011692%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171006448316800215011692&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-6-132609434-null-null.142^v99^pc_search_result_base1&utm_term=stk%E8%BD%A8%E9%81%93%E4%BB%BF%E7%9C%9F&spm=1018.2226.3001.4187>
内附数据提取，教程笔记。
#### 1.2.1 星链网站数据 celestrak
<https://celestrak.org/NORAD/elements/>
获取实时数据。（.txt）格式。

#### 1.2.2 数据导入STK流程（图片）
1. ![图1](https://img-blog.csdnimg.cn/f97ec456a723485b9422d4d1d974cd43.png "STK1")
打开STK
点击Create, 创建场景。时间区间选择自己想要的时间段，最好控制在前后一个月，卫星轨迹预报会更精确一些。
点击菜单栏的insert按钮，然后点击New按钮。
在Scenario Objects中选择Satellite，然后在右侧Select A Method中选择From TLE File，点击最下方的Insert按钮。弹出界面如下
![文件导入](https://img-blog.csdnimg.cn/0617e709c3434bec95aed5acef02b548.png)
选择刚才保存的TXT文件即可。

显示所有星链卫星的卫星轨道。

点击卫星，点击Ctrl+A。即可选中所有星链卫星数据 ![全选](https://img-blog.csdnimg.cn/5639819a1791463fad0d274756562407.png)
最后点击Insert，即可在场景中载入全部星链卫星数据，并实现二维与三维的可视化。结果如下： ![星链结果](https://img-blog.csdnimg.cn/ff7589b7e8754b32a9b3a2f1dba9690f.png)

#### 1.2.3 其他卫星设计
近地圆轨道、太阳同步轨道 设计
！[STK流程](https://blog.csdn.net/ltylty001/article/details/111997420?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_utm_term~default-4-111997420-blog-132609434.235^v43^pc_blog_bottom_relevance_base1&spm=1001.2101.3001.4242.3&utm_relevant_index=7)

matlab读取卫星数据，调用STK流程。
！[STK与matlab联用](https://blog.csdn.net/weixin_44323671/article/details/130545842?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-2-130545842-blog-132609434.235%5Ev43%5Epc_blog_bottom_relevance_base1&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-2-130545842-blog-132609434.235%5Ev43%5Epc_blog_bottom_relevance_base1&utm_relevant_index=5) 
![联用生成特殊轨道](https://blog.csdn.net/ltylty001/article/details/113946663?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-4-113946663-blog-130545842.235^v43^pc_blog_bottom_relevance_base1&spm=1001.2101.3001.4242.3&utm_relevant_index=7 "同步、闪电、冻结")

## 2 航航天器轨迹预测——根据速度和位置确定初轨
教程参考 ![预测流程](https://blog.csdn.net/Tang_Zhe/article/details/122128724 "csdn算法流程")