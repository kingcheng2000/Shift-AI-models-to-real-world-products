# 二、机器学习项目过程

[1.概述 <--](/ch01_Overview.md) | [--> 3.机器学习项目团队组成](/ch03_ML-Teams.md)

## 项目的基本概念

本文的整体目标是偏向于ML的项目落地应用和交付，所以在正文的开篇，我觉得有必要先解释下“项目”和“项目管理”等知识点的基本概念，这样方便后续在一个语境内理解相关内容。

### 什么是项目

国际项目管理学（PMI，PMP考试就是PMI的认证）对项目的定义：***项目是为创造独特的产品、服务或成果而进行的临时性工作***。  

简短一句话，有几个重要的概念一定需要理解，否则很难理解项目管理的一些东西为什么那么要求。  

> **独特性**：正如没有两个片雪花是一样的，也没有两个项目是完全一样的，最直观的就是：客户、需求的不同。项目是需要交付特定的成果或者服务的，也就是说，项目是必须有目标的。  
> **临时性**：一定具有明确的“开始时间”和“结束时间”是项目的重要属性，所以项目**不是**一项持续不断的工作。当项目的目标实现，或者项目的目标已经明显无法实现，或者项目需求已经不复存在时，就意味着项目的结束。所以项目一定是三个结果：完成，失败，取消。需要注意的是，虽然项目是临时性工作，但项目但交付成果可以在项目结束后存在。  
> **渐进性**：因为项目需要交付的成果或者服务事先是不可见的，即使在项目前期“明确了项目目标”，但对于具体细节、成果、计划等内容的定义依然是“依靠经验粗略定义”，随着项目的推进，这些细节才能逐渐完善和明确。这一点对于项目的重要意义就是：项目过程中的变更是一定存在的。

### 什么是项目管理

PMI对于项目管理的定义：**将知识、技能、工具与技术应用于项目活动，以满足项目的要求。项目管理通过合理运用与整合特定项目所需的项目管理过程得以实现。项目管理使组织能够有效且高效地开展项目。**  

简单的理解就是：运用合理的资源，确保项目能够在规定时间内完成，并交付规定的可交付成果的过程。  

所以，一般认为项目管理三要素是：***时间、成本、质量*** ，也可以增加 ***范围*** 变为四要素。

### 项目管理过程组

PMI的定义：**启动过程组、规划过程组、执行过程组、监控过程组、收尾过程组**。  

项目经理进行项目管理的过程，就是依据 PMBOK 定义的五个过程组，并运用十个知识领域的49个知识点进行管理的过程。  

PMI 的 PMBOK 经过多年的修订改版，目前为第六版。五个过程组没有变化，知识领域增加“**项目相关方管理**”从九个变为十个，“相关方”在过去的版本里称之为“干系人”；对应的知识点也从经历了44个到47个到目前的49个变更过程。

### 项目生命周期

对项目过程一般通识定义为：项目前期 --> 项目开始 --> 项目组织与准备 --> 项目执行 --> 项目完成 。  

由于“项目前期”的主要工作是项目需求评估与论证，评估的结果有可能是项目不予立项，那么就没有后续的工作内容了，所以一般的对**项目生命周期**的定义为：项目开始 --> 项目组织与准备 --> 项目执行 --> 项目完成 。  

可能细心的朋友会发现：项目管理过程组有五个，而项目生命周期为何只有四个环节？原因其实非常简单，因为“监控过程组”是贯穿项目整个生命周期的。  

基于上述对“项目”的基本概念的介绍，下面我们来看看机器学习的项目生命周期。

## Lifecycle Of a ML Project

### 约定

本文探讨的是机器学习项目的落地过程，在继续之前需要做如下约定：  

> - 对项目的目标设定为：算法与软件集成的整体软件产品交付，而非仅交付model(s)或者APIs。  
> - 软件项目的交付，相关知识与方法已经非常成熟，本文仅对ML与软件的关键集成相关内容进行说明，不会过多涉及其他软件部分相关的项目过程；  
> - 同样，对于DevOps相关内容,如非必须也不会过多涉及；  

