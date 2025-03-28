# 肌疲劳鲁棒的动作识别方法研究
引用自[肌疲劳鲁棒的动作识别方法研究](https://wap.cnki.net/touch/web/Dissertation/Article/10618-1024511656.nh.html)
## 解决的问题
***肌肉疲劳***的产生使肌电信号在动态范围发生幅值和分布等改变,从而导致基于表面肌电信号的***动作识别准确率下降***,***泛化性变差***,难以为人机交互提供安全、实时的控制策略
## 研究内容
(1)开展***肌电信号采集***与***多重滤波去噪***方法研究  
(2)开展具备肌疲劳鲁棒性及动作可分性的***肌电特征***研究  
(3)开展肌疲劳鲁棒的***对抗域适应动作识别***方法研究  
(4)开展与其他特征分析方法及其他动作识别方法的***对照实验***研究  
## 如何解决该问题
---
针对内容(1),提出一种基于***综合得分准则的变分模态分解联合小波阈值的肌电信号多重滤波***方法。  
- 首先，***采集***受试者肌肉疲劳前后的肌电信号，通过***模态分量的最大中心频率变化趋势***确定变分模态分解的***最佳分解层数***范围，并引入相关系数、峭度和样本熵的概念构建综合得分准则筛选含噪分量  
- 最后，经过***小波阈值***进行信号去噪。

针对内容(2),构建一种具有良好肌疲劳鲁棒性和动作可分性的特征集合。  
- 首先，观察特征在***肌疲劳前后的幅值与分布变化***  
- 其次，设计不同情景下的动作分类实验，以肌疲劳鲁棒性、动作可分性强为指标，通过***典型机器学习模型***，结合***统计学方法***和***斯皮尔曼相关系数***，从***时域、频域、时频域***以及***非线性特征***中综合分析肌电特征的性能，获得对肌疲劳鲁棒、可分性强且特征冗余程度低的特征集合，为肌疲劳鲁棒的动作识别方法奠定基础

针对内容(3)，对***肌疲劳前后数据分布差异大***和***标签不平衡***导致的动作***识别模型分类精度下降***、***泛化性变差***的问题，提出一种肌疲劳鲁棒的对抗域适应动作识别方法  
- 首先，通过***引入域适应***的思想，构建***通道注意力机制联合卷积神经网络***和***门控循环单元***作为特征提取器，提取域不变特征  
- 其次，结合***多核最大均值差异***和***域对抗***的方法，解决肌疲劳前后数据分布差异和标签不平衡的问题  
- 最后，经过实测数据实验，实验结果表明所提出的模型能显著提高肌疲劳下的动作分类精度

针对内容(4)，开展与其他特征分析方法及其他动作识别方法的对照实验研究  
- 首先，进行传统的基于主成分分析的特征降维动作识别方法对比实验  
- 其次，构建基于多尺度卷积的能量生成对抗网络，从疲劳数据扩充模型训练集出发，进行数据增强的动作识别方法对比实验
## 实验过程
### 肌电信号采集及多重滤波去噪方法研究
#### 引言  
肌肉疲劳将导致 sEMG 在时域上出现信号的幅值增加，在频域上出现信号向低频移动等现象
#### 流程
##### 信号采集
- 采集设备的选择：意大利 OT Bioeletronica s.n.c 公司的可穿戴式无线肌电采集系统。如下图  
![1](https://github.com/user-attachments/assets/5bc267cd-cce7-47e2-8189-28c51e020470)
- 采集动作及对应肌肉选择：选择了爬坡、平地行走、上楼、下楼四种动作模式，其图和肌肉选择图如下
![2](https://github.com/user-attachments/assets/75650da4-b5c9-4164-8649-a04571a4d2bf)
![3](https://github.com/user-attachments/assets/e2261d78-192b-43ae-b92f-e5091d114d65)
![4](https://github.com/user-attachments/assets/acb562e1-ca5b-4a85-83cc-22a4ce0174e1)
- 采集到的数据如下
![5](https://github.com/user-attachments/assets/36147a4f-7bfd-4eb2-9da3-79eae23d8f85)
![6](https://github.com/user-attachments/assets/3eb7dddb-8abd-4f91-89aa-aa36bfcd0af4)
##### 信号预处理：基于改进变分模态分解联合小波阈值的多重滤波方法
- 原始信号含噪成分  
(1)仪器及环境固有噪声  
(2)移动伪迹干扰（基线干扰）  
(3)个人内部因素
- 滤波流程图
![7](https://github.com/user-attachments/assets/256a3849-04b3-4dc0-b42a-0fefd7d3bc30)
- 巴特沃斯滤波器与陷波器的设计  
一堆公式我也看不懂  
- 基于综合得分准则的变分模态分解联合小波阈值去噪方法  
同上
##### 实验效果
![8](https://github.com/user-attachments/assets/01797f1f-68e5-49dd-8fc2-e7d90e155503)
### 肌疲劳鲁棒及动作可分性肌电特征研究
#### 引言
本章则针对肌肉疲劳致使***肌电特征产生变化***，从而导致动作识别***模型的分类精度下降***和***泛化性变差***的问题而展开研究，旨在构建一种对肌疲劳鲁棒和动作可分性高的特征集合  
肌疲劳鲁棒性及可分性特征分析方法:（1）SVM（2）DT（3）LDA（4）KNN
##### 时间窗口分割
![1](https://github.com/user-attachments/assets/66eedfa4-8647-4b99-a644-fe87d7134d77)
##### 时域特征
（1）绝对平均值（Mean Absolute Value，MAV）：其反映了一段时间内肌肉作用的强度大小  
（2）均方根值（Root Mean Square，RMS）：能够代表 sEMG 的有效值，体现运动过程中各肌肉的贡献程度  
（3）方差（Variance，VAR）：方差反应 sEMG 幅值的变化程度  
（4）过零点数（Zero Crossing，ZC）：在不同的动作模式下，sEMG 信号的波动情况有所不同，而波动的剧烈程度可用 sEMG 经过零点的次数即过零点数来表示  
（5）积分肌电值（Integrated EMG，IEMG）：反映了肌肉活动的强弱，其值越大，肌肉的活动程度越高  
（6）波长（Waveform Length，WL）：反映 sEMG 的振幅和波动频率信息  
（7）斜率符号变化次数（Slope Sign Change，SSC）：反映 sEMG 的变化程度  
##### 频域特征
（1）平均功率频率（Mean Power Frequency，MPF）：反应了肌肉活动的整体水平  
（2）中值频率（Median Frequency，MF）：体现肌肉活动的平均水平  
（3）功率谱最大值（Maximum Power Spectral，MPS）：MPS 反映了肌肉活动的强度，强度越大，则对应 MPS 的值越高  
（4）重心频率（Centroid Frequency，CF）：CF 反应了频谱的集中程度和整体位置  
##### 时频域特征
本文选择提取基于小波包变换的时频域特征  
![2](https://github.com/user-attachments/assets/75bb78b9-fd95-4196-8e74-f7d0c669a495)
#### 非线性动力学特征
本文针对模糊熵（FE）和排列熵（PE）展开相关非线性特征分析
##### 特征可视化
本文采用 t 分布随机领域嵌入[69]（t-distributed Stochastic Neighbor Embedding，t-SNE）对肌肉疲劳前后的特征进行可视化分析，观察其分布变化情况
##### 实验效果
![3](https://github.com/user-attachments/assets/9a752a64-1c18-440c-8a9c-fa1f17af3ff8)
![4](https://github.com/user-attachments/assets/1ee2a0e7-5edc-4d04-bf09-e1b4e0a69e87)
![5](https://github.com/user-attachments/assets/eaeda01c-145c-4b9c-862f-b122aefa29e7)
![6](https://github.com/user-attachments/assets/f319a2f7-dcd3-4ec4-94df-3f1c04fab716)
![7](https://github.com/user-attachments/assets/080d0559-8a66-404a-a316-07e723afa09a)
![8](https://github.com/user-attachments/assets/5d8ee99e-a82a-4b98-acd4-3c08782f37f6)
![9](https://github.com/user-attachments/assets/302483c3-d35e-4930-81b3-800638de0d90)
### 肌疲劳鲁棒的对抗域适应动作识别方法研究
针对肌肉疲劳前后出现的数据分布差异大和标签不平衡的问题，提出一种肌疲劳鲁棒的对抗域适应动作识别方法
- 融合注意力机制的 CNN-GRU 特征提取
- 肌疲劳鲁棒的对抗域适应模型结构
![10](https://github.com/user-attachments/assets/e823b1a8-b3d3-4270-a221-d2b9d0b82f93)
![11](https://github.com/user-attachments/assets/4ff6e60f-87dc-452e-afc6-1c390561e101)
### 其余略









