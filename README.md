# AdaSpring: Context-adaptive and Runtime-evolutionary Deep Model Compression for Mobile Applications

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

——系统创新性：AdaSpring是一个设计用于动态优化DNN模型在移动平台上运行性能的框架。系统包含两个创新设计的模块：

1. **自进化网络**：由一个骨干网络和多个无需重训练的压缩算子变体组成。骨干网的超参数在设计时通过按需生成的DNN框架初始化，以满足目标平台上移动应用的性能需求。

2. **运行时自适应压缩**：系统能在运行时自动选择最优压缩操作符组合，动态调整骨干网架构，以适应实时变化的性能需求。

在系统运行时，模块能够持续检测部署环境的变化，触发运行时自适应压缩，确保应用在动态环境中保持最佳性能。

——运行流程：

    # Initialize the AdaSpring framework
    AdaSpring:
        initialize BackboneNet using AdaDeep
        initialize CompressionOperators from Δ
        initialize DynamicContextAwarenessBlock
    
    # Main execution loop for continuously running apps
    while app_is_running:
        # Detect context changes
        context = DynamicContextAwarenessBlock.detect_changes()
    
        # Check if the context triggers reconfiguration
        if context.requires_evolution():
            # Select the optimal compression operators
            optimal_operators = RuntimeAdaptiveCompressionBlock.select_optimal_operators(Δ, context)
    
            # Reconfigure the backbone network using selected operators
            BackboneNet = self_evolutionary_network.reconfigure(optimal_operators)
    
        # Execute the DNN model with the current configuration
        results = BackboneNet.run_inference()
    
        # Evaluate the performance metrics
        accuracy, latency, energy_efficiency = evaluate_performance(results)
    
        # Log or adjust based on performance
        log_performance(accuracy, latency, energy_efficiency)
        adjust_importance_coefficients(accuracy, energy_efficiency)
    
    # Supporting functions
    def evaluate_performance(results):
        # Calculate performance metrics
        accuracy = measure_accuracy(results)
        latency = measure_latency(results)
        energy_efficiency = measure_energy_consumption(results)
        return accuracy, latency, energy_efficiency
    
    def adjust_importance_coefficients(accuracy, energy_efficiency):
        # Dynamically adjust importance coefficients λ1 and λ2 based on current context
        λ1 = adjust_λ1(accuracy)
        λ2 = adjust_λ2(energy_efficiency)
        return λ1, λ2


---

## 5. 系统实用性 🔧

AdaSpring在多种动态环境下的应用场景中具有重要价值，尤其适用于需要持续运行并动态调整性能的移动应用。例如，在实时视频处理、连续图像识别、增强现实（AR）、智能传感器数据分析、和移动健康监测等场景中，设备资源和环境条件（如电池电量、网络状况、计算资源）经常发生变化。AdaSpring能够根据这些变化，自动调整DNN模型的精度、延迟和能效，确保应用在不同条件下都能高效运行，提升用户体验、减少功耗并延长设备续航时间，从而在移动设备上提供更为智能和自适应的解决方案。


