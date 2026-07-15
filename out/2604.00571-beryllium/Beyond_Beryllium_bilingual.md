arXiv:2604.00571v1 [cond-mat.mtrl-sci] 1 Apr 2026

# Beyond Beryllium: AI-Accelerated Materials Discovery for Interstellar Spacecraft Shielding / 超越铍：用于星际飞船屏蔽的AI加速材料发现

Yue Li, $^{1}$ Xu Pan, $^{2}$ and Kaiyuan Guo $^{3}$

$^{1}$School of Materials Science and Engineering, Nanyang Interstellar University, Singapore 639798, Singapore

$^{1}$南洋星际大学材料科学与工程学院，新加坡 639798，新加坡

$^{2}$School of Artificial Intelligence, Nanyang Interstellar University, Singapore 639798, Singapore

$^{2}$南洋星际大学人工智能学院，新加坡 639798，新加坡

$^{3}$Department of Medical Radiation Management and Hibernation, Shanghai Interstellar Jiao Tong University, Shanghai 200240, China

$^{3}$上海星际交通大学医学辐射管理与冬眠系，上海 200240，中国

(Dated: April 1, 2026)

(日期：2026年4月1日)

Project Daedalus (1973–1978), the most detailed interstellar probe design study ever conducted, specified a 9 mm beryllium erosion shield to protect the spacecraft payload during its 5.9 light-year cruise to Barnard's Star at 12% of the speed of light. This design, however, predated both the isolation of two-dimensional materials and the development of graph neural network (GNN) property predictors. Here, we systematically screen 20 candidate materials—spanning conventional aerospace metals, transition metal dichalcogenides, and ultra-high-temperature ceramics—using density functional theory (DFT) data from the JARVIS database (76,000 materials) with independent validation by the Atomistic Line Graph Neural Network (ALIGNN). We evaluate candidates across four criteria: specific mechanical stiffness ($K_V/\rho$), sputtering resistance, thermal neutron absorption cross-section, and thermodynamic stability. Our screening identifies hexagonal boron nitride (h-BN) and boron carbide ($B_4C$) as dual-function materials offering simultaneous mechanical protection and neutron radiation shielding, and we propose a graphene/h-BN/polymer layered heterostructure shield design that achieves an estimated 47% mass reduction relative to the original beryllium specification. These findings will become immediately actionable upon the successful development of fusion pulse propulsion, which we note remains an outstanding engineering challenge.

戴达罗斯计划 (Project Daedalus, 1973–1978) 是迄今为止最详细的星际探测器设计研究，该计划规定采用9毫米厚的铍侵蚀防护罩，以保护飞船有效载荷在以12%光速巡航5.9光年到达巴纳德星 (Barnard's Star) 的过程中免受侵蚀。然而，这项设计早于二维材料的发现以及图神经网络 (GNN) 性能预测器的发展。在此，我们利用 JARVIS 数据库（包含76,000种材料）的密度泛函理论 (DFT) 数据，并通过原子线图神经网络 (ALIGNN) 进行独立验证，系统筛选了20种候选材料，涵盖了传统航空航天金属、过渡金属二硫化物和超高温陶瓷。我们根据四个标准评估了这些候选材料：比机械刚度 ($K_V/\rho$)、溅射阻力、热中子吸收截面和热力学稳定性。我们的筛选结果表明，六方氮化硼 (h-BN) 和碳化硼 ($B_4C$) 是能够同时提供机械保护和中子辐射屏蔽的双功能材料。我们提出了一种石墨烯/h-BN/聚合物层状异质结构防护罩设计，相对于原始的铍规格，预计可实现47%的质量减轻。这些发现将在聚变脉冲推进成功开发后立即投入实际应用，但我们注意到，聚变脉冲推进仍然是一项悬而未决的工程挑战。

![手持式光谱仪工作原理及石墨烯层结构示意图](images/img_000.png)

Table of Contents Graphic: An interstellar probe encounters the ISM at 0.12c. Inset: layered heterostructure shield with graphene and h-BN nanostructures. / 目录图：星际探测器以0.12倍光速遭遇星际介质 (ISM)。插图：带有石墨烯和h-BN纳米结构的层状异质结构防护罩。

# INTRODUCTION / 引言

The prospect of interstellar travel has motivated some of the most ambitious engineering studies in human history. In 1968, Dyson [1] articulated the fundamental energetics of interstellar transport, establishing that nuclear pulse propulsion could in principle accelerate a spacecraft to a significant fraction of the speed of light.

星际旅行的前景激发了人类历史上一些最雄心勃勃的工程研究。1968年，戴森 (Dyson) [1] 阐述了星际运输的基本能量学，确立了核脉冲推进原则上可以将航天器加速到光速的很大一部分。

Project Orion (1958–1965) explored nuclear pulse propulsion using fission bombs before being curtailed by the Partial Test Ban Treaty [2]. The most comprehensive design study to date, Project Daedalus (1973–1978), proposed an unmanned probe propelled by inertial confinement fusion to reach Barnard's Star, 5.9 light-years distant, at a cruise velocity of 0.12c [3]. More recently, Project Icarus has sought to update the Daedalus concept with modern engineering knowledge [4].

猎户座计划 (Project Orion, 1958–1965) 探索了使用裂变炸弹进行核脉冲推进，但后来因《部分禁止核试验条约》而被中止 [2]。迄今为止最全面的设计研究是戴达罗斯计划 (Project Daedalus, 1973–1978)，该计划提出了一种由惯性约束聚变驱动的无人探测器，以0.12倍光速的巡航速度抵达5.9光年外的巴纳德星 [3]。最近，伊卡洛斯计划 (Project Icarus) 旨在利用现代工程知识更新戴达罗斯概念 [4]。

A critical and often underappreciated challenge of relativistic spaceflight is the bombardment of the spacecraft by interstellar medium (ISM) particles. At 0.12c (3.6 × 10$^{7}$ m/s), even the tenuous ISM becomes a formidable particle beam. Martin's analysis for the Daedalus study [5] showed that over a 5.9 light-year transit through a region with particle density n ≈ 1 cm $^{-3}$, the frontal shield (area A ≈ 491 m$^{2}$) would encounter ≈ 2.7 × 10$^{25}$ particles, with individual protons carrying kinetic energies of ~6.7 MeV—well into the nuclear reaction regime. Larger dust grains, though far rarer, can deliver megajoule-scale impacts equivalent to macroscopic explosions [6, 7].

相对论性太空飞行中一个关键但常被低估的挑战是航天器受到星际介质 (ISM) 粒子的轰击。在0.12倍光速（3.6 × 10$^{7}$ 米/秒）下，即使稀薄的星际介质也会变成强大的粒子束。马丁 (Martin) 为戴达罗斯研究进行的分析 [5] 表明，在穿过粒子密度 n ≈ 1 cm $^{-3}$ 区域的5.9光年航程中，前部防护罩（面积 A ≈ 491 m$^{2}$）将遭遇约 2.7 × 10$^{25}$ 个粒子，单个质子携带约6.7 MeV的动能——这已进入核反应区域。虽然更大型的尘埃颗粒极为罕见，但它们能产生兆焦耳级撞击，相当于宏观爆炸 [6, 7]。

The Daedalus team's solution was a 9 mm beryllium erosion shield, selected for its combination of low density ($\rho = 1.85$ g/cm$^3$), reasonable bulk modulus ($K_V \approx 115$ GPa), and high sublimation energy ($E_{sb} = 3.36$ eV/atom) [3, 5]. However, this design was constrained to the materials knowledge of the 1970s. In the intervening half-century, materials science has undergone transformative advances: the isolation and characterization of two-dimensional materials beginning with graphene in 2004 [8]; the development of ultra-high-

“代达罗斯”团队的解决方案是9毫米厚的铍侵蚀防护罩，选择铍是因为它兼具低密度（$\rho = 1.85$ g/cm$^3$）、合理的体积模量（$K_V \approx 115$ GPa）和高升华能（$E_{sb} = 3.36$ eV/atom）[3, 5]。然而，这项设计受限于20世纪70年代的材料知识。在随后的半个世纪里，材料科学取得了变革性进展：从2004年石墨烯开始的二维材料的分离和表征[8]；超高-

temperature ceramics (UHTCs) with extreme mechanical properties [9]; and the discovery that boron-containing materials provide exceptional neutron radiation shielding [10–13].

温陶瓷（UHTCs）的开发，这些陶瓷具有极端的力学性能[9]；以及发现含硼材料能提供卓越的中子辐射屏蔽[10–13]。

Equally transformative has been the rise of computational materials screening. The JARVIS (Joint Automated Repository for Various Integrated Simulations) database now contains density functional theory (DFT) calculations for over 76,000 materials [14], while graph neural network architectures such as the Atomistic Line Graph Neural Network (ALIGNN) enable rapid property prediction with near-DFT accuracy [15–17].

同样具有变革性的是计算材料筛选的兴起。JARVIS（各种集成模拟联合自动化存储库）数据库目前包含超过76,000种材料的密度泛函理论（DFT）计算结果[14]，而原子线图神经网络（ALIGNN）等图神经网络架构则能以接近DFT的精度实现快速性能预测[15–17]。

In this work, we leverage the JARVIS-DFT database and ALIGNN pretrained models to systematically re-evaluate the materials selection for interstellar dust shielding. We screen 20 candidate materials across three families—conventional aerospace metals, layered/two-dimensional materials, and ceramics/superhard compounds—against four performance metrics relevant to the Daedalus mission profile. We identify several materials that substantially outperform beryllium, propose a layered heterostructure shield concept, and discuss the implications for future interstellar mission design.

在这项工作中，我们利用JARVIS-DFT数据库和ALIGNN预训练模型，系统地重新评估了星际尘埃屏蔽的材料选择。我们针对“代达罗斯”任务剖面相关的四项性能指标，筛选了涵盖三个系列的20种候选材料——传统航空航天金属、层状/二维材料以及陶瓷/超硬化合物。我们识别出几种性能大幅优于铍的材料，提出了层状异质结构防护罩概念，并讨论了其对未来星际任务设计的影响。

# METHODS / 方法

## Mission Parameters / 任务参数

We adopt the Daedalus Phase 2 mission profile [3]: cruise velocity $v = 0.12c = 3.6 \times 10^7$ m/s, distance to Barnard's Star $d = 5.9$ ly = $5.58 \times 10^{16}$ m, yielding a cruise time of ~49 years. The shield is modeled as a circular disk of radius $R = 12.5$ m (matching the Daedalus second stage diameter of 25 m), giving a frontal area $A = \pi R^2 \approx 491$ m $^{2}$.

我们采用“代达罗斯”第二阶段任务剖面[3]：巡航速度 $v = 0.12c = 3.6 \times 10^7$ m/s，到巴纳德星的距离 $d = 5.9$ ly = $5.58 \times 10^{16}$ m，巡航时间约为49年。防护罩被建模为一个半径 $R = 12.5$ m 的圆形盘（与“代达罗斯”第二级直径25 m相匹配），迎风面积 $A = \pi R^2 \approx 491$ m $^{2}$。

The local ISM is modeled with particle number density $n = 1 \text{ cm}^{-3} (= 10^6 \text{ m}^{-3})$ and mean particle mass $\bar{m} = 1.29$ amu, appropriate for a hydrogen-dominated medium with ~10% helium by number. The total fluence on the shield surface over the mission is:

局部星际介质（ISM）被建模为粒子数密度 $n = 1 \text{ cm}^{-3} (= 10^6 \text{ m}^{-3})$，平均粒子质量 $\bar{m} = 1.29$ amu，这适用于以氢为主、氦含量约10%的介质。任务期间防护罩表面的总注量为：

$$ \Phi = n \cdot d = 5.58 \times 10^{18} \text{ particles/cm}^2 \quad (1) $$

At 0.12c, the kinetic energy of a single proton is $E_p = \frac{1}{2}m_p v^2 \approx 6.7$ MeV (non-relativistic approximation; the Lorentz factor $\gamma = 1.0072$ introduces a <1% correction). This energy substantially exceeds typical sputtering thresholds (~10–100 eV) and surface binding energies (~3–9 eV), placing the bombardment firmly in the high-energy sputtering regime.

在0.12c的速度下，单个质子的动能为 $E_p = \frac{1}{2}m_p v^2 \approx 6.7$ MeV（非相对论近似；洛伦兹因子 $\gamma = 1.0072$ 引入的修正小于1%）。此能量大幅超过典型的溅射阈值（约10–100 eV）和表面结合能（约3–9 eV），使轰击牢固地处于高能溅射状态。

## Material Screening Criteria / 材料筛选标准

We evaluate each candidate material against four criteria:

我们根据四项标准评估每种候选材料：

(i) Specific mechanical stiffness, quantified by the ratio $K_V/\rho$ (GPa·cm $^{3}$/g), where $K_V$ is the Voigt bulk modulus and $\rho$ is the mass density. This metric captures the ability to resist mechanical deformation per unit mass—critical for minimizing shield mass while maintaining structural integrity under impact loading. We note that the Voigt average represents an upper bound on the true polycrystalline bulk modulus; for highly anisotropic layered materials (graphite, h-BN), this average includes the very stiff in-plane elastic constants and thus substantially exceeds the soft out-of-plane response. The Reuss (lower) bound for these materials would be significantly lower. Both bounds are reported where relevant.

(i) 比机械刚度，通过比率 $K_V/\rho$ (GPa·cm $^{3}$/g) 量化，其中 $K_V$ 是沃伊特体积模量（Voigt bulk modulus），$\rho$ 是质量密度。该指标衡量单位质量抵抗机械变形的能力——这对于在冲击载荷下保持结构完整性同时最小化防护罩质量至关重要。我们注意到，沃伊特平均值代表了真实多晶体积模量的上限；对于高度各向异性的层状材料（如石墨、六方氮化硼 h-BN），该平均值包含了非常坚硬的面内弹性常数，因此大幅超过了较软的面外响应。这些材料的罗伊斯（Reuss，下）限将显著更低。相关时会报告这两个界限。

(ii) Sputtering resistance, parameterized by the surface binding energy $E_{sb}$ (eV/atom). In the high-energy limit relevant to 0.12c bombardment, the sputtering yield scales approximately as $Y \propto 1/E_{sb}$ [18]. We employ a simplified model:

(ii) 抗溅射性，由表面结合能 $E_{sb}$（eV/原子）参数化。在与0.12c轰击相关的高能极限下，溅射产额大约与 $Y \propto 1/E_{sb}$ 成比例 [18]。我们采用一个简化模型：

$$ Y = Y_{\text{ref}} \cdot \frac{E_{\text{ref}}}{E_{\text{sh}}} \quad (2) $$

with $Y_{ref} = 3$ atoms/ion at $E_{ref} = 4$ eV, consistent with the high-energy limiting behavior reported for metallic targets [18].

其中 $Y_{ref} = 3$ 原子/离子，在 $E_{ref} = 4$ eV，这与金属靶材 [18] 报告的高能极限行为一致。

(iii) Thermal neutron absorption cross-section $\sigma_a$ (barns). While the primary ISM bombardment consists of fast particles, secondary neutron production within the shield itself, combined with the galactic cosmic ray background, makes neutron moderation an important secondary consideration. Materials containing boron-10 ($\sigma_a = 3,840$ barns) offer a dramatic advantage [10].

(iii) 热中子吸收截面 $\sigma_a$（靶恩）。虽然主要的星际介质 (ISM) 轰击由快粒子组成，但屏蔽层内部的次级中子产生，结合银河宇宙射线背景，使得中子慢化成为一个重要的次要考虑因素。含有硼-10（$\sigma_a = 3,840$ 靶恩）的材料具有显著优势 [10]。

(iv) Thermodynamic stability, assessed via the energy above the convex hull ($E_{\text{hull}}$) from DFT calculations.

(iv) 热力学稳定性，通过密度泛函理论 (DFT) 计算得出的凸包能量 ($E_{\text{hull}}$) 进行评估。

## Material Data Sources / 材料数据来源

Elastic moduli ($K_V$, $G_V$), formation energies, and band gaps were obtained from the JARVIS-DFT database [14, 17], which provides DFT-computed properties using the OptB88vdW functional for over 76,000 materials. Each material is identified by a unique JVASP identifier (Table II), enabling full reproducibility. Thermal neutron cross-sections were taken from the NNDC/IAEA Nuclear Data compilation [19]. Surface binding energies were obtained from experimental sublimation enthalpy data.

弹性模量 ($K_V$, $G_V$)、形成能和带隙均来自 JARVIS-DFT 数据库 [14, 17]，该数据库使用 OptB88vdW 泛函提供了超过 76,000 种材料的 DFT 计算属性。每种材料都由唯一的 JVASP 标识符（表 II）识别，从而实现完全可重现性。热中子截面取自 NNDC/IAEA 核数据汇编 [19]。表面结合能则来自实验升华焓数据。

As an independent validation, we performed property predictions using the ALIGNN pretrained models [15] (jv_bulk_modulus_kv_alignn and jv_shear_modulus_gv_alignn) on the same crystal

作为一项独立验证，我们使用 ALIGNN 预训练模型 [15]（jv_bulk_modulus_kv_alignn 和 jv_shear_modulus_gv_alignn）对相同的晶体

structures retrieved from JARVIS. We note that beryllium is represented in the JARVIS database by its bcc phase (JVASP-14628, Im $\bar{3}$m), as the ground-state hcp phase lacks computed elastic tensor data in the current release.

结构进行了属性预测，这些结构是从 JARVIS 数据库中检索的。我们注意到，JARVIS 数据库中的铍以其体心立方 (bcc) 相（JVASP-14628, Im $\bar{3}$m）表示，因为当前版本中缺少基态密排六方 (hcp) 相的计算弹性张量数据。

# Composite Figure of Merit / 综合品质因数

To enable single-metric ranking, we define a shield figure of merit:

为了实现单一指标排名，我们定义了一个屏蔽品质因数：

$$ \text{FoM} = \frac{K_V}{\rho} \cdot E_{sb} \cdot (1 + \log_{10}(\sigma_a + 1)) \quad (3) $$

normalized such that Be = 1.0. This weighting treats mechanical performance, sputtering resistance, and neutron absorption as multiplicatively complementary properties. We note that different mission architectures may warrant alternative weightings.

归一化后使 Be = 1.0。这种加权方式将机械性能、抗溅射性和中子吸收视为乘法互补属性。我们注意到，不同的任务架构可能需要替代的权重。

# RESULTS / 结果

# Mechanical Properties / 机械性能

Figure 1 presents the Voigt bulk modulus $K_V$ and Fig. 2 the specific modulus $K_V/\rho$ for all 20 candidate materials. Among the ceramics, diamond ($K_V = 437$ GPa, JVASP-91), cubic boron nitride (c-BN, 378 GPa, JVASP-7836), tungsten carbide (WC, 342 GPa), and tantalum carbide (TaC, 327 GPa) exhibit the highest absolute stiffness. When normalized by density, diamond and graphite ($K_V/\rho \approx 125$ GPa·cm$^3$/g) dominate, followed by c-BN (109), h-BN (107), and $B_4C$ (92).

图1展示了所有20种候选材料的沃伊特体模量 $K_V$，图2展示了比模量 $K_V/\rho$。在陶瓷材料中，金刚石 ($K_V = 437$ GPa, JVASP-91)、立方氮化硼 (c-BN, 378 GPa, JVASP-7836)、碳化钨 (WC, 342 GPa) 和碳化钽 (TaC, 327 GPa) 表现出最高的绝对刚度。当按密度归一化时，金刚石和石墨 ($K_V/\rho \approx 125$ GPa·cm$^3$/g) 占据主导地位，其次是 c-BN (109)、h-BN (107) 和 $B_4C$ (92)。

An important caveat applies to the layered materials. The JARVIS-DFT Voigt bulk moduli for graphite ($K_V = 281$ GPa, JVASP-48) and h-BN ($K_V = 245$ GPa, JVASP-62756) are substantially higher than the ~30–40 GPa values commonly cited in the literature. This discrepancy arises because the Voigt average is an upper bound that heavily weights the extremely stiff in-plane elastic constants ($C_{11} > 1,000$ GPa for graphene) while the interlayer response ($C_{33} \sim 30$–40 GPa) contributes less. The Reuss (lower) bound for these materials would be closer to the commonly cited values. For the shielding application considered here, the in-plane stiffness is arguably the more relevant metric, as dust grain impacts would load the shield primarily in-plane.

对于层状材料，存在一个重要的注意事项。JARVIS-DFT 计算的石墨 ($K_V = 281$ GPa, JVASP-48) 和六方氮化硼 (h-BN, $K_V = 245$ GPa, JVASP-62756) 的沃伊特体模量显著高于文献中普遍引用的约 30–40 GPa 的值。这种差异的产生是因为沃伊特平均值是一个上限，它严重加权了极高的面内弹性常数（石墨烯的 $C_{11} > 1,000$ GPa），而层间响应 ($C_{33} \sim 30$–40 GPa) 的贡献较小。这些材料的罗伊斯（下限）将更接近普遍引用的值。对于此处考虑的屏蔽应用，面内刚度可以说是更相关的指标，因为尘粒撞击主要会在面内加载屏蔽层。

The layered transition metal dichalcogenides ($MoS_2$, $WS_2$, $MoSe_2$, $WSe_2$) exhibit uniformly low specific moduli (<15 GPa·cm$^3$/g), rendering them unsuitable as primary structural shielding materials.

层状过渡金属二硫属化物（二硫化钼 $MoS_2$、二硫化钨 $WS_2$、二硒化钼 $MoSe_2$、二硒化钨 $WSe_2$）表现出统一的低比模量（<15 GPa·cm$^3$/g），这使得它们不适合作为主要的结构屏蔽材料。

![不同材料的Voigt体模量对比柱状图](images/img_001.png)

FIG. 1. Voigt bulk modulus $K_V$ of 20 candidate shielding materials (JARVIS-DFT). Dashed line: Be baseline. / 图1. 20种候选屏蔽材料的Voigt体积模量 $K_V$ (JARVIS-DFT)。虚线：Be基线。

# Shield Mass Analysis / 屏蔽质量分析

Figure 3 presents the erosion-adjusted shield mass for each material, computed by scaling the Daedalus reference thickness (9 mm) inversely with surface binding energy relative to beryllium ($E_{sb}^{Be} = 3.36$ eV), with a minimum structural thickness of 1 mm. The Daedalus beryllium erosion plate at 9 mm thickness serves as the baseline at 8.5 metric tons.

图3展示了每种材料侵蚀调整后的屏蔽质量，该质量是根据Daedalus参考厚度（9毫米）与相对于铍的表面结合能（$E_{sb}^{Be} = 3.36$ eV）成反比进行缩放计算的，并设定了1毫米的最小结构厚度。9毫米厚的Daedalus铍侵蚀板作为基线，其质量为8.5公吨。

Several materials achieve significant mass reductions relative to beryllium: graphite (4.5 t, -47%), $B_4C$ (6.4 t, -24%), h-BN (6.6 t, -22%), and diamond (7.0 t, -17%). The color encoding in Fig. 3 reveals that h-BN and $B_4C$ simultaneously provide exceptional neutron absorption ($\sigma_a > 380$ barns per atom), a capability entirely absent from the beryllium baseline ($\sigma_a = 0.008$ barns).

有几种材料相对于铍实现了显著的质量减少：石墨（4.5吨，-47%）、$B_4C$（6.4吨，-24%）、h-BN（6.6吨，-22%）和金刚石（7.0吨，-17%）。图3中的颜色编码显示，h-BN（六方氮化硼）和$B_4C$（碳化硼）同时提供了卓越的中子吸收能力（$\sigma_a > 380$ 靶恩/原子），而铍基线则完全不具备这种能力（$\sigma_a = 0.008$ 靶恩）。

At the other extreme, high-Z materials such as tungsten carbide (32.8 t), tungsten (31.5 t), and tantalum carbide (29.3 t) are unsuitable despite their excellent absolute mechanical properties, as their high densities translate to prohibitive shield masses.

另一方面，高Z材料（高原子序数材料），如碳化钨（32.8吨）、钨（31.5吨）和碳化钽（29.3吨），尽管具有优异的绝对力学性能，但因其高密度导致屏蔽质量过高，因此不适用。

# Multi-Objective Screening / 多目标筛选

Figure 4 presents the two most critical performance axes—specific modulus versus thermal neutron

图4展示了两个最关键的性能轴——比模量与热中子

![不同材料比模量对比条形图](images/img_002.png)

FIG. 2. Specific modulus $K_V/\rho$, the key mass-efficiency metric. Dashed line: Be baseline from the Daedalus design. / 图2. 比模量 $K_V/\rho$，关键的质量效率指标。虚线：Daedalus设计中的Be基线。

absorption—as a scatter plot with point size proportional to surface binding energy.

吸收——以散点图形式呈现，点的大小与表面结合能成正比。

The Pareto front reveals three distinct high-performance regimes: (i) Pure mechanical excellence: diamond and graphite, with $K_V/\rho \approx 125$ but negligible neutron absorption. (ii) Balanced performance: $B_4C$ ($K_V/\rho = 92$, $\sigma_a = 614$ barns), c-BN and h-BN ($K_V/\rho \approx 107-109$, $\sigma_a = 384$ barns), and $TiB_2$ ($K_V/\rho = 57$, $\sigma_a = 513$ barns), combining strong mechanical properties with very high neutron absorption via their boron content. (iii) Radiation shielding specialists: $ZrB_2$ ($\sigma_a = 511$ barns) at moderate specific modulus.

帕累托前沿揭示了三个不同的高性能区域：(i) 纯粹的力学性能卓越：金刚石和石墨，其$K_V/\rho \approx 125$，但中子吸收能力可忽略不计。(ii) 平衡性能：$B_4C$（碳化硼， $K_V/\rho = 92$，$\sigma_a = 614$ 靶恩）、c-BN（立方氮化硼）和h-BN（六方氮化硼）（$K_V/\rho \approx 107-109$，$\sigma_a = 384$ 靶恩），以及$TiB_2$（二硼化钛）（$K_V/\rho = 57$，$\sigma_a = 513$ 靶恩），它们通过其硼含量将强大的力学性能与极高的中子吸收能力相结合。(iii) 辐射屏蔽专家：$ZrB_2$（二硼化锆）（$\sigma_a = 511$ 靶恩），具有中等的比模量。

Beryllium occupies a poor position in this space: moderate specific modulus (65) with essentially zero neutron absorption. Its selection in 1978 reflects the limited material options available, not optimization against modern multi-objective criteria.

铍在此空间中处于不利位置：比模量中等（65），中子吸收能力几乎为零。它在1978年的选择反映了当时可用的材料选择有限，而非根据现代多目标标准进行优化。

# ALIGNN Validation / ALIGNN验证

Figure 5 presents parity plots comparing ALIGNN predictions with JARVIS-DFT values for bulk modulus $K_V$ and shear modulus $G_V$. Excluding $B_4C$, the agreement is excellent: $R^2 = 0.990$ and MAE = 4.4 GPa for $K_V$; $R^2 = 0.980$ and MAE = 6.8 GPa for $G_V$.

图5展示了比较ALIGNN预测值与JARVIS-DFT计算的体积模量$K_V$和剪切模量$G_V$值的一致性图。排除$B_4C$后，两者的一致性极佳：对于$K_V$， $R^2$（决定系数）= 0.990，MAE（平均绝对误差）= 4.4 GPa；对于$G_V$， $R^2$ = 0.980，MAE = 6.8 GPa。

The B₄C outlier (JVASP-52866;ALIGNN predicts

$B_4C$（碳化硼）异常值（JVASP-52866；ALIGNN预测

![不同材料侵蚀调整后屏蔽质量的横向条形图](images/img_003.png)

FIG. 3. Erosion-adjusted shield mass for a 5.9 ly mission at 0.12c. Bar color indicates thermal neutron absorption cross-section (color bar, log scale). Dashed line marks the beryllium baseline (8.5 t). Colored markers indicate material family. / 图3. 5.9光年、0.12c任务的侵蚀调整后屏蔽质量。条形颜色表示热中子吸收截面（色条，对数刻度）。虚线标记铍基线（8.5吨）。彩色标记表示材料族。

![材料的热中子吸收截面与比模量关系散点图](images/img_004.png)

FIG. 4. Multi-objective screening: specific modulus versus thermal neutron absorption cross-section. Point size is proportional to surface binding energy. Staircase line indicates the Pareto front. The gold star marks beryllium (Daedalus baseline). / 图4. 多目标筛选：比模量与热中子吸收截面。点的大小与表面结合能成正比。阶梯线表示帕累托前沿。金色星号标记铍（Daedalus基线）。

$K_V = 9$ GPa versus DFT $K_V = 228$ GPa) is attributed to the structural complexity of the rhombohedral $B_{12}C_3$ unit cell (15 atoms, R$\bar{3}$m), which contains icosahedral $B_{12}$ clusters linked by C–B–C chains. This topology is rare in the ALIGNN training set, and the resulting graph representation may inadequately capture the inter-cluster bonding that governs the bulk elastic response.

$K_V = 9$ GPa，而DFT计算的$K_V = 228$ GPa）归因于菱方晶系$B_{12}C_3$晶胞（15个原子，R$\bar{3}$m）的结构复杂性，该晶胞包含通过C–B–C链连接的准二十面体$B_{12}$团簇。这种拓扑结构在ALIGNN训练集中很少见，因此产生的图表示可能未能充分捕捉决定整体弹性响应的团簇间键合。

![ALIGNN与JARVIS-DFT模型计算的体积模量(Kv)和剪切模量(Gv)预测值对比散点图](images/img_005.png)

FIG. 5. ALIGNN predictions versus JARVIS-DFT values for (a) $K_V$ and (b) $G_V$. $B_4C$ (inverted triangle) is an outlier due to structural complexity. Statistics exclude $B_4C$. / 图5. ALIGNN 预测值与 JARVIS-DFT 值在 (a) $K_V$ 和 (b) $G_V$ 方面的对比。$B_4C$（倒三角形）由于结构复杂性而成为异常值。统计数据不包含 $B_4C$。

## Layered Heterostructure Shield Concept / 分层异质结构防护罩概念

Based on our screening results, we propose a functionally graded layered shield (Fig. 6) in which each layer addresses a specific threat:
根据我们的筛选结果，我们提出了一种功能梯度分层防护罩（图6），其中每一层都针对特定的威胁：

Layer 1: Graphene/graphite impact layer (~50 µm). The outermost layer exploits the extraordinary specific modulus of sp $^{2}$ carbon ($K_V/\rho = 124$ GPa·cm $^{3}$/g) and high sublimation energy (7.43 eV/atom) to absorb initial dust grain impacts and resist sputtering erosion.
第1层：石墨烯/石墨冲击层（约50微米）。最外层利用sp²碳非凡的比模量（$K_V/\rho = 124$ GPa·cm³/g）和高升华能（7.43 eV/原子）来吸收初始尘埃颗粒冲击并抵抗溅射侵蚀。

Layer 2: h-BN neutron absorber (~2 mm). Hexagonal boron nitride serves dual duty: its boron-10 content ($\sigma_a = 3,840$ barns for $^{10}$B) efficiently captures secondary thermal neutrons, while its high Voigt bulk modulus ($K_V = 245$ GPa) provides mechanical reinforcement. NASA has independently validated BN-based materials for space radiation shielding [10, 12, 20].
第2层：h-BN中子吸收层（约2毫米）。六方氮化硼（h-BN）具有双重作用：其硼-10含量（$^{10}$B的吸收截面 $\sigma_a = 3,840$ 靶恩）能有效捕获次级热中子，同时其高沃伊特体积模量（$K_V = 245$ GPa）提供机械增强。NASA 已独立验证了基于BN的材料用于空间辐射屏蔽 [10, 12, 20]。

Layer 3: HDPE cosmic ray moderator (~5 mm). High-density polyethylene, with its high hydrogen content, serves as a proton moderator for secondary cosmic ray particles, following established spacecraft shielding practice.
第3层：HDPE宇宙射线减速层（约5毫米）。高密度聚乙烯（HDPE）因其高氢含量，按照既定的航天器屏蔽实践，可作为次级宇宙射线粒子的质子减速剂。

Layer 4: Aluminum structural support (~1 mm). A conventional aluminum backing provides structural mounting and thermal management.
第4层：铝结构支撑层（约1毫米）。传统的铝背板提供结构安装和热管理。

The total heterostructure thickness of ~8 mm is comparable to the original 9 mm beryllium design, but the estimated total mass of ~4.5 metric tons represents a 47% reduction from the 8.5-ton beryllium baseline, while adding neutron absorption capability entirely absent from the original.
该异质结构的总厚度约为8毫米，与原始的9毫米铍设计相当，但估计总质量约为4.5公吨，比8.5公吨的铍基准减少了47%，同时增加了原始设计中完全没有的中子吸收能力。

## Figure of Merit Ranking / 性能指标排名

Table I presents the composite figure of merit for the top 10 candidates. The top-ranked materials—c-BN (FoM = 9.2), B₄C (9.1), h-BN (9.0), and TiB₂ (6.3)—all contain boron, reflecting the outsized contribution

表 I 列出了排名前 10 的候选材料的综合品质因数。排名最高的材料——c-BN（FoM = 9.2）、B₄C（9.1）、h-BN（9.0）和 TiB₂（6.3）——都含有硼，这反映了

![分层复合材料结构示意图：用于宇宙射线屏蔽与有效载荷保护](images/img_006.png)

FIG. 6. Proposed layered heterostructure shield concept. Each layer is optimized for a specific threat: dust impact absorption (graphene/graphite), neutron capture (h-BN), cosmic ray moderation (HDPE), and structural support (Al). Total mass represents a ~47% reduction relative to the Daedalus beryllium shield. / 图6. 拟议的分层异质结构防护罩概念。每一层都针对特定威胁进行了优化：尘埃冲击吸收（石墨烯/石墨）、中子捕获（h-BN）、宇宙射线减速（HDPE）和结构支撑（Al）。总质量相对于“代达罗斯”号铍防护罩减少了约47%。

TABLE I. Top 10 candidate materials ranked by composite figure of merit, normalized to Be = 1.0. All $K_V$ values from JARVIS-DFT. / 表I. 按综合性能指标排名的前10名候选材料，归一化至Be = 1.0。所有 $K_V$ 值均来自 JARVIS-DFT。

|Material| $K_V/\rho$ | $\sigma_a$ (b) | $E_{\text{sb}}$ (eV) |Mass (t)|FoM|
|---|---|---|---|---|---|
|c-BN|109.2|384|5.18|9.9|9.2|
|$B_{4}C$|92.2|614|5.70|6.4|9.1|
|h-BN|106.9|384|5.18|6.6|9.0|
|$TiB_{2}$|57.0|513|6.50|10.2|6.3|
|Diamond|125.0|0.004|7.43|7.0|4.2|
|Graphite|124.1|0.004|7.43|4.5|4.2|
|$ZrB_{2}$|39.4|511|6.30|14.2|4.2|
|SiC|67.6|0.09|6.22|7.5|2.0|
|HfC|19.5|52|6.80|27.5|1.6|
|TaC|23.0|10|7.20|29.3|1.5|

of neutron absorption to overall shielding performance. Diamond and graphite rank next (FoM ≈ 4.2) on the strength of their unmatched specific moduli alone.
中子吸收对整体屏蔽性能的巨大贡献。金刚石和石墨紧随其后（FoM ≈ 4.2），仅凭其无与伦比的比模量。

The original Daedalus beryllium (FoM $\equiv$ 1.0) is outperformed by 13 of 20 candidates, suggesting that the 1978 material selection was, charitably, suboptimal by modern standards.
原始的“代达罗斯”号铍（FoM $\equiv$ 1.0）被20种候选材料中的13种超越，表明1978年的材料选择，宽泛地说，按现代标准来看是次优的。

# DISCUSSION / 讨论

Our screening reveals a striking finding: hexagonal boron nitride, a material whose radiation shielding properties have been extensively validated by NASA for low-Earth orbit applications [10–13], has apparently never been considered for interstellar shielding. This oversight is historically understandable—h-BN was not available in
我们的筛选揭示了一个惊人的发现：六方氮化硼（h-BN），一种其辐射屏蔽性能已由NASA针对近地轨道应用广泛验证的材料 [10–13]，显然从未被考虑用于星际屏蔽。这一疏忽在历史上是可以理解的——1978年h-BN尚无

bulk form in 1978—but it represents a factor-of-48,000 improvement in neutron absorption cross-section over beryllium (384 vs. 0.008 barns per atom).
块状形式——但它代表着中子吸收截面比铍提高了48,000倍（384 vs. 0.008 靶恩/原子）。

The borde ceramics $B_4C$ and $TiB_2$ emerge as the strongest overall candidates when all metrics are weighted equally. $B_4C$ is already used in nuclear reactor control rods and neutron shielding precisely because of its boron content, high hardness, and low density—the same properties that make it attractive for interstellar shielding.

当所有指标权重相等时，硼化物陶瓷 $B_4C$ 和 $TiB_2$ 成为综合性能最强的候选材料。$B_4C$ 因其硼含量、高硬度和低密度等特性，已被用于核反应堆控制棒和中子屏蔽，这些相同的特性也使其在星际屏蔽方面具有吸引力。

A notable result of this study is the high Voigt bulk moduli obtained for layered materials from JARVISDFT: 281 GPa for graphite and 245 GPa for h-BN. These values reflect the Voigt (upper bound) averaging of highly anisotropic elastic tensors, in which the extraordinary in-plane stiffness dominates. The Reuss (lower) bound, which would be more appropriate for estimating out-of-plane compressive response, yields values closer to the commonly cited ~30–40 GPa. For the in-plane impact loading relevant to dust shielding, the Voigt average may in fact be the more physically meaningful metric.

本研究的一个显著结果是，从 JARVISDFT 获得的层状材料的 Voigt 体积模量 (Voigt bulk moduli) 较高：石墨为 281 GPa，h-BN 为 245 GPa。这些值反映了高度各向异性弹性张量的 Voigt (上限) 平均值，其中卓越的面内刚度 (in-plane stiffness) 占主导地位。Reuss (下限) 值更适合估算面外压缩响应 (out-of-plane compressive response)，其结果接近通常引用的 ~30–40 GPa。对于与尘埃屏蔽相关的面内冲击载荷 (in-plane impact loading)，Voigt 平均值实际上可能是一个物理上更有意义的指标。

Several limitations warrant discussion:

有几个局限性值得讨论：

Temperature effects. Our screening uses room-temperature DFT elastic moduli. At the ~3 K ambient temperature of interstellar space, most ceramics will be harder and more brittle, while the sputtering physics may differ from room-temperature models.

温度效应。我们的筛选使用了室温下的 DFT (密度泛函理论) 弹性模量。在星际空间约 3 K 的环境温度下，大多数陶瓷将更硬、更脆，而溅射物理学 (sputtering physics) 可能与室温模型有所不同。

Radiation damage accumulation. We treat sputtering as a surface phenomenon, neglecting bulk radiation damage (displacement cascades, amorphization) that will degrade mechanical properties over the 49-year mission duration [7].

辐射损伤累积。我们将溅射视为一种表面现象，忽略了体积辐射损伤 (bulk radiation damage) (位移级联 (displacement cascades)、非晶化 (amorphization))，这些损伤将在 49 年的任务期间降低材料的机械性能 [7]。

$ALIGNN$ limitations. The $ALIGNN$ pretrained model fails dramatically for $B_4C$ (Fig. 5), predicting $K_V = 9$ GPa versus the DFT value of 228 GPa. This failure highlights a known limitation of GNN-based property predictors for structurally complex materials with large, low-symmetry unit cells that are underrepresented in training data.

$ALIGNN$ 的局限性。$ALIGNN$ 预训练模型在预测 $B_4C$ 时表现出显著的失效 (图 5)，预测的 $K_V = 9$ GPa，而 DFT 值为 228 GPa。这一失效凸显了基于 GNN (图神经网络) 的性能预测器在处理结构复杂、具有大尺寸、低对称性晶胞且在训练数据中代表性不足的材料时的一个已知局限性。

Manufacturing considerations. Our analysis assumes that candidate materials can be fabricated into ~500 m $^{2}$ shields of the required thickness. We note that manufacturing a 491 m $^{2}$ diamond shield remains an outstanding challenge.

制造考量。我们的分析假设候选材料可以被制造成所需厚度、面积约 500 m $^{2}$ 的屏蔽层。我们注意到，制造一个 491 m $^{2}$ 的金刚石屏蔽层仍然是一个尚未解决的挑战。

Scope of applicability. Our analysis assumes the existence of a spacecraft capable of reaching 0.12c, which we acknowledge has not yet been constructed. The primary bottleneck in implementing our recommendations is not materials selection but rather the development of a functioning fusion pulse drive—a challenge we leave to future work.

适用范围。我们的分析假设存在一个能够达到 0.12c 速度的航天器，我们承认该航天器尚未建成。实施我们建议的主要瓶颈不是材料选择，而是开发一个可运行的聚变脉冲推进器 (fusion pulse drive)——这一挑战我们留待未来工作解决。

# CONCLUSION / 结论

We have performed a systematic computational screening of 20 candidate materials for interstellar dust shielding, using DFT-computed mechanical properties from the JARVIS database (76,000 materials) with independent validation byALIGNN graph neural network predictions ($R^2 = 0.990$ for bulk modulus, excluding one outlier).

我们对 20 种星际尘埃屏蔽候选材料进行了系统性的计算筛选，使用了 JARVIS 数据库 (76,000 种材料) 中 DFT (密度泛函理论) 计算的机械性能，并通过 ALIGNN 图神经网络 (graph neural network) 预测进行了独立验证 (体积模量 (bulk modulus) 的 $R^2 = 0.990$，排除一个异常值)。

Our analysis demonstrates that 48 years of materials science progress since Project Daedalus have yielded multiple candidates that substantially outperform the original beryllium shield specification. The most promising finding is the identification of boron-containing materials—particularly h-BN, $B_4C$, and c-BN—as dual-function materials providing both mechanical protection and neutron radiation shielding. We propose a layered graphene/h-BN/HDPE/Al heterostructure that achieves a 47% mass reduction relative to the Daedalus beryllium design while adding neutron absorption capability entirely absent from the original.

我们的分析表明，自戴达罗斯计划 (Project Daedalus) 以来 48 年的材料科学进展已经产生了多种候选材料，它们大幅超越了原始铍屏蔽层的规格。最有前景的发现是确定了含硼材料——特别是 h-BN、 $B_4C$ 和 c-BN——作为双功能材料，既能提供机械防护，又能提供中子辐射屏蔽。我们提出了一种层状石墨烯/h-BN/HDPE/铝异质结构，相对于戴达罗斯计划的铍设计，它实现了 47% 的质量减轻，同时增加了原始设计中完全没有的中子吸收能力。

# ACKNOWLEDGMENTS / 致谢

We acknowledge that this work was submitted on April 1, 2026. While the research question addressed herein is of limited immediate practical relevance—owing primarily to the nonexistence of the spacecraft under consideration—all data, computational methods, and physical models presented are genuine and fully reproducible. The JARVIS-DFT dataset identifiers (Table II) and AIGNN pretrained model weights are publicly available, and we encourage skeptical readers to verify our results.

我们确认本工作于 2026 年 4 月 1 日提交。尽管本文所探讨的研究问题在实际应用上具有有限的即时相关性——这主要归因于所考虑的航天器尚不存在——但所有呈现的数据、计算方法和物理模型都是真实的且完全可复现。JARVIS-DFT 数据集标识符 (表 II) 和 AIGNN 预训练模型权重均已公开，我们鼓励持怀疑态度的读者验证我们的结果。

Y.L. and X.P. celebrate eight years of partnership since a fateful April Fools' Day in 2018, which began as a research excursion and proved considerably more consequential than either party anticipated. This paper is dedicated to that anniversary.

Y.L. 和 X.P. 庆祝自 2018 年一个命运般的愚人节以来八年的合作关系，那次合作始于一次研究考察，其意义远超双方预期。本文谨献给这个纪念日。

Y.L. and K.G. raise a glass to a bro's birthday month—April has always been kind to us.

Y.L. 和 K.G. 为兄弟的生日月举杯——四月总是对我们很友好。

The total computational cost of this study was approximately 2 CPU-hours, which represents roughly $10^{-10}$ of the estimated energy budget of the Daedalus spacecraft itself.

本研究的总计算成本约为 2 CPU-小时（中央处理器工作小时），这大约相当于戴达罗斯号飞船自身估算能源预算的 $10^{-10}$。

We thank Freeman Dyson (1923–2020) for articulating the possibility of interstellar transport, and the British Interplanetary Society for the engineering audacity of Project Daedalus.

我们感谢 Freeman Dyson (1923–2020) 阐明了星际运输的可能性，并感谢英国星际学会 (British Interplanetary Society) 在戴达罗斯计划 (Project Daedalus) 中展现的工程上的大胆设想。

May the Force be with you.

愿原力与你同在。

TABLE II. JARVIS-DFT identifiers and DFT-computed properties for all 20 screened materials. / 表 II. JARVIS-DFT 标识符和所有 20 种筛选材料的 DFT 计算属性。

|Material|JVASP ID|$K_V$|$K_V/\rho$|
|---|---|---|---|
|Be*|JVASP-14628|124.7|65.1|
|Al|JVASP-816|69.9|26.3|
|Ti|JVASP-14815|115.2|24.4|
|Fe|JVASP-882|201.4|24.5|
|W|JVASP-14830|305.2|16.2|
|Graphite|JVASP-48|281.0|124.1|
|Diamond|JVASP-91|437.4|125.0|
|h-BN|JVASP-62756|244.8|106.9|
|c-BN|JVASP-7836|378.2|109.2|
|MoS$_2$|JVASP-28733|70.6|14.6|
|WS$_2$|JVASP-72|74.3|10.0|
|MoSe$_2$|JVASP-57|57.6|8.6|
|WSe$_2$|JVASP-75|59.9|6.7|
|B$_4$C|JVASP-52866|228.0|92.2|
|SiC|JVASP-22633|213.2|67.6|
|TiB$_2$|JVASP-20096|254.8|57.0|
|ZrB$_2$|JVASP-19723|237.3|39.4|
|HfC|JVASP-17957|245.8|19.5|
|TaC|JVASP-20073|326.7|23.0|
|WC|JVASP-52591|342.5|20.7|

*bcc phase; hcp Be lacks elastic data in JARVIS.

*bcc 相（体心立方相）；hcp Be（六方密排铍）在 JARVIS 中缺乏弹性数据。

[2] G. R. Schmidt, J. A. Bonometti, and P. J. Morton, Nuclear pulse propulsion — Orion and beyond, in 36th AIAA/ASME/SAE/ASEE Joint Propulsion Conference (2000) aIAA 2000-3856.

[2] G. R. Schmidt, J. A. Bonometti, and P. J. Morton, 核脉冲推进——猎户座及超越, 载于 36th AIAA/ASME/SAE/ASEE 联合推进会议 (Joint Propulsion Conference) (2000) aIAA 2000-3856。

[3] A. Bond and A. R. Martin, Project Daedalus — the final report on the BIS starship study, J. Brit. Interplanet. Soc. 31, S1 (1978), supplement.

[3] A. Bond and A. R. Martin, 戴达罗斯计划——英国星际学会 (BIS) 星舰研究的最终报告, J. Brit. Interplanet. Soc. 31, S1 (1978), 增刊。

[4] K. F. Long and R. K. Obousy, Project Icarus: Son of Daedalus — flying closer to another star, J. Brit. Interplanet. Soc. 62, 403 (2009).

[4] K. F. Long and R. K. Obousy, 伊卡洛斯计划：戴达罗斯之子——飞向另一颗恒星, J. Brit. Interplanet. Soc. 62, 403 (2009)。

[5] A. R. Martin, Project Daedalus: Bombardment by interstellar material and its effects on the vehicle, J. Brit. Interplanet. Soc. 31, S116 (1978).

[5] A. R. Martin, 戴达罗斯计划：星际物质轰击及其对飞船的影响, J. Brit. Interplanet. Soc. 31, S116 (1978)。

[6] K. F. Long et al., Calculations of particle bombardment due to dust and gas in the interstellar medium on an interstellar probe, arXiv preprint (2023), 2307.12160.

[6] K. F. Long et al., 星际介质中尘埃和气体对星际探测器粒子轰击的计算, arXiv 预印本 (2023), 2307.12160。

[7] T. Hoang, A. Lazarian, B. Burkhart, and A. Loeb, The interaction of relativistic spacecrafts with the interstellar medium, Astrophys. J. 837, 5 (2017).

[7] T. Hoang, A. Lazarian, B. Burkhart, and A. Loeb, 相对论飞船与星际介质的相互作用, Astrophys. J. 837, 5 (2017)。

[8] C. Lee, X. Wei, J. W. Kysar, and J. Hone, Measurement of the elastic properties and intrinsic strength of monolayer graphene, Science 321, 385 (2008).

[8] C. Lee, X. Wei, J. W. Kysar, and J. Hone, 单层石墨烯弹性特性和本征强度的测量, Science 321, 385 (2008)。

[9] W. G. Fahrenholtz, G. E. Hilmas, I. G. Talmy, and J. A. Zaykoski, Refractory diborides of zirconium and hafnium, J. Am. Ceram. Soc. 90, 1347 (2007).

[9] W. G. Fahrenholtz, G. E. Hilmas, I. G. Talmy, and J. A. Zaykoski, 锆和铪的难熔二硼化物, J. Am. Ceram. Soc. 90, 1347 (2007)。

[10] S. A. Thibeault et al., Radiation Shielding Materials Containing Hydrogen, Boron, and Nitrogen: Systematic Computational and Experimental Study, Tech. Rep. (NASA, 2012) nIAC Phase I Final Report.

[10] S. A. Thibeault et al., 含氢、硼、氮的辐射屏蔽材料：系统计算与实验研究, 技术报告 (Tech. Rep.) (NASA, 2012) nIAC 第一阶段最终报告 (Phase I Final Report)。

[11] C. Harrison, S. Weaver, C. Bertelsen, E. Burgett, N. Herber, and E. Grulke, Polyethylene/boron nitride composites for space radiation shielding, J. Appl. Polym. Sci. 109, 2529 (2008).

[11] C. Harrison, S. Weaver, C. Bertelsen, E. Burgett, N. Herber, and E. Grulke, 用于空间辐射屏蔽的聚乙烯/氮化硼复合材料, J. Appl. Polym. Sci. 109, 2529 (2008)。

[12] T. Thomas, I. Orikasa, and A. Agarwal, Foam with direction: Unraveling the anisotropic radiation shielding properties of 2D boron nitride nanoplatelet foams, npj, 2D Mater. Appl. 8, 15 (2024).

[12] T. Thomas, I. Orikasa, and A. Agarwal, 有方向的泡沫：揭示二维氮化硼纳米片泡沫的各向异性辐射屏蔽特性, npj, 2D Mater. Appl. 8, 15 (2024)。

[13] Y.-K. Kim et al., High-density boron nitride nanotube composites via surfactant-stabilized lyotropic liquid crystals for enhanced space radiation shielding, Adv. Funct. Mater. 10.1002/adfm.202510716 (2025).

[13] Y.-K. Kim et al., 通过表面活性剂稳定的溶致液晶制备高密度氮化硼纳米管复合材料以增强空间辐射屏蔽, Adv. Funct. Mater. 10.1002/adfm.202510716 (2025)。

[14] K. Choudhary et al., The joint automated repository for various integrated simulations (JARVIS) for data-driven materials design, npj Comput. Mater. 6, 173 (2020).

[14] K. Choudhary et al., 用于数据驱动材料设计的各种集成模拟联合自动化存储库 (JARVIS), npj Comput. Mater. 6, 173 (2020)。

[15] K. Choudhary and B. DeCost, Atomistic line graph neural network for improved materials property predictions, npj Comput. Mater. 7, 185 (2021).

[15] K. Choudhary and B. DeCost, 用于改进材料属性预测的原子线图神经网络, npj Comput. Mater. 7, 185 (2021)。

[16] K. Choudhary, K. Garrity, and F. Tavazza, Rapid prediction of phonon structure and properties using the atomic line graph neural network (ALIGNN), Phys. Rev. Mater. 7, 023803 (2023).

[16] K. Choudhary, K. Garrity, 和 F. Tavazza, 使用原子线图神经网络 (ALIGNN) 快速预测声子结构和性质, Phys. Rev. Mater. 7, 023803 (2023).

[17] K. Choudhary, G. Cheon, E. Reed, and F. Tavazza, Elastic properties of bulk and low-dimensional materials using van der Waals density functional, Phys. Rev. B 98, 014107 (2018).

[17] K. Choudhary, G. Cheon, E. Reed, 和 F. Tavazza, 使用范德华密度泛函研究块体和低维材料的弹性性质, Phys. Rev. B 98, 014107 (2018).

[18] J. Drobny, A. N. Cohen, D. Curreli, P. Lubin, M. G. Pelizzo, and M. Umansky, Survivability of metallic shields for relativistic spacecraft, J. Brit. Interplanet. Soc. 73, 446 (2020).

[18] J. Drobny, A. N. Cohen, D. Curreli, P. Lubin, M. G. Pelizzo, 和 M. Umansky, 相对论性航天器金属屏蔽层的生存能力, J. Brit. Interplanet. Soc. 73, 446 (2020).

[19] S. F. Mughabghab, Thermal Neutron Capture Cross Sections, Resonance Integrals and g-Factors (International Atomic Energy Agency, 2003) iAEA Nuclear Data Services.

[19] S. F. Mughabghab, 热中子俘获截面、共振积分和g因子 (国际原子能机构, 2003) 国际原子能机构核数据服务.

[20] I. Orikasa et al., Smart foams: Boron nitride-graphene nanoplatelet foams for tunable radiation shielding and strain sensing, Adv. Mater. Technol. 9, 2400106 (2024).

[20] I. Orikasa 等人, 智能泡沫：用于可调谐辐射屏蔽和应变传感的氮化硼-石墨烯纳米片泡沫, Adv. Mater. Technol. 9, 2400106 (2024).