# Machine-Learning
# 信用卡违约预测实验项目

## 项目概述

本项目旨在基于信用卡用户历史数据构建一个预测模型，用于识别可能违约的高风险用户。通过复现完整的机器学习工作流程，包括数据探索、特征工程和模型构建，帮助金融机构有效降低信用风险，优化风险管理策略。

## 环境

### 系统支持

- Windows: Windows 10/11
- Linux: Ubuntu 25.04, NixOS

### Python环境

- Python 3
- 主要库：
  - Pandas
  - NumPy
  - Matplotlib
  - Seaborn
  - Scikit-learn

## 环境搭建

### windows

系统：`windows10`, `windows11`
使用`anaconda`,库默认安装完成。

### linux

系统: `ubuntu25.04`, `nixos`

```bash
apt update -y
apt install gcc g++ build-essential

# 安装miniconda
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
sudo chmod +x bash ~/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.

# 创建虚拟环境ml，并指定python版本和安装相关库
conda create -n ml
conda install -n ml python=3.7
conda activate ml
conda install jupyter seaborn scikit-learn numpy pandas matplotlib
pip install imbalanced-learn==0.11.0
jupyter notebook
```

## 数据集

数据集`dataset-credit-default.csv`包含34个特征和6462条样本，主要包含以下类型的信息：

### 主要特征

- **用户基本信息**：性别、年龄、婚姻状态、教育程度、工作年限等
- **信用历史**：逾期账户数、逾期金额、逾期持续时间等
- **征信信息**：最大逾期金额、总逾期月数等（ZX_前缀特征）

### 目标变量

- `Target`：0表示未违约，1表示违约

## 数据分布

### 目标变量分布

| 类别     | 数量   | 比例    |
| ------ | ---- | ----- |
| 未违约(0) | 6341 | 98.1% |
| 违约(1)  | 121  | 1.9%  |

![目标变量分布](distribution.png)

> 数据存在严重不平衡问题，违约样本仅占总样本的1.9%

## 分析流程

1. **数据加载与探索**
   
   - 查看数据集结构和基本信息
   - 分析目标变量分布

2. **数据预处理**
   
   - 处理缺失值
   - 特征编码（分类变量转换）
   - 处理数据不平衡问题

3. **特征工程**
   
   - 特征相关性分析
   - 特征选择与转换
   - 创建新特征

4. **模型构建**
   
   - 数据集划分（训练集/测试集）
   - 使用多种算法：
     - 逻辑回归
     - 随机森林
     - XGBoost
     - 神经网络
   - 处理不平衡问题的方法：
     - SMOTE过采样
     - 类别权重调整

5. **模型评估**
   
   - 主要评估指标：
     - AUC-ROC曲线
     - F1分数
     - 召回率（特别关注违约类的识别能力）
   - 混淆矩阵分析
   - 特征重要性评估

6. **预期结果**
   
   - 最佳模型AUC-ROC > 0.85
   
   - 违约类召回率 > 0.75
   
   - 特征重要性分析报告
   
   - 模型部署准备文件

## 后续步骤

1. 深入探索特征间关系
2. 尝试不同的采样策略处理不平衡问题
3. 优化模型超参数
4. 部署最佳模型进行实时预测

## To do list

- 特征工程创新
- 模型性能优化
- 不平衡问题处理新方法
- 模型解释性分析

## 许可证

本项目采用MIT许可证

## 鸣谢

- 华为实验
