#### 期刊要求
利用机器学习解决工程应用中的问题，包括能源、运输和医疗等等。
#### 论文题目
节能的虚拟网络嵌入：基于图卷积网络的深度强化学习方法
#### 问题
##### 目前大部分节能的VNE算法采用的启发式的（元启发式解决方案通常遵循由专门的人类经验手动设计的静态改进步骤（不灵活）。）
- "Virtual network mapping considering energy consumption and availability"考虑了同时考虑虚拟网络嵌入问题能耗和可用性约束的问题公式，并采用了一种基于贪婪随机自适应搜索程序（GRASP）元启发式的算法。并利用基于可靠性框图（RBD）和随机Petri网（SPN）的模型来估计可用性。但是其中局部最优问题和算法性能问题并没有得到解决
- "Energy efficiency with service availability guarantee for Network Function Virtualization"将所研究的问题表述为ILP模型，并证明了问题的NP硬度。由于所研究的问题是NP困难的，我们提出了一种基于拉格朗日松弛技术的高效启发式算法。但是局部最优问题任然没有得到解决
##### 大部分算法不能高效率的获取网络的空间特征
- "A Q-learningbased approach for virtual network embedding in data center"使用Q学习算法，设计了一个与虚拟链接嵌入效果相关的奖励函数，并应用无监督学习对其进行更新。然而，在这个算法中特征是手动获得的。
- "Nfvdeep: Adaptive online service function chain deployment with deep reinforcement learning"使用基于深度RL的模型来制定服务功能链的自动部署问题，并采用基于策略梯度的方法来提高训练效率和收敛到最优。不幸的是，他们没有考虑到空间特征。
##### 目前的节能VNE算法主要是基于当前网络状态提出节能方案（没有考虑网络的周期性波动）
- "Realization of congestion-aware energy-aware virtual link embedding"提出了一种涉及两阶段协调CEVNE的启发式解决方案。节点映射算法搜索三个目标（节省成本、节约能源又能同时避免网络拥塞的）的次优解。链路映射过程是一种基于SDN的启发式算法，用于在 SDN 控制器上部署路径服务和资源监视应用程序。该方法通过找出同时满足五种规则约束规则的路径来满足三个目标。但是，该方法的输入是当前状态的两个端点，并没有考虑网络流量的周期波动。
- "DEVINE: Distributed Energy-related Virtual Network Embedding Approach utilizing Multiple Objective Optimization"提出的VNE算法试图优化成本和能源，并提供避免网络拥塞的次优解决方案。这种方法通过手动提取当前网络特征，并且使用线性规划的方式求解，没有考虑网络流量的周期性波动。
#### 解决方案
- 使用基于深度强化学习的VNE算法解决启发式算法的局部最优等问题
- 将图卷积网络（GCN）作为特征提取器去平衡其它算法对于图结构的特征提取的低效率。
- 模拟流量的周期性特征，并且使用GCN提取网络流量的周期特征。以此作为约束，对VNR做出具有预测性的嵌入。
