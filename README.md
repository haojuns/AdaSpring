# Enabling Resource-efficient AIoT System with Cross-level Optimization: A survey

> 深度学习驱动的移动应用通过模型压缩在资源有限的设备上本地部署，以实现稳健且私密的环境感知。然而，现有的DNN压缩技术要么手工设计以优化模型性能，要么按需压缩以优化硬件指标，但都无法在线运行且未考虑动态部署环境。为此，我们提出了AdaSpring，一个上下文自适应、自进化的DNN压缩框架，实现本地在线的自适应压缩。我们的研究成果《**[AdaSpring: Context-adaptive and Runtime-evolutionary Deep Model Compression for Mobile Applications](https://dl.acm.org/doi/10.1145/3448125)**》已发表在Proceedings of the ACM on Interactive, Mobile, Wearable and Ubiquitous Technologies。

---

## 1. 引用格式 📚

```bibtex
@article{liu2021adaspring,
  title={AdaSpring: Context-adaptive and runtime-evolutionary deep model compression for mobile applications},
  author={Liu, Sicong and Guo, Bin and Ma, Ke and Yu, Zhiwen and Du, Junzhao},
  journal={Proceedings of the ACM on Interactive, Mobile, Wearable and Ubiquitous Technologies},
  volume={5},
  number={1},
  pages={1--22},
  year={2021},
  publisher={ACM New York, NY, USA}
}
```

---

## 2. 问题 ❓

1. **动态调整压缩配置困难**：大多数DNN压缩方法无法逆向扩展，难以恢复原始架构和权重，并且受限于离线再训练，导致实时调整以满足多维度性能优化目标变得复杂。

2. **实时优化难度大**：要解决运行时优化，需要快速找到合适的压缩技术，并在不进行再训练的情况下有效调整权重，同时难以平衡多个性能指标（如延迟、存储和能效）之间的冲突。

---

## 3. 动机 🔍

1. **动态适应**：为解决DNN压缩难以动态调整的问题，需要开发无需离线再训练的灵活扩展方法，以实时满足精度、延迟、能耗等多维度性能需求。

2. **实时压缩**：针对运行时优化的复杂性，需研究快速压缩技术搜索与权重调整机制，平衡多项性能指标，提升DNN实际应用中的优化效率。

---

## 4. AdaSpring Workflow 🚀

'''


    def 主函数():
        # 步骤1: 用户输入
        模型 = 解析DL程序(DL程序)  # 解析用户提供的深度学习程序
        数据集 = 加载数据集()       # 加载AIoT数据集
        资源限制, 性能目标 = 获取用户要求()  # 获取资源限制和性能目标
    
        # 步骤2: 模型预训练
        训练后的模型 = 训练(模型, 数据集)  # 使用数据集对模型进行预训练
    
        # 步骤3: 分发模型到设备
        统一模型 = 转换为统一格式(训练后的模型)  # 将模型转换为统一格式
        分发到设备(统一模型, 设备列表)  # 将模型分发到各个AIoT设备
    
        # 步骤4: 模型压缩与推理
        for 设备 in 设备列表:
            压缩模型 = 应用压缩技术(统一模型, 设备)  # 选择并应用合适的模型压缩技术
            if 需要重训练(压缩模型):
                压缩模型 = 重训练(压缩模型, 数据集)  # 根据需要对模型进行重训练
            部署模型(压缩模型, 设备)  # 部署压缩后的模型到设备进行推理
    
        # 步骤5: 编译与硬件优化
        for 设备 in 设备列表:
            前端优化模型 = 前端编译优化(压缩模型)  # 进行平台无关的前端优化
            硬件优化模型 = 后端编译优化(前端优化模型, 设备)  # 进行平台相关的后端优化
            部署模型(硬件优化模型, 设备)  # 部署优化后的模型到设备
    
        # 步骤6: 检查是否需要重训练
        if 准确率下降(硬件优化模型):
            if 可在单设备上重训练(设备列表):
                更新模型 = 单设备重训练(硬件优化模型, 数据集)  # 在单个设备上进行重训练
            else:
                更新模型 = 分布式重训练(硬件优化模型, 数据集, 设备列表)  # 进行分布式重训练
        
        # 最终部署更新的模型
        最终部署(更新模型, 设备列表)
    
    主函数()
'''
---

## 5. 系统实用性 🔧




