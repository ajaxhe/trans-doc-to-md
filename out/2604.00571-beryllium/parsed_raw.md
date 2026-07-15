<!-- "type": "page-number", "value": 0 -->
arXiv:2604.00571v1 [cond-mat.mtrl-sci] 1 Apr 2026

#   Beyond Beryllium: AI-Accelerated Materials Discovery for Interstellar Spacecraft Shielding

Yue Li, $^{1}$ Xu Pan, $^{2}$ and Kaiyuan Guo $^{3}$

$^{1}$School of Materials Science and Engineering, Nanyang Interstellar University, Singapore 639798, Singapore

$^{2}$School of Artificial Intelligence, Nanyang Interstellar University, Singapore 639798, Singapore

$^{3}$Department of Medical Radiation Management and Hibernation, Shanghai Interstellar Jiao Tong University, Shanghai 200240, China

(Dated: April 1, 2026)

Project Daedalus (1973–1978), the most detailed interstellar probe design study ever conducted, specified a 9 mm beryllium erosion shield to protect the spacecraft payload during its 5.9 light-year cruise to Barnard's Star at 12% of the speed of light. This design, however, predated both the isolation of two-dimensional materials and the development of graph neural network (GNN) property predictors. Here, we systematically screen 20 candidate materials—spanning conventional aerospace metals, transition metal dichalcogenides, and ultra-high-temperature ceramics—using density functional theory (DFT) data from the JARVIS database (76,000 materials) with independent validation by the Atomistic Line Graph Neural Network (ALIGNN). We evaluate candidates across four criteria: specific mechanical stiffness ($K_V/\rho$), sputtering resistance, thermal neutron absorption cross-section, and thermodynamic stability. Our screening identifies hexagonal boron nitride (h-BN) and boron carbide ($B_4C$) as dual-function materials offering simultaneous mechanical protection and neutron radiation shielding, and we propose a graphene/h-BN/polymer layered heterostructure shield design that achieves an estimated 47% mass reduction relative to the original beryllium specification. These findings will become immediately actionable upon the successful development of fusion pulse propulsion, which we note remains an outstanding engineering challenge.

[IMAGE]
图片链接：/assets/39e6838a37e346ad9ddf2cceda0e04d9
图片标题：手持式光谱仪工作原理及石墨烯层结构示意图
图片描述：该图像是一幅手绘风格的科技示意图。左侧主体是一个类似手电筒的手持设备，从其前端圆形发光口处，发出大量向外扩散的波浪状线条（代表光线或能量束）以及一些小点（可能代表粒子或散射光）。设备的筒身有细节刻画，如环形纹理和一个侧面的小支架或开关。从设备前端引出一条粗大的箭头，指向右下方的一个圆形放大区域。该放大区域以剖面图的形式展示了材料的结构：最上层是密集的六边形网格结构，由许多小的白色圆圈（代表原子）和连接它们的黑色细线（代表化学键）组成，这典型地表示石墨烯或类似的二维材料。六边形网格下方是几层不同的结构：中间一层较为稀疏，也包含一些小圆圈；最底层则是由斜线填充的区域，表示基底或另一种材料。在放大区域的右侧边缘，可以看到'Ex'和'Em'的缩写，分别代表激发（Excitation）和发射（Emission），暗示了光谱分析的过程。整个图像的背景为浅米色，带有素描般的笔触感。结合其具体内容和潜在的上下文功能，这张图片旨在直观地说明手持式光谱分析设备如何通过发射能量束与材料（如石墨烯）相互作用，并可能通过分析其激发和发射特性来获取材料的微观结构信息。
[/IMAGE]

# Table of Contents Graphic: An interstellar probe encounters the ISM at 0.12c. Inset: layered heterostructure shield with graphene and h-BN nanostructures.

#   INTRODUCTION

The prospect of interstellar travel has motivated some of the most ambitious engineering studies in human history. In 1968, Dyson [1] articulated the fundamental energetics of interstellar transport, establishing that nuclear pulse propulsion could in principle accelerate a spacecraft to a significant fraction of the speed of light.

Project Orion (1958–1965) explored nuclear pulse propulsion using fission bombs before being curtailed by the Partial Test Ban Treaty [2]. The most comprehensive design study to date, Project Daedalus (1973–1978), proposed an unmanned probe propelled by inertial confinement fusion to reach Barnard's Star, 5.9 light-years distant, at a cruise velocity of 0.12c [3]. More recently, Project Icarus has sought to update the Daedalus concept with modern engineering knowledge [4].

A critical and often underappreciated challenge of relativistic spaceflight is the bombardment of the spacecraft by interstellar medium (ISM) particles. At 0.12c (3.6 × 10$^{7}$ m/s), even the tenuous ISM becomes a formidable particle beam. Martin's analysis for the Daedalus study [5] showed that over a 5.9 light-year transit through a region with particle density n ≈ 1 cm $^{-3}$, the frontal shield (area A ≈ 491 m$^{2}$) would encounter ≈ 2.7 × 10$^{25}$ particles, with individual protons carrying kinetic energies of ~6.7 MeV—well into the nuclear reaction regime. Larger dust grains, though far rarer, can deliver megajoule-scale impacts equivalent to macroscopic explosions [6, 7].