### 项目过程综述

如下图所示，黑虚线框中部分为项目中软件部分，如约定所述，此部分仅包含对关键内容的概括；红色虚线框中部分为项目中机器学习部分，也是本文关注的部分。  

![ch02-01](/res/ch02/ch02-01.jpeg)

可以看到，项目过程分为四个阶段，分别是：项目启动、数据收集、模型训练与调试、交付部署。  

事实上，在项目启动前还有“项目前期”这个阶段，依据不同的项目类型，具体内容会稍有不同。如果是内部应用项目，那么项目前期一般需要做需求可行性论证、效益分析、商业论证等项目立项准备工作；如果是向 B/G 客户交付的项目，那么项目前期一般是项目售前咨询、招投标等工作。  

对于内部应用项目，各企业的管理风格、资金储备、商业模式等的不同，项目立项的准备工作会相差比较大。对于内控严、合规性要求高的公司，一般会有严谨的流程去遵照执行；大多数公司可能会做一些讨论以及头脑风暴，再了解下同业公司的情况之后，做出决定；而对于有些公司，可能就是某个领导的“要求”，就会有部分精于企业生存之道的投机者去组织执行。所以，对于此类项目前期工作，本文不做讨论。  

对于需要向客户（最终用户）交付的项目，前期阶段的相关工作内容，如：项目售前咨询一般的过程、一些通用的方法、需要注意及规避问题、售前PPT的制作、演讲技巧，以及解决方案的如何编写等内容，会在本文[第五章](/ch05_Project-Consulting-and-Solutions.md)中详细介绍。  

#### 1.项目启动

一般来说，在项目启动后，企业内部需要做的第一件工作是：“**确定项目经理**”，因为项目启动后所有的工作都需要由项目经理去牵头、协调完成。对于“**大（金额大、意义重大）项目**”，一般还会同步成立PMO（Project Management Office）并设立“项目领导小组”。

> 特别的，对于一些B/G项目，尤其是 G 类的项目，一般在“投标阶段”就需要在投标文件中明确投标人选定的“项目经理”及“技术经理”人员及资质（简历）。中标后，也会将此项内容写入合同或技术协议文本中，并会对乙方（“投标人”、“乙方”这些属于标准名词：在投标阶段是投标人，中标签署合同后是乙方。）更换项目经理、技术经理的流程进行约定，一般原则都是可以“向上”更换。意思就是，乙方要换人可以，但是你要换的人必须是比合同中确定的人员资质、能力更高才行。为什么这么规定呢？这都是政企客户用“血泪教训”买来的经验：投标把公司最牛的人列为项目经理，以证明公司技术实力，中标后，项目经理甚至连项目启动会都没开，就换人了。  

考虑到人工智能领域的公司，大多为初创公司，处于产品孵化阶段的居多，也未成立专职的项目交付团队，由产品经理兼任或者转岗项目经理是比较合理的。所以，对于项目经理的工作内容一部分介绍会在本文[第四章](/ch04_Product-Manager's-Challenge.md)中与产品经理的工作内容共同说明。  

> 产品经理去做项目经理这种安排，并无什么不妥，希望广大产品经理看见后不要有什么意外，也不要担心，做好相关知识储备就好。  
>
> 说说我个人的经历吧：上午还在客户现场改PLC的代码逻辑和调试，中午接到电话让我立即回公司另有工作安排；回到公司后变成产品经理，去参与公司准备自主开发的软件产品的需求工作；产品需求完成后，开始配合研发完成产品测试；产品具备销售条件后，按公司新安排去做售前顾问，配合销售去“拿”项目；项目中标后，公司第一个自主产品的软件项目，产品我最熟悉，毫不意外我又变成了项目经理；然后在项目现场，借客户的会议室组织公司内部培训，培训销售经理、售前顾问、项目经理，中间还要溜出去带着“徒弟”去做售前；中标的项目多了，多个项目并行展开之后，我就“升职”为PMO，同时兼顾多个项目了。

总体来说，在项目启动阶段，在完成项目经理遴选后，主要的任务有如下五项。  

##### 1.1 - 定义项目目标

按照“项目”定义，项目是必须有目标的。所以，在项目启动之后，我们的第一个任务就是确定项目目标。对于政企（就是 to B/G 的项目，以下会依据上下文的语境，两种描述方式选择使用）类项目，项目目标其实说出来挺无聊的，那就是：合同内容。  

一般的，合同及技术协议文本都是非常严谨的，大到模块，小到功能点的描述，细到具体的技术指标，都会写的清清楚楚。估计会有人有这样的迷惑：“**白纸黑字的合同都签了，照着做就是了，还定义什么目标？**”，对于这样的疑惑，我只能说：***小同学，还是太年轻了，把事情想简单了***。一般而言，为了中标签合同（没有合同就没有收入，没有收入哪里有钱发工资，VC的钱总有烧完的那一天！）从售前到合同签定过程中，多少都会有一些内容是“不当承诺”，大白话就是“吹牛B”。在合同执行阶段，对于项目经理来说，这些“不当承诺”都属于风险管理中要严防死守的内容。  

“项目”的定义中，另一个重要的属性就是有明确的开始时间和结束时间。所以，不要奢望“等我做出来再交付”，时不我待只争朝夕，从项目开始第一天，就要有紧迫感。一方面，有上述的“不当承诺”的可能，另一方面，合同中要求的功能，公司内部不可能一点没有（啥都没有，正常操作，别想中标！非正常操作，也能中标，我什么都不知道，别问我为什么又能中标了），但是也不会全部都有。  

所以，定义项目目标的工作，就要从梳理合同、技术协议，厘清需求，定义优先级开始。  

##### 1.2 - 评估基线

在明确了机器学习任务后，首要需要考虑的应该就是“baseline”的问题。如果恰好有同类任务，那么这个任务的State-of-the-art就是基线，如果没有，那么就找类似的任务，让我们的技术专家，确定一个基线。  

##### 1.3- 定义指标

在对ML任务的基线有了认识后，建议结合合同中的条款“**理智**”的定义项目指标。  

为什么要“理智”？一方面State-of-the-art就是这样，你要超越，需要付出多少代价？另一方面，即便我们的metrics不是要超越State-of-the-art，为了多一个“9”需要付出多少代价？而且，这种代价显然不是线性的。  

而且，考虑到先阶段ML的特定领域的迭代速度是以月为单位的，也许运气好，我们定义的指标虽然“保守”，但是在后续训练过程中，来了一篇神论文，就帮了大忙。  

另外，对于生产部署，一定会有inference相关的技术指标，比如并发、速度，如果是实时视频的推理，还会有FPS的要求等。如果合同内明确了部署环境的说明，那么这些指标的可实现性就有明确的测算依据。如果，对于部署、推理环境没有明确说明，那么一定要提前沟通，不一定一次沟通就能定下来，但是大方向要清晰。GPU还是CPU还是FPGA，具体型号，配置。如果是实时视频的推理，还要明确是1080还是720或者更高，结合并发要求，测算一下网络环境的上行带宽够不够。不要等到交付部署了，前期测试也一切正常，正式使用了，发现网络给你一个小水管，还要你大并发。  

温习一下项目成功的四要素：***范围、时间、成本、质量***，所以，请时刻保持成本意识。杠精们也不需要抬杠，有没有不计成本的项目？肯定有，比如“Project Apollo”，这种国家意志驱动的项目，咱们不好比。记住，咱们是企业，企业就是要赚钱的，特殊项目，可以不赚钱，可以小赔本，但是总体上要赚钱这个事情天经地义，对于合理利润，没有什么不好意思说出来的。  

##### 1.4- 项目计划

项目内容和优先级明确了，关键指标也明确了，项目的时间合同上就已经明确了，是时候做项目计划了。如果计划出来后，发现“难度大，时间紧，任务重”，怎么办？  

成本允许范围内，多上人呗，能并行的就并行。  

刚从产品经理转到项目经理，不会排项目计划或者怕排的计划不科学怎么办？好办啊，做计划最简单的办法就是“倒推法”。一个团队中总有在不同领域“经验丰富”的选手，按照合同约定的项目交付时间，按照项目阶段，从后往前排就是了。每个阶段的持续时间怎么定？请教“经验丰富”的同事后，合理的“拍脑袋”呗。  

反复“拍脑袋”讨论之后，相信制定的项目计划已经具备很大的可执行性了。有些任务是可以并行的，有些任务是必须串行的，那么依据每个阶段的任务，尤其是串行任务容易变成“卡脖子”节点，那么就需要合理安排资源，是时候成立项目组了。

##### 1.5- 成立项目组

项目组成立后，任务明确，计划明确，合理分工，责任到人，该睡地板就睡地板，该996就996，项目就是这样，**Deadline**就在那里默默的看着你。你选择无视他，他就会让你后悔；你选择重视他，他也许会“隐身”。

有关项目团队成员组成的更详细的说明，在[第三章](/ch03_ML-Teams.md)做进一步解释。

有关**项目启动**先到这里，部分更详细的介绍在[第六章](/ch06_Project-or-Product-Setup.md)

#### 2.数据收集

事实上，现阶段的深度学习还是在比拼数据集规模的阶段。这一点，AI创业公司是能够理解的，但是对于转做深度学习的软件公司来说，可能有一个误区：“下一个开源数据集不就好了么？干嘛还要自己去准备数据集，费时、费力还费钱”。  

一方面，对于政企领域的特定任务来说，大概率是没有特定的开源数据集的，恰好有，那也非常小，可以拿来搞搞研究玩玩，但是想做到“生产就绪”，数据量是远远不够的。举个例子，给你一个中文语音到文字的NLP任务，去找找中文语料库看看够用不。  

另一方面，恰好有比较大的开源数据集，比方说“人脸”这么热闹，数据集不少，还有FaceNet、DeepFace、DeepID，是不是找两个程序员就可以做出来和“独角兽们”一样的“人脸”了？嗯，我也尝试过（匿了，匿了，说出来好丢人）。但是，“独角兽们”不会告诉你，他们用的数据集，比开源数据集，高一个数量级起步。再比如，人脸特征点，Dlib好啊，68点看起来不错把，唬唬行外人妥妥没问题，也有个小哥做了一个81点的放出来，你以为这就是State-of-the-art了？现在人脸特征点是96点起步，做到128点出门才好意思跟人打招呼，196点才能算是现阶段“比较领先的水平”。嗯，196点是有个**Helen dataset**，training + test 一共2330个数据，研究可以，商用想都别想。  

**开源一代，自用一代，研究一代**，这句话真的没有错。在这里建议从各个领域拥抱AI转向DL项目的的兄弟们，一定要给Boos说清楚数据集这件事。  

##### 2.1 指标验证

为什么还没有正式收集数据集，就要先验证？  

实际上，这个工作，在我们在评估基线和定义项目指标的时候，就可以同步开始去做了。毕竟项目不是莫名其妙从天上掉下来，在项目前期准备过程中，对于这个特定任务显然已经明确，一方面用户方会提供一些数据供验证与Poc测试，另一方面我们也会准备一些数据做可行性验证与制作演示Demo。  

这个阶段做的验证工作，真正要解决的问题是：  

> - 用小数据集，利用经验去评估指标实现的可能性和代价；
> - 通过误差分析（再建议一遍，不知道误差分析怎么做的，去看 Andrew Ng 的 Machine Learning Yearning）明确数据采集的策略和要求；
> - 基于误差分析，“炼丹师”仔细评估数据集，看看有没有可能在数据质量，标注上做点工作；
> - 基于小数据表现、经验、任务难度以及数据集采集难度，估算数据集规模；

##### 2.2 数据策略

上一步已经基于指标验证工作，对数据集的规模、采集要求、标注有了初步结论。那么就需要对所有的数据可能性，给出足够范例，然后项目经理明确对外包团队的数据要求、标准。当然，好多AI公司现在都有自己的数据标注团队了，这个事情做起来会相对靠谱的多。  

另外还有一点需要注意的就是，对于CV类的图片数据采集，一定要和生产环境使用的场景基本一致，不要为了凑数据数量而忽视了质量。  

##### 2.3 数据采集

这个暂时不多说，按照给出的范例去采集就好。

##### 2.4 数据标注

这就是个体力活，主要就是做好培训，然后就是早期多检查“Turk”的工作，确保标注准确性和符合要求。

##### 2.5 数据管理

此外，还有一个重要的事情是做好数据集的管理工作。一方面是保证数据安全，不能丢，更不能莫名其妙就泄漏出去。另一方面要有一个比较好的数据集管理策略，raw数据怎么管，标注后的怎么管，怎么做数据增强，数据集和训练数据怎么关联，毕竟“炼丹”遇到大麻烦，还是要回来看看数据集的。

有关数据收集更多的内容会在[第七章](/ch07_Data-Collection-Labeling-and-Management.md)做更详细的解释。

#### 3.训练与调试

训练与调试，这是做深度学习的基本功，这些做不好还谈什么项目落地，本文的定位是介绍项目落地相关的工作，这部分内容按理来说可以不关注。但是考虑到作为一个项目整体的一部分，训练与调试的目标是项目交付，而不是搞科研、发Paper，过程中关注的侧重点与思考方向会有所差异。  

##### 3.1 模型的MVP

MVP(Minimum Viable Product)是产品经理非常熟悉的一个概念，为什么在已经做了指标验证的情况下，还要提出用Simplest model 去做 model 的 MVP 呢？  

如果项目的任务是我们非常熟悉的领域，对于数据集、model选择、超参的经验值等这些都非常熟悉，那么可以忽略这一步工作，但是如果是一个从未做过的全新任务，那么“强烈建议”从这一步开始做起。选一个较小的数据集开始验证想法，一般把这种数据集叫做“Eyeball 开发集”，起步用一个“AlexNet like”的模型就可以，主要的任务就是能方便我们验证想法、思路，并做好误差分析，最终目标是确定一个可以Work的思路。  

##### 3.2 验证模型

在上一步，我们通过Eyeball 开发集，完成了误差分析，也确定了model的方向，从我们的training set中取一部分数据出来，用小一点的数据集做模型验证工作。具体这个数量是多少，因该按照具体任务确定，如果是简单的CV任务，我们要做的是fine-tuning工作，一个分类有100～200个样本应该就够了。这个阶段在关注精度的同时，也要同时考虑部署后的推理性能问题，避免解决了精度的指标而导致推理指标大幅超过目标值。  

用较小数据集做验证还有一个好处，可以用较短的时间完成一轮训练，那么就可以晚上让机器干活，白天我们根据结果进行调整，既不耽误时间也不会过多抢占GPU算力。  

验证阶段，解决了偏差问题，那么可以用全量training set开始训练了。  

##### 3.3 模型训练

在之前提到过，对于model来说，是**训练数据，权重，超参**一体化的，为了更好的调参、优化，在训练阶段我们需要有适当的工具做好相关内容的管理与记录。  

##### 3.4 模型优化

在优化方向的选择上，一方面我们要做好误差分析工作，另一方面要对误差的优化难度和优先级做好评估工作，其实就是一句话：在误差占比高的方向选择“成本、难度、时间”综合最经济的，先做优化。  

另外，对于模型精度的选择。查准和查全，不同的任务，不同的应用场景实际上要求是有区别的，不能用固化的思维去看待这个问题，只看F1 score来确定模型是否使用。还是拿“人脸”举个例子。  

假设我们训练完成后，排前两名的model在F1 score上相差不多，但是恰好A查准精度高，B查全精度高，如何选择呢？安全的选择肯定是F1 score那个高用那个，用理论支撑的工具做的选择，出了问题没责任。但这不一定是最优但选择，切记，一定要看场景但业务需求。如果是做“人证合一”的验证，业务的核心需求是“准确验证”，那么选择A是比较合适的；如果是做“人脸布控”，那么查全就非常重要了，所以选择B更合理，误报没关系，但是漏报就麻烦了。同理，大家可以思考下，在“张学友的演唱会”要做人脸布控追逃的话，又该怎么选？  

##### 3.5 软件集成

到这个阶段，业务相关的软件开发工作也基本完成了，是时候将ML与软件进行开发集成了测试了，Postman虽能解决集成测试问题，但是早投入模拟生产的集成测试，总是没有坏处的。  

有关训练与调试的更多内容，在[第八章](/ch08_Training-and-Debugging.md)会做更多的说明。

有关机器学习开发过程中，与软件开发DevOps的配合，以及一些专用工具或者软件平台的简单介绍，在[第十章](/ch10_ML-DevOps.md)。

#### 4. 部署

如果一切顺利，按照项目计划，到部署的时间节点就该去做生产试点部署了。当然了，就算有点不顺利，到了时间还是要去部署。而且，正常情况下，试点部署的时间只会比计划提前，很少会有推后的。你想啊，你小时候过年买了新衣服，是不是也想在年三十之前就穿啊？  

##### 4.1 开发环境测试

“谋定而后动，知止而有得”，所以我们要制订完备的项目计划，做好风险管理，知进退才能有期望中的收获。  

“不打无准备之仗，不打无把握之仗”，所以，在正式去客户现场部署之前，我们要在内部尽量去模仿一个最终部署形态的“env”环境。有条件、不缺钱计算资源多的公司，建议在开始关注政企市场的项目机会后，在“研发环境”、“测试环境”、“生产环境”之外，从基础设施平台中再独立出一个“交付部署测试环境”。  

有人可能会想，在开发过程中，已经做了软件集成及相关测试，为什么要增加工作量，不做这一步可以不？答案是：可以。为什么可以呢？因为只有吃过足够的苦头之后，就会长记性了，就知道这一步的重要性了。  

技术从业者是一个奇特的“物种”，讲起理论、概念、方法都可以做到滔滔不绝，各种新颖名词脱口而出，你要想全听懂，要么是专家，要么是全才，要么随时准备好Google。但是，干起活来，各种意想不到的Bug，奇葩的错误，诡异的意外，技术储备的欠缺等等情况，都有可能出现，你脑洞再大，也有出你意料之外的“惊喜”：  

- 内网部署，无互联网，依赖拉不下来，没法部署下去；  

- 家里测试没问题，到了现场跑不起来，各路高手轮番上阵排错，最后发现是有个对自家“基础环境”的小依赖忘了部署；  

- Nginx负载均衡玩的溜的很，结果用户有硬件负载均衡，还分链路和服务，要求不用Nginx用他们硬件实现LB，前期没问清楚，不会配置，傻眼了；  

- 客户指着地上放的纸箱子说“这是给你们准备的全新服务器，你们自己上架，自己做系统吧……”。什么是bond，什么是虚拟化，什么是SAN网络，我在哪？我要干什么？  

在家千日好，出门半朝难。充分演练，充分准备，没有任何坏处。  

##### 4.2 生产试点

先试点，再扩大，最后全面推广，这基本是标准规则。所有要动生产环境的事情，就是：小心，小心，再小心。  

##### 4.3 测试

最理想的情况是，客户恰好有生产测试环境，那么在生产测试环境做试点部署和测试，是最稳妥的，也是客户肯定会要求的。但是，如果没有生产测试环境呢？那么就一定要做好测试的准备工作，从用例到回滚到风险应对等的全套方案。而且，极其不建议在生产试点阶段的测试做回滚操作，这是增加风险的动作。最好的方式是，先单独测试ML部分，不和业务数据联动，ML部分验证没问题后，再做对接业务的测试，但对数据库是非CUD数据测试。  

##### 4.4 正式部署

项目走到这个阶段，大家都可以松一口气了。恭喜，恭喜。  

##### 4.5 监控

虽然可以松一个口起了，但是项目刚上线，还没有验收，千万不可大意，做好监控工作，定好Oncall的排班计划。谁都不希望出事，但是哪里有那么多心想事成但好事啊，做好预案，有了问题能快速解决更重要。  

有关部署的内容，在[第九章](/ch09_Deployment-and-Testing.md)会进一步说明一些注意事项和风险预防与规避策略。  

一般而言，对于政企项目，在部署环节开始后，就进入了正式的“交付实施过程”，项目经理在这个阶段压力是非常大的。当然，也有部分to G 的项目，要求合同签订项目正式启动后，就要项目组进场，“驻场”开发，这种项目对项目经理的能力要求是指数级上升的。  

由于国内软件行业传统的认识和人员的选用安排，项目经理、项目交付人员，无论从待遇上还是能力要求上，还是在内部的话语权上，都是相对同级别程序员较低的。事实上，大多公司都存在类似这样的认识：“实施，不就是去现场装个系统，教会客户使用么，有什么难的，干嘛要用那么“贵”的人？”。  

但是，实际情况是这样么？我们来看看ML的项目经理应该具备哪些能力：  

- 情商高。会和人打交道，而且还要具有快速和陌生人建立信任关系的能力；  

- 头脑灵活反应快，会说话，敢说话。给领导汇报，能三言两语说清楚；和项目相关方沟通，知道怎么说，能“听懂话”；  

- 快速判断能力。很多时候就是要在分钟级的时间单位内对一件事的难度、风险，是否答应，该不该答应等做出综合判断，并给出回复，而且还要不怕承担风险；否则用户就会觉得这个项目经理“不行”，什么事情都磨磨唧唧，什么事情都定不下来，失去信任感。项目经理一旦让客户失去信任感，基本这个项目做“砸”就是高概率了；  

- 快速学习能力。面对新进入的陌生领域，要能快速学习客户方业务知识，在需求沟通过程中才会收放自如；  

- 硬件、网络等IT综合知识。项目经理要在现场协调、沟通方方面面的工作内容，即使这些工作都有专业工程师配合完成，但是项目经理要都懂才能做好沟通、协调工作；  

- 对于CV类的项目，还要懂视频相关知识，以及工程施工的相关知识，否则人家摄像头给你配个H.265，你可能取流就要傻眼，摄像头怎么安装位置选择要清楚，POE是什么总要明白吧……；  

- 要有架构、写代码的能力。在客户现场，讨论需求、沟通变更或者和第三方集成，做技术沟通，没有这些基本功，怎么沟通，怎么初步判断工作量的量级？能不能判断出来别人是帮你还是害你？  

- 对于ML项目来说，还要有基本的深度学习技术相关知识。否则，客户问，速度这么慢，为什么你们不给我们上GPU？GPU不是能成倍的加速么。项目经理起码要知道训练和推理的计算量的区别吧，要知道反向传播吧，这样才能balabala的解释下吧。  

- 要有出众的语言组织能力。机器学习怎么能用“大白话”解释给客户；推理出了错，怎么和客户沟通才能让对方理解“这不是人工智障”；为了项目推进，需要想客户提要求的时候，怎么说才比较委婉、合情合理？  

- 风险意识和风险管理能力。

**三分软件，七分实施**绝对不是说着玩的，项目有一个好的项目经理带队，基本就已经成功一半了。所以，考虑到深度学习的技术难度和理解难度，建议在项目经理选派这件事上，真不要随意，更不要为了控成本，从这个方向开始下手。  

项目经理代表公司在客户现场做交付，项目做的好，用户满意，就是“活广告”；做不好，客户不会认为是项目经理能力不行，而会说“这个公司不行”，这里面的机会成本，各位决策者衡量衡量。  

有关项目经理和项目交付的更多内容，在[第十一章](/ch11_Project-Delivery.md)会做进一步详细介绍。

[1.概述 <--](/ch01_Overview.md) | [--> 3.机器学习项目团队组成](/ch03_ML-Teams.md)