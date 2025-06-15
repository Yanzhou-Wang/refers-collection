# I. refers-collection
## II. Structural forms of disordered carbon
- `zhu2024_aC-discontinous-phase-diagram.pdf`, Zhu, YinBo, et al. "Discontinuous phase diagram of amorphous carbons." National Science Review 11.4 (2024): nwae051. ||首次归纳出了无序碳结构存在的6种相，并以sp3/sp2-density二维坐标面的形式首次绘制了它们的非连续相图。|| 以DGN为前驱体，采用"快速升温(4000K)-恒温弛豫-升压(20, 40GPa)-恒压弛豫"的温度协议，得到Fig. 1中6种 (包括前驱体DGN）代表性结构。Fig. 1(b-c)是P=20 GPa所得；Fig. 1d-f是高压P=40GPa所得。|| Fig. 3以sp3/sp2-density二维坐标面，展示了这6种结构的非连续相图 ||Fig. 2给出了这些相的xrd和structure factor结构表征。
- `zhang2023nanoletter_paracrystalline-nucleation-in-disordered-diamonds.pdf`, Zhang, ZhongTing, et al. "Temperature-dependent paracrystalline nucleation in atomically disordered diamonds." Nano Letters 24.1 (2023): 312-318.  ||对温度要求比较矫情 (温度范围比较窄) 的paracrystalline nucleation in disordered diamond. ||肯定了这一亚稳态相的相对稳定存在，并说只有在3200-3400K左右的狭窄范围内（Fig. 4c吉布斯自由能），才可能容易制备到paracrystalline diamond; 低于该温度，则不易形成；而高于该温度，会更容易形成nano-polycystalline diamond（如3600 K） ||MD制备样品的温度协议：以1 g/cc的DGN为前驱体，快速挤压到3.3 g/cc, 然后3000 (Fig. S1)， 3200 (Fig. S1)，3800 (Fig. S1) K弛豫2 ns得到样品.
- `tang2021nature_paracrystalline-diamond_part1.pdf`, Tang, Hu, et al. "Synthesis of paracrystalline diamond." Nature 599.7886 (2021): 605-610. TO BE DONE ...
- `wang2021crystal_porous-DGN.pdf`,   Wang, YongChao, YinBo Zhu, and HengAn Wu. "Porous characteristics of three-dimensional disordered graphene networks." Crystals 11.2 (2021): 127. TO BE DONE


## II. structure-kappa relationship

- `zhang2025scienceAdvances_aC-anomalous-kappa.pdf`, ZhongTing Zhang et al. "Unveiling the microscopic origin of anomalous thermal conductivity in amorphous carbon." Sci. Adv.11 (2025). || 以a-DG为例，高温高压，通过微修改压强，得到了密度范围为2.36-3.18 g/cc的DMG (disordered multilayer graphene network) to a-DG相（第一阶段相变）再 to ND (nanodiamond=paracrystalline diamond or nanopolycrystalline diamond) (第二阶段相变). 第一阶段是相对有序的DMG基体内部出现一定程度的amorphization（sp3），导致形成的a-DG的化学无序度的增大，但sp2/sp3=1附近，化学无序度达到最大。这一阶段对应的热导率变化是下降的趋势； 第二阶段相变，是持续增大的sp3,逐渐形核和长大，形成微小的diamond晶粒。这一阶段对应的热导率变化是上升趋势。|| 整体看来，a-DG热导率随密度先变小再增大。这一变化趋势跟报道的都是单调增加的结论不符合，所以叫anomalous。 ||原因分析：热导率先减小后增大形成一个极小值，跟结构相变直接相关。通过热导率物理量分析，发现diffusivity ($v^2\tau$)和热导率变化趋势同步，表明是结构相变带来的声子自由程和声子(主要集中在中频率7-30 THz范围)寿命先变小后变大所致 （因为体积热熔和群速度都随密度单调增加）。





## II. Thermal properties

- ` guo2025jcp_tutorial-ACE-kappa-solid.pdf`, Guo, Liben, et al. "Lattice dynamics modeling of thermal transport in solids using machine-learned atomic cluster expansion potentials: A tutorial." Journal of Applied Physics 137.8 (2025). || 该教程以ACE机器学习势函数为例，从训练集构造（手动构造+主动学习），势函数训练（能量/力权重选择，超参数选择）精度（和应用性质精度）和MLIP-MD计算成本的trade-off考量，到热性质计算等，做了一个基本流程介绍。|| 关于热性质及热导率计算的演示，采用的方法是基于准简谐近似的晶格动力学。|| 对于有清晰定义的波矢的晶体，采用准简谐近似求解玻尔兹曼热输运方程的方法来计算，即使用phono3py软件分别计算了声子谱，DOS，声子linewidth和热导率。||对于没有清晰定义波矢的非晶，采用准简谐近似格林函数（QHGK）方法。使用kALDo软件完成类似热性质的计算。



## II. MLIP-related

- `Baghishov2025_appplication-specific-MLIP.pdf `, Ilgar Baghishov et al, "Application-specific Machine-Learned Interatomic Potentials: Exploring the Trade-off Between Precision and Computational Cost", arXiv:2506.05646 || 如材料发现，由于需要高通量计算，要考虑MD模拟耗费的总时间成本，所以当机器学习势函数用于某一具体应用时，就会对MLIP的模型复杂性做某种限制。即是说，考虑快速的MD计算，我们要降低制约MLIP运行速度的模型复杂度（神经网络层数，描述符个数，描述符完备程度等）。 简言之，我们在做某一具体应用时，就要考虑计算成本和计算精度的之间的平衡。|| 一个MLIP模型的训练，要经历两个阶段：数据集制备和模型拟合。第一阶段的数据集的DFT制备，涉及MLIP模型精度的因素主要有两个：DFT计算精度（k-point, cuttoff energy）和 dataset size. 第二阶段的模型拟合，涉及MLIP模型精度的因素也主要是两个：模型复杂度选择和训练时能量/力的权重分配。也就是说，这四个因素都会明显影响训练的MLIP模型的精度和计算成本。|| 具体来说，文章使用SNAP势函数模型，分别考察了dataset size (Leveragge score，主动学习远点采样做data efficiency), DFT precision (不同precision等级但构型都相同的dataset)， energy/force weight factor during training, expansion order (2$J_{max}$ 衡量模型复杂度)如何同时影响势函数精度和DFT计算成本（注意这里是DFT成本，不是MD成本，因为MLIP一旦训练好了，精度高或低，都基本不会影响MD计算成本）.






## II. Misc

- `Cao2025jap_16-metal-kappa.pdf`, Cao, Shuo, et al. "Lattice thermal conductivity of 16 elemental metals from molecular dynamics simulations with a unified neuroevolution potential." arXiv preprint arXiv:2505.13179 (2025). || 使用UNEP16-v1势，EAM势，HNEMD计算了16种金属的晶格热导率，并跟BTE方法计算的结果做了对照。发现UNEP16-v1的晶格热导率比EAM普遍大一点，从而更接近BTE只考虑声子-声子散射计算的结果。


## TO DO (Bohan-related)
- Ibragimova, Rina, et al. "Unifying the description of hydrocarbons and hydrogenated carbon materials with a chemically reactive machine learning interatomic potential." Chemistry of Materials 37.3 (2025): 1094-1110.
- Chen, Zhuo, et al. "Softening of Vibrational Modes and Anharmonicity Induced Thermal Conductivity Reduction in a‐Si: H at High Temperatures." Advanced Electronic Materials (2025): 2500104.


## TO Do

- `moon2025npj_aC-crystal-like-kappa.pdf`，Moon, Jaeyun, and Zhiting Tian. "Crystal-like thermal transport in amorphous carbon." npj Computational Materials 11.1 (2025): 1-8.