The Daedalus team's solution was a 9 mm beryllium erosion shield, selected for its combination of low density ($\rho = 1.85$ g/cm$^3$), reasonable bulk modulus ($K_V \approx 115$ GPa), and high sublimation energy ($E_{sb} = 3.36$ eV/atom) [3, 5]. However, this design was constrained to the materials knowledge of the 1970s. In the intervening half-century, materials science has undergone transformative advances: the isolation and characterization of two-dimensional materials beginning with graphene in 2004 [8]; the development of ultra-high-


<!-- "type": "page-number", "value": 1 -->
2

temperature ceramics (UHTCs) with extreme mechanical properties [9]; and the discovery that boron-containing materials provide exceptional neutron radiation shielding [10–13].

Equally transformative has been the rise of computational materials screening. The JARVIS (Joint Automated Repository for Various Integrated Simulations) database now contains density functional theory (DFT) calculations for over 76,000 materials [14], while graph neural network architectures such as the Atomistic Line Graph Neural Network (ALIGNN) enable rapid property prediction with near-DFT accuracy [15–17].

In this work, we leverage the JARVIS-DFT database and ALIGNN pretrained models to systematically re-evaluate the materials selection for interstellar dust shielding. We screen 20 candidate materials across three families—conventional aerospace metals, layered/two-dimensional materials, and ceramics/superhard compounds—against four performance metrics relevant to the Daedalus mission profile. We identify several materials that substantially outperform beryllium, propose a layered heterostructure shield concept, and discuss the implications for future interstellar mission design.

#   METHODS

##   Mission Parameters

We adopt the Daedalus Phase 2 mission profile [3]: cruise velocity $v = 0.12c = 3.6 \times 10^7$ m/s, distance to Barnard's Star $d = 5.9$ ly = $5.58 \times 10^{16}$ m, yielding a cruise time of ~49 years. The shield is modeled as a circular disk of radius $R = 12.5$ m (matching the Daedalus second stage diameter of 25 m), giving a frontal area $A = \pi R^2 \approx 491$ m $^{2}$.

The local ISM is modeled with particle number density $n = 1 \text{ cm}^{-3} (= 10^6 \text{ m}^{-3})$ and mean particle mass $\bar{m} = 1.29$ amu, appropriate for a hydrogen-dominated medium with ~10% helium by number. The total fluence on the shield surface over the mission is:

$$ \Phi = n \cdot d = 5.58 \times 10^{18} \text{ particles/cm}^2 \quad (1) $$

At 0.12c, the kinetic energy of a single proton is $E_p = \frac{1}{2}m_p v^2 \approx 6.7$ MeV (non-relativistic approximation; the Lorentz factor $\gamma = 1.0072$ introduces a <1% correction). This energy substantially exceeds typical sputtering thresholds (~10–100 eV) and surface binding energies (~3–9 eV), placing the bombardment firmly in the high-energy sputtering regime.

##   Material Screening Criteria

We evaluate each candidate material against four criteria:

(i) Specific mechanical stiffness, quantified by the ratio $K_V/\rho$ (GPa·cm $^{3}$/g), where $K_V$ is the Voigt bulk modulus and $\rho$ is the mass density. This metric captures the ability to resist mechanical deformation per unit mass—critical for minimizing shield mass while maintaining structural integrity under impact loading. We note that the Voigt average represents an upper bound on the true polycrystalline bulk modulus; for highly anisotropic layered materials (graphite, h-BN), this average includes the very stiff in-plane elastic constants and thus substantially exceeds the soft out-of-plane response. The Reuss (lower) bound for these materials would be significantly lower. Both bounds are reported where relevant.

(ii) Sputtering resistance, parameterized by the surface binding energy $E_{sb}$ (eV/atom). In the high-energy limit relevant to 0.12c bombardment, the sputtering yield scales approximately as $Y \propto 1/E_{sb}$ [18]. We employ a simplified model:

$$ Y = Y_{\text{ref}} \cdot \frac{E_{\text{ref}}}{E_{\text{sh}}} \quad (2) $$

with $Y_{ref} = 3$ atoms/ion at $E_{ref} = 4$ eV, consistent with the high-energy limiting behavior reported for metallic targets [18].

(iii) Thermal neutron absorption cross-section $\sigma_a$ (barns). While the primary ISM bombardment consists of fast particles, secondary neutron production within the shield itself, combined with the galactic cosmic ray background, makes neutron moderation an important secondary consideration. Materials containing boron-10 ($\sigma_a = 3,840$ barns) offer a dramatic advantage [10].

(iv) Thermodynamic stability, assessed via the energy above the convex hull ($E_{\text{hull}}$) from DFT calculations.

##   Material Data Sources

Elastic moduli ($K_V$, $G_V$), formation energies, and band gaps were obtained from the JARVIS-DFT database [14, 17], which provides DFT-computed properties using the OptB88vdW functional for over 76,000 materials. Each material is identified by a unique JVASP identifier (Table II), enabling full reproducibility. Thermal neutron cross-sections were taken from the NNDC/IAEA Nuclear Data compilation [19]. Surface binding energies were obtained from experimental sublimation enthalpy data.

As an independent validation, we performed property predictions using the ALIGNN pretrained models [15] (jv_bulk_modulus_kv_alignn and jv_shear_modulus_gv_alignn) on the same crystal


<!-- "type": "page-number", "value": 2 -->
3

structures retrieved from JARVIS. We note that beryllium is represented in the JARVIS database by its bcc phase (JVASP-14628, Im $\bar{3}$m), as the ground-state hcp phase lacks computed elastic tensor data in the current release.

#   Composite Figure of Merit

To enable single-metric ranking, we define a shield figure of merit:

$$ \text{FoM} = \frac{K_V}{\rho} \cdot E_{sb} \cdot (1 + \log_{10}(\sigma_a + 1)) \quad (3) $$

normalized such that Be = 1.0. This weighting treats mechanical performance, sputtering resistance, and neutron absorption as multiplicatively complementary properties. We note that different mission architectures may warrant alternative weightings.

#   RESULTS

#   Mechanical Properties

Figure 1 presents the Voigt bulk modulus $K_V$ and Fig. 2 the specific modulus $K_V/\rho$ for all 20 candidate materials. Among the ceramics, diamond ($K_V = 437$ GPa, JVASP-91), cubic boron nitride (c-BN, 378 GPa, JVASP-7836), tungsten carbide (WC, 342 GPa), and tantalum carbide (TaC, 327 GPa) exhibit the highest absolute stiffness. When normalized by density, diamond and graphite ($K_V/\rho \approx 125$ GPa·cm$^3$/g) dominate, followed by c-BN (109), h-BN (107), and $B_4C$ (92).

An important caveat applies to the layered materials. The JARVIS-DFT Voigt bulk moduli for graphite ($K_V = 281$ GPa, JVASP-48) and h-BN ($K_V = 245$ GPa, JVASP-62756) are substantially higher than the ~30–40 GPa values commonly cited in the literature. This discrepancy arises because the Voigt average is an upper bound that heavily weights the extremely stiff in-plane elastic constants ($C_{11} > 1,000$ GPa for graphene) while the interlayer response ($C_{33} \sim 30$–40 GPa) contributes less. The Reuss (lower) bound for these materials would be closer to the commonly cited values. For the shielding application considered here, the in-plane stiffness is arguably the more relevant metric, as dust grain impacts would load the shield primarily in-plane.

The layered transition metal dichalcogenides ($MoS_2$, $WS_2$, $MoSe_2$, $WSe_2$) exhibit uniformly low specific moduli (<15 GPa·cm$^3$/g), rendering them unsuitable as primary structural shielding materials.

[IMAGE]
图片链接：/assets/d62f83235ae44b49ae204a95ba31a07a
图片标题：不同材料的Voigt体模量对比柱状图
图片描述：该图片是一张水平柱状图，展示了多种材料的Voigt体模量Kv值（单位：GPa）。横轴表示Voigt体模量Kv的数值范围，从0到400 GPa，刻度间隔为100 GPa。纵轴列出了19种材料名称，从上到下依次为：Diamond, c-BN, WC, TaC, W, Graphite, TiB2, HfC, h-BN, ZrB2, B4C, SiC, Fe, Be, Ti, WS2, MoS2, Al, WSe2, MoSe2。柱状图的颜色编码位于图表右下角图例：蓝色代表Metals（金属），绿色代表2D / Layered（二维/层状材料），橙色代表Ceramics（陶瓷）。
具体数据点如下：
- Diamond (橙色)：约440 GPa
- c-BN (橙色)：约380 GPa
- WC (橙色)：约350 GPa
- TaC (橙色)：约330 GPa
- W (蓝色)：约310 GPa
- Graphite (橙色)：约280 GPa
- TiB2 (橙色)：约260 GPa
- HfC (橙色)：约250 GPa
- h-BN (绿色)：约240 GPa
- ZrB2 (橙色)：约220 GPa
- B4C (橙色)：约210 GPa
- SiC (橙色)：约200 GPa
- Fe (蓝色)：约180 GPa
- Be (蓝色)：约160 GPa
- Ti (蓝色)：约140 GPa
- WS2 (绿色)：约80 GPa
- MoS2 (绿色)：约70 GPa
- Al (绿色)：约60 GPa
- WSe2 (绿色)：约50 GPa
- MoSe2 (绿色)：约40 GPa
图中有一条垂直的虚线，位于横轴100 GPa的刻度位置。结合其具体内容和作为数据图表的通用功能，这张图片向读者直接传达的核心信息是：以直观的柱状图形式，对比了包括金属、二维/层状材料和陶瓷在内的19种常见材料的Voigt体模量Kv值，揭示了不同材料间体模量的显著差异，并通过颜色区分了材料类别，同时可能通过100 GPa的虚线提供了一个参考基准。
[/IMAGE]

# FIG. 1. Voigt bulk modulus $K_V$ of 20 candidate shielding materials (JARVIS-DFT). Dashed line: Be baseline.

#   Shield Mass Analysis

Figure 3 presents the erosion-adjusted shield mass for each material, computed by scaling the Daedalus reference thickness (9 mm) inversely with surface binding energy relative to beryllium ($E_{sb}^{Be} = 3.36$ eV), with a minimum structural thickness of 1 mm. The Daedalus beryllium erosion plate at 9 mm thickness serves as the baseline at 8.5 metric tons.

Several materials achieve significant mass reductions relative to beryllium: graphite (4.5 t, -47%), $B_4C$ (6.4 t, -24%), h-BN (6.6 t, -22%), and diamond (7.0 t, -17%). The color encoding in Fig. 3 reveals that h-BN and $B_4C$ simultaneously provide exceptional neutron absorption ($\sigma_a > 380$ barns per atom), a capability entirely absent from the beryllium baseline ($\sigma_a = 0.008$ barns).

At the other extreme, high-Z materials such as tungsten carbide (32.8 t), tungsten (31.5 t), and tantalum carbide (29.3 t) are unsuitable despite their excellent absolute mechanical properties, as their high densities translate to prohibitive shield masses.

#   Multi-Objective Screening

Figure 4 presents the two most critical performance axes—specific modulus versus thermal neutron


<!-- "type": "page-number", "value": 3 -->
4

[IMAGE]
图片链接：/assets/652c0d9d581e4efd9c2820ba503c0034
图片标题：不同材料比模量对比条形图
图片描述：该图表为横向条形图，用于比较多种材料的比模量 (Specific modulus Kv/ρ)。Y轴列出材料名称，从上到下依次为：Diamond (金刚石)、Graphite (石墨)、c-BN (立方氮化硼)、h-BN (六方氮化硼)、B4C (碳化硼)、SiC (碳化硅)、Be (铍)、TiB2 (二硼化钛)、ZrB2 (二硼化锆)、Al (铝)、Fe (铁)、Ti (钛)、TaC (碳化钽)、WC (碳化钨)、HfC (碳化铪)、W (钨)、MoS2 (二硫化钼)、WS2 (二硫化钨)、MoSe2 (二硒化钼)、WSe2 (二硒化钨)。X轴表示比模量，单位为 GPa·cm³·g⁻¹，刻度从0到120，每20为一个间隔。图中包含三种颜色的条形，分别代表不同类别的材料：蓝色代表 Metals (金属)，绿色代表 2D / Layered (二维/层状材料)，橙色代表 Ceramics (陶瓷)。每种材料对应一个水平条形，其长度表示该材料的比模量数值。图例中明确了颜色与材料类别的对应关系。图中还含有一条垂直的虚线，位于X轴刻度60和80之间，目测约在68左右的位置。具体数据来看：金刚石 (橙色) 的比模量最高，超过120；石墨 (绿色) 紧随其后，略低于120；立方氮化硼 (橙色) 约为108；六方氮化硼 (绿色) 约为105；碳化硼 (橙色) 约为92；碳化硅 (橙色) 约为68，其末端与垂直虚线对齐；铍 (蓝色) 约为65；二硼化钛 (橙色) 约为55；二硼化锆 (橙色) 约为38；铝 (蓝色) 约为22；铁 (蓝色) 约为20；钛 (蓝色) 约为18；碳化钽 (橙色) 约为16；碳化钨 (橙色) 约为14；碳化铪 (橙色) 约为12；钨 (蓝色) 约为10；二硫化钼 (绿色) 约为6；二硫化钨 (绿色) 约为3；二硒化钼 (绿色) 约为2.5；二硒化钨 (绿色) 约为1.5。该图表通过条形图的形式，清晰、直观地对比了包括金属、陶瓷、二维/层状材料在内的多种材料的比模量 (Kv/ρ)。其核心目的是帮助读者快速评估不同材料在比模量这一性能指标上的相对优劣，识别出高性能材料（如金刚石、石墨）和低性能材料（如某些二维材料），并为材料选择提供数据支持。垂直虚线的引入可能暗示了一个特定的比较基准或性能门槛。
图片OCR结果：$$ \begin{array}{l}\text{Diamond}\\\text{Graphite}\\\text{c-BN}\\\text{h-BN}\\\text{B}_4\text{C}\\\text{SiC}\\\text{Be}\\\text{TiB}_2\\\text{ZfB}_2\\\text{Al}\\\text{Fe}\\\text{Ti}\\\text{TaC}\\\text{WC}\\\text{HfC}\\\text{W}\\\text{MoS}_2\\\text{WS}_2\\\text{MoSe}_2\\\text{WSe}_2\end{array} \qquad\begin{array}{l}\text{Metals}\\\text{2D/Layered}\\\text{Ceramics}\end{array} $$
[/IMAGE]

# FIG. 2. Specific modulus $K_V/\rho$, the key mass-efficiency metric. Dashed line: Be baseline from the Daedalus design.

absorption—as a scatter plot with point size proportional to surface binding energy.

The Pareto front reveals three distinct high-performance regimes: (i) Pure mechanical excellence: diamond and graphite, with $K_V/\rho \approx 125$ but negligible neutron absorption. (ii) Balanced performance: $B_4C$ ($K_V/\rho = 92$, $\sigma_a = 614$ barns), c-BN and h-BN ($K_V/\rho \approx 107-109$, $\sigma_a = 384$ barns), and $TiB_2$ ($K_V/\rho = 57$, $\sigma_a = 513$ barns), combining strong mechanical properties with very high neutron absorption via their boron content. (iii) Radiation shielding specialists: $ZrB_2$ ($\sigma_a = 511$ barns) at moderate specific modulus.

Beryllium occupies a poor position in this space: moderate specific modulus (65) with essentially zero neutron absorption. Its selection in 1978 reflects the limited material options available, not optimization against modern multi-objective criteria.

#   ALIGNN Validation

Figure 5 presents parity plots comparing ALIGNN predictions with JARVIS-DFT values for bulk modulus $K_V$ and shear modulus $G_V$. Excluding $B_4C$, the agreement is excellent: $R^2 = 0.990$ and MAE = 4.4 GPa for $K_V$; $R^2 = 0.980$ and MAE = 6.8 GPa for $G_V$.

The B₄C outlier (JVASP-52866;ALIGNN predicts

# a

[IMAGE]
图片链接：/assets/d866cdc9a82e4eca87808b9574f25acd
图片标题：不同材料侵蚀调整后屏蔽质量的横向条形图
图片描述：该图为一张横向条形图，用于比较不同材料的侵蚀调整后屏蔽质量。图表的横轴表示“Erosion-adjusted shield mass (metric tons)”（侵蚀调整后屏蔽质量，单位为公吨），刻度范围从0到35，主要刻度标记为0, 5, 10, 15, 20, 25, 30, 35。纵轴列出了18种不同的材料名称，从上到下依次为：WC, W, TaC, Fe, WSe₂, HfC, MoSe₂, WS₂, MoS₂, Ti, ZrB₂, Al, TiB₂, c-BN, Be, SiC, Diamond, h-BN, B₄C, Graphite。每种材料对应一个水平条形。条形的长度表示其侵蚀调整后屏蔽质量。颜色表示“Thermal neutron σₙ (barns)”（热中子截面，单位为靶恩），右侧有一个垂直的颜色条作为图例，颜色从深红色（代表高值，约10⁻¹ barns）渐变到浅黄色（代表低值，约10⁻⁵ barns）。大部分条形的末端带有一个小方块标记，其颜色与条形颜色一致，对应热中子截面的数值。图中有一条垂直的虚线，旁边标注“Be baseline”（铍基线），该虚线位于横轴刻度7和8之间。大部分材料（如WC, W, TaC, Fe, WSe₂, HfC, MoSe₂, WS₂, MoS₂）的条形长度较长，屏蔽质量在10吨以上，其中WC最长，接近32.5吨。Ti, ZrB₂, Al, TiB₂, c-BN的屏蔽质量在7到16吨之间。Be, SiC, Diamond, h-BN, B₄C, Graphite的屏蔽质量较短，均在6吨以下。颜色方面，Fe, WSe₂, MoSe₂的条形呈现较深的红色，表明其热中子截面较高；WC, W, TaC, HfC, WS₂, MoS₂, Ti, Al, TiB₂, c-BN, Be, SiC, Diamond, h-BN, B₄C, Graphite的颜色则相对较浅，偏向黄色或橙色。该图表旨在直观比较18种不同材料的侵蚀调整后屏蔽质量和热中子截面，以帮助评估和选择适用于特定屏蔽应用的材料，其中WC表现出最高的屏蔽质量，而不同材料的热中子吸收能力通过颜色编码加以区分，并以铍（Be）的性能作为基线参考。
[/IMAGE]

# FIG. 3. Erosion-adjusted shield mass for a 5.9 ly mission at 0.12c. Bar color indicates thermal neutron absorption cross-section (color bar, log scale). Dashed line marks the beryllium baseline (8.5 t). Colored markers indicate material family.

[IMAGE]
图片链接：/assets/309850e52e5a4fc4a8fd02eadbf825a1
图片标题：材料的热中子吸收截面与比模量关系散点图
图片描述：这是一张二维散点图。横轴表示比模量Kv/ρ，单位是GPa·cm³·g⁻¹，采用对数刻度，范围从0到140。纵轴表示热中子吸收截面σa，单位是barns per atom（每个原子的靶恩），也采用对数刻度，范围从10⁻²到10⁴。图中包含多个数据点，每个点代表一种材料，并用不同的颜色和形状进行区分。根据图例，蓝色圆形代表金属，青绿色圆形代表2D层状材料，橙色圆形代表陶瓷，黑色星形代表基准线。此外，在图的右下角有石墨（Graphite）和金刚石（Diamond）两个标记点。图上标注了多种材料的缩写，包括：WSe₂, WS₂, MoS₂, Mo₂C, ZrB₂, Nb, TaC, HfC, Ti, TAC, Fe, SiC, TaB₂, B₄C, p-BN, Be (hexagonal), 以及一个黑色星形标记的基准线（Benchmark line）。右上角标注了'Plot size = δ_cu'。该图直观地展示了多种材料在热中子吸收能力和比模量方面的性能分布，旨在帮助读者快速识别和比较不同类别材料的特性，从而为特定应用（尤其是涉及中子与材料相互作用的领域）选择合适的材料提供依据。
[/IMAGE]

# FIG. 4. Multi-objective screening: specific modulus versus thermal neutron absorption cross-section. Point size is proportional to surface binding energy. Staircase line indicates the Pareto front. The gold star marks beryllium (Daedalus baseline).

$K_V = 9$ GPa versus DFT $K_V = 228$ GPa) is attributed to the structural complexity of the rhombohedral $B_{12}C_3$ unit cell (15 atoms, R$\bar{3}$m), which contains icosahedral $B_{12}$ clusters linked by C–B–C chains. This topology is rare in the ALIGNN training set, and the resulting graph representation may inadequately capture the inter-cluster bonding that governs the bulk elastic response.


<!-- "type": "page-number", "value": 4 -->
5

[IMAGE]
图片链接：/assets/47b841032f6a4cbfa357e8f83e2ccf49
图片标题：ALIGNN与JARVIS-DFT模型计算的体积模量(Kv)和剪切模量(Gv)预测值对比散点图
图片描述：图像包含两个并排的科学图表，分别标记为a和b。

**图表a（左侧）：**
*   **标题/主题：** 比较ALIGNN预测的Kv值与JARVIS-DFT计算的Kv值。
*   **X轴：** 标签为“JARVIS-DFT Kv (GPa)”，范围从0到约450 GPa，主要刻度间隔为100 GPa。
*   **Y轴：** 标签为“ALIGNN Kv (GPa)”，范围从0到400 GPa，主要刻度间隔为100 GPa。
*   **数据点与趋势线：**
    *   图中散布着多个圆形数据点，颜色各异。
    *   一条虚线对角线从坐标原点(0,0)延伸至右上角，表示理想情况下的完美拟合（即y=x）。
    *   图左上角有一个文本框，内含三行信息：
        *   "R² = 0.9892"
        *   "MAE = 18.3 GPa"
        *   "(train: Bi₂Cl)"
    *   图例中（位于图表下方，由彩色方块指示）：
        *   蓝色方块：Metals (金属)
        *   绿色方块：2D/Layered (二维/层状材料)
        *   橙色方块：Ceramics (陶瓷)
    *   图中标注了几个特定材料点：
        *   "Bi₂C"：一个橙色箭头指向一个位于x轴约220 GPa, y轴约70 GPa的数据点。
        *   "HfC"：一个标签指向一个数据点，该点约在x=200 GPa, y=220 GPa。
        *   "Graphite"：一个标签指向一个数据点，该点约在x=250 GPa, y=240 GPa。

**图表b（右侧）：**
*   **标题/主题：** 比较ALIGNN预测的Gv值与JARVIS-DFT计算的Gv值。
*   **X轴：** 标签为“JARVIS-DFT Gv (GPa)”，范围从0到500 GPa，主要刻度间隔为100 GPa。
*   **Y轴：** 标签为“ALIGNN Gv (GPa)”，范围从0到500 GPa，主要刻度间隔为100 GPa。
*   **数据点与趋势线：**
    *   图中散布着多个圆形数据点，颜色各异，分布趋势与图表a相似。
    *   一条虚线对角线从坐标原点(0,0)延伸至右上角。
    *   图左上角有一个文本框，内含三行信息：
        *   "R² = 0.9798"
        *   "MAE = 23.8 GPa"
        *   "(train: Bi₂Cl)"
    *   图例与图表a相同。
    *   图中标注了几个特定材料点：
        *   "Bi₂C"：一个橙色箭头指向一个位于x轴约120 GPa, y轴约50 GPa的数据点。
        *   "HfC"：一个标签指向一个数据点，该点约在x=200 GPa, y=210 GPa。
        *   "Graphite"：一个标签指向一个数据点，该点约在x=280 GPa, y=290 GPa。结合其具体内容和上下文功能，这张图片向读者直接传达的核心信息是：ALIGNN机器学习模型在预测材料的体积模量（Kv）和剪切模量（Gv）方面表现出高精度，与JARVIS-DFT计算结果高度吻合（R²值均接近0.98），且误差较小（MAE分别为18.3 GPa和23.8 GPa），证明了ALIGNN模型在这些材料属性预测任务上的有效性和可靠性。
[/IMAGE]

# FIG. 5. ALIGNN predictions versus JARVIS-DFT values for (a) $K_V$ and (b) $G_V$. $B_4C$ (inverted triangle) is an outlier due to structural complexity. Statistics exclude $B_4C$.

##   Layered Heterostructure Shield Concept

Based on our screening results, we propose a functionally graded layered shield (Fig. 6) in which each layer addresses a specific threat:

Layer 1: Graphene/graphite impact layer (~50 µm). The outermost layer exploits the extraordinary specific modulus of sp $^{2}$ carbon ($K_V/\rho = 124$ GPa·cm $^{3}$/g) and high sublimation energy (7.43 eV/atom) to absorb initial dust grain impacts and resist sputtering erosion.

Layer 2: h-BN neutron absorber (~2 mm). Hexagonal boron nitride serves dual duty: its boron-10 content ($\sigma_a = 3,840$ barns for $^{10}$B) efficiently captures secondary thermal neutrons, while its high Voigt bulk modulus ($K_V = 245$ GPa) provides mechanical reinforcement. NASA has independently validated BN-based materials for space radiation shielding [10, 12, 20].

Layer 3: HDPE cosmic ray moderator (~5 mm). High-density polyethylene, with its high hydrogen content, serves as a proton moderator for secondary cosmic ray particles, following established spacecraft shielding practice.

Layer 4: Aluminum structural support (~1 mm). A conventional aluminum backing provides structural mounting and thermal management.

The total heterostructure thickness of ~8 mm is comparable to the original 9 mm beryllium design, but the estimated total mass of ~4.5 metric tons represents a 47% reduction from the 8.5-ton beryllium baseline, while adding neutron absorption capability entirely absent from the original.

##   Figure of Merit Ranking

Table I presents the composite figure of merit for the top 10 candidates. The top-ranked materials—c-BN (FoM = 9.2), B₄C (9.1), h-BN (9.0), and TiB₂ (6.3)—all contain boron, reflecting the outsized contribution

[IMAGE]
图片链接：/assets/44ff64509e964f2aa772d2cef2875c12
图片标题：分层复合材料结构示意图：用于宇宙射线屏蔽与有效载荷保护
图片描述：该图是一个垂直堆叠的层状结构示意图。从上到下依次为：1. 顶层为黑色区域，标注为“Graphene / Graphite”，功能是“Impact absorption”（冲击吸收），并列出了材料参数“K_V/ρ = 124 GPa cm³ g⁻¹”和“E_coh = 7.4 eV/atom”。该层右侧标注厚度为“50 μm”。2. 第二层为浅灰色区域，标注为“h-BN”，功能是“Neutron absorber”（中子吸收剂），参数为“σ_a(B-10) = 3.840 barns”和“K_V = 245 GPa”，厚度标注为“2 mm”。3. 第三层为浅蓝色区域，标注为“HDPE”，功能是“Cosmic-ray moderator”（宇宙射线调节器），描述为“High H content | proton thermalization”，厚度标注为“5 mm”。4. 底层为灰色区域，标注为“Al”，功能是“Structural support”（结构支撑），参数为“K_V = 70 GPa”和“ρ = 2.7 g cm⁻³”，厚度标注为“1 mm”。顶部有红色箭头从“Interstellar medium (dust + cosmic rays)”指向第一层。底部有蓝色箭头从最后一层指向下方的“Payload”。右侧有两个文本框：上方橙色框为“Total”，内容是“~ 8 mm”和“~ 4.5 t”；下方白色框为“Daedalus”，内容是“9 mm Be”和“~ 8.5 t”。结合其具体内容和上下文功能，这张图片向读者直接传达的核心信息是：该文档提出了一种创新的分层复合防护结构，通过从上至下依次使用石墨烯/石墨（吸能）、氮化硼（中子吸收）、高密度聚乙烯（宇宙射线慢化）和铝（结构支撑）四层材料，旨在以约8mm总厚度和4.5吨总重量，为有效载荷提供比传统单层铍防护（9mm, 8.5t）更高效、更轻便的宇宙射线与微陨石综合防护方案。
[/IMAGE]

# FIG. 6. Proposed layered heterostructure shield concept. Each layer is optimized for a specific threat: dust impact absorption (graphene/graphite), neutron capture (h-BN), cosmic ray moderation (HDPE), and structural support (Al). Total mass represents a ~47% reduction relative to the Daedalus beryllium shield.

# TABLE I. Top 10 candidate materials ranked by composite figure of merit, normalized to Be = 1.0. All $K_V$ values from JARVIS-DFT.

|Material|$K_V/\rho$|$\sigma_a$ (b)|$E_{\text{sb}}$ (eV)|Mass (t)|FoM|
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

The original Daedalus beryllium (FoM $\equiv$ 1.0) is outperformed by 13 of 20 candidates, suggesting that the 1978 material selection was, charitably, suboptimal by modern standards.

#   DISCUSSION

Our screening reveals a striking finding: hexagonal boron nitride, a material whose radiation shielding properties have been extensively validated by NASA for low-Earth orbit applications [10–13], has apparently never been considered for interstellar shielding. This oversight is historically understandable—h-BN was not available in


<!-- "type": "page-number", "value": 5 -->
6

bulk form in 1978—but it represents a factor-of-48,000 improvement in neutron absorption cross-section over beryllium (384 vs. 0.008 barns per atom).

The borde ceramics $B_4C$ and $TiB_2$ emerge as the strongest overall candidates when all metrics are weighted equally. $B_4C$ is already used in nuclear reactor control rods and neutron shielding precisely because of its boron content, high hardness, and low density—the same properties that make it attractive for interstellar shielding.

A notable result of this study is the high Voigt bulk moduli obtained for layered materials from JARVISDFT: 281 GPa for graphite and 245 GPa for h-BN. These values reflect the Voigt (upper bound) averaging of highly anisotropic elastic tensors, in which the extraordinary in-plane stiffness dominates. The Reuss (lower) bound, which would be more appropriate for estimating out-of-plane compressive response, yields values closer to the commonly cited ~30–40 GPa. For the in-plane impact loading relevant to dust shielding, the Voigt average may in fact be the more physically meaningful metric.

Several limitations warrant discussion:

Temperature effects. Our screening uses room-temperature DFT elastic moduli. At the ~3 K ambient temperature of interstellar space, most ceramics will be harder and more brittle, while the sputtering physics may differ from room-temperature models.

Radiation damage accumulation. We treat sputtering as a surface phenomenon, neglecting bulk radiation damage (displacement cascades, amorphization) that will degrade mechanical properties over the 49-year mission duration [7].

$ALIGNN$ limitations. The $ALIGNN$ pretrained model fails dramatically for $B_4C$ (Fig. 5), predicting $K_V = 9$ GPa versus the DFT value of 228 GPa. This failure highlights a known limitation of GNN-based property predictors for structurally complex materials with large, low-symmetry unit cells that are underrepresented in training data.

Manufacturing considerations. Our analysis assumes that candidate materials can be fabricated into ~500 m $^{2}$ shields of the required thickness. We note that manufacturing a 491 m $^{2}$ diamond shield remains an outstanding challenge.

Scope of applicability. Our analysis assumes the existence of a spacecraft capable of reaching 0.12c, which we acknowledge has not yet been constructed. The primary bottleneck in implementing our recommendations is not materials selection but rather the development of a functioning fusion pulse drive—a challenge we leave to future work.

#   CONCLUSION

We have performed a systematic computational screening of 20 candidate materials for interstellar dust shielding, using DFT-computed mechanical properties from the JARVIS database (76,000 materials) with independent validation byALIGNN graph neural network predictions ($R^2 = 0.990$ for bulk modulus, excluding one outlier).

Our analysis demonstrates that 48 years of materials science progress since Project Daedalus have yielded multiple candidates that substantially outperform the original beryllium shield specification. The most promising finding is the identification of boron-containing materials—particularly h-BN, $B_4C$, and c-BN—as dual-function materials providing both mechanical protection and neutron radiation shielding. We propose a layered graphene/h-BN/HDPE/Al heterostructure that achieves a 47% mass reduction relative to the Daedalus beryllium design while adding neutron absorption capability entirely absent from the original.

#   ACKNOWLEDGMENTS

We acknowledge that this work was submitted on April 1, 2026. While the research question addressed herein is of limited immediate practical relevance—owing primarily to the nonexistence of the spacecraft under consideration—all data, computational methods, and physical models presented are genuine and fully reproducible. The JARVIS-DFT dataset identifiers (Table II) and AIGNN pretrained model weights are publicly available, and we encourage skeptical readers to verify our results.

Y.L. and X.P. celebrate eight years of partnership since a fateful April Fools' Day in 2018, which began as a research excursion and proved considerably more consequential than either party anticipated. This paper is dedicated to that anniversary.

Y.L. and K.G. raise a glass to a bro's birthday month—April has always been kind to us.

The total computational cost of this study was approximately 2 CPU-hours, which represents roughly $10^{-10}$ of the estimated energy budget of the Daedalus spacecraft itself.

We thank Freeman Dyson (1923–2020) for articulating the possibility of interstellar transport, and the British Interplanetary Society for the engineering audacity of Project Daedalus.

May the Force be with you.


<!-- "type": "page-number", "value": 6 -->
7

# TABLE II. JARVIS-DFT identifiers and DFT-computed properties for all 20 screened materials.

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

[2] G. R. Schmidt, J. A. Bonometti, and P. J. Morton, Nuclear pulse propulsion — Orion and beyond, in 36th AIAA/ASME/SAE/ASEE Joint Propulsion Conference (2000) aIAA 2000-3856.

[3] A. Bond and A. R. Martin, Project Daedalus — the final report on the BIS starship study, J. Brit. Interplanet. Soc. 31, S1 (1978), supplement.

[4] K. F. Long and R. K. Obousy, Project Icarus: Son of Daedalus — flying closer to another star, J. Brit. Interplanet. Soc. 62, 403 (2009).

[5] A. R. Martin, Project Daedalus: Bombardment by interstellar material and its effects on the vehicle, J. Brit. Interplanet. Soc. 31, S116 (1978).

[6] K. F. Long et al., Calculations of particle bombardment due to dust and gas in the interstellar medium on an interstellar probe, arXiv preprint (2023), 2307.12160.

[7] T. Hoang, A. Lazarian, B. Burkhart, and A. Loeb, The interaction of relativistic spacecrafts with the interstellar medium, Astrophys. J. 837, 5 (2017).

[8] C. Lee, X. Wei, J. W. Kysar, and J. Hone, Measurement of the elastic properties and intrinsic strength of monolayer graphene, Science 321, 385 (2008).

[9] W. G. Fahrenholtz, G. E. Hilmas, I. G. Talmy, and J. A. Zaykoski, Refractory diborides of zirconium and hafnium, J. Am. Ceram. Soc. 90, 1347 (2007).

[10] S. A. Thibeault et al., Radiation Shielding Materials Containing Hydrogen, Boron, and Nitrogen: Systematic Computational and Experimental Study, Tech. Rep. (NASA, 2012) nIAC Phase I Final Report.

[11] C. Harrison, S. Weaver, C. Bertelsen, E. Burgett, N. Herber, and E. Grulke, Polyethylene/boron nitride composites for space radiation shielding, J. Appl. Polym. Sci. 109, 2529 (2008).

[12] T. Thomas, I. Orikasa, and A. Agarwal, Foam with direction: Unraveling the anisotropic radiation shielding properties of 2D boron nitride nanoplatelet foams, npj, 2D Mater. Appl. 8, 15 (2024).

[13] Y.-K. Kim et al., High-density boron nitride nanotube composites via surfactant-stabilized lyotropic liquid crystals for enhanced space radiation shielding, Adv. Funct. Mater. 10.1002/adfm.202510716 (2025).

[14] K. Choudhary et al., The joint automated repository for various integrated simulations (JARVIS) for data-driven materials design, npj Comput. Mater. 6, 173 (2020).

[15] K. Choudhary and B. DeCost, Atomistic line graph neural network for improved materials property predictions, npj Comput. Mater. 7, 185 (2021).

[16] K. Choudhary, K. Garrity, and F. Tavazza, Rapid prediction of phonon structure and properties using the atomic line graph neural network (ALIGNN), Phys. Rev. Mater. 7, 023803 (2023).

[17] K. Choudhary, G. Cheon, E. Reed, and F. Tavazza, Elastic properties of bulk and low-dimensional materials using van der Waals density functional, Phys. Rev. B 98, 014107 (2018).

[18] J. Drobny, A. N. Cohen, D. Curreli, P. Lubin, M. G. Pelizzo, and M. Umansky, Survivability of metallic shields for relativistic spacecraft, J. Brit. Interplanet. Soc. 73, 446 (2020).

[19] S. F. Mughabghab, Thermal Neutron Capture Cross Sections, Resonance Integrals and g-Factors (International Atomic Energy Agency, 2003) iAEA Nuclear Data Services.

[20] I. Orikasa et al., Smart foams: Boron nitride-graphene nanoplatelet foams for tunable radiation shielding and strain sensing, Adv. Mater. Technol. 9, 2400106 (2024).