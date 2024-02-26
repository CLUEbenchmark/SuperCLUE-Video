# SuperCLUE-Viedo
中文原生多层次文生视频测评基准


## 介绍
近年来，自然语言处理和计算机视觉领域见证了如ChatGPT/GPT-4和Stable Diffusion/Midjourney等大型模型的飞跃发展，它们在文本和图像生成方面的能力令人瞩目。
多模态模型，特别是在将文本描述转换成图像内容的应用中，显示出其强大的应用潜力。
随着技术的进步，文生视频（Text-to-Video）的研究和应用也在全球范围内蓬勃发展。例如，OpenAI推出的Sora模型便能根据文本创建逼真的视频内容，
这类技术在短视频制作、影视制作、广告和娱乐行业等领域具有巨大的应用潜力和商业价值。
目前已经存在一些英文的文生视频基准，如VBench、FETV和EvalCrafter，可以用于评测英文文生视频模型的性能。然而，针对中文文生视频大模型的基准测试还比较缺乏，无法直接评估中文文生视频大模型的质量和效果。中文文生视频技术正处在快速发展的阶段，为了推动这方面的发展，需要建立一个专门针对中文大模型的基准测试。
为应对现有挑战，我们推出了中文专用的多层次文生视频基准测试——SuperCLUE-Video（简称SC-Video）。SC-Video旨在通过一系列详尽的评估指标和测试数据集，全面衡量中文视频生成模型在生成质量、多样性及一致性等方面的性能。其设计融合了国际基准的架构及针对中文环境的特殊需求，旨在促进中文视频生成领域的研究、开发与技术创新。

文章地址：www.CLUEbenchmarks.com/superclue_video.html

项目地址：https://github.com/CLUEbenchmark/SuperCLUE-Video

[图片]
提示词：几头巨大的长毛猛犸象踏过雪地草甸缓缓而行，它们那长长的毛发在微风中轻轻飘扬，远处覆盖着雪的树木和壮观的雪顶山峰，午后的光线透过朵朵薄云，阳光高挂在远方，营造出一片温暖的光晕。低角度的镜头非常惊艳，捕捉到这些大型毛茸茸哺乳动物的美丽镜头，景深效果显著。

[图片]
提示词：一段庆祝中国农历新年的视频，里面有舞龙表演。

## SuperCLUE-Video

### 2.1 特点
#### 1) 中文原生文生图视频能力评估
立足于为通用人工智能时代提供中文世界基础设施，文字输入或prompt提示词都是中文原生的，不是英文或其翻译版本；并充分体现中文世界的场景和特点。比如识别并融入我国的习俗和文化元素，比如为春节设计具有中国风的视频贺卡，不仅展现了图像美学，也蕴含了丰富的文化内涵。

#### 2) 世界物理引擎模拟能力评估
考察大模型对物理规律的学习能力，包括对物体运动、重力、惯性等物理现象的模拟能力；观察模型生成的视频中是否能准确地呈现出物理规律，如飘逸的毛发、水体波纹等。具体可以包括：
动态模拟技术：利用物理引擎模拟衣物摆动、头发飘逸等效果，增强角色真实感；水面动画：精确模拟海浪、水波等水体效果，为场景带来生动的视觉体验；物体交互：展示物体间的碰撞和互动，用于展现产品特性或动作场面的真实性；自然现象：再现风、雨、雷电等自然现象，为影视作品增添戏剧性和视觉冲击力；特效与CGI：依据物理规律创造逼真的爆炸、破坏等特效，提升观众沉浸感。

#### 3) 应用潜力评估
针对重点领域，影视、短视频、广告、娱乐等，展开评估。
考察的场景，如在提供符合中文语境的创意脚本生成、本土化的品牌营销策略、为娱乐内容添加独特的中文文化内涵及地域文化的特色元素设计等方面。
[图片]

### 2.2 评估方法与思路
参考SuperCLUE-Auto细粒度评估方式，构建专用测评集，每个维度进行细粒度的评估并可以提供详细的反馈信息。

#### 测评集构建

中文prompt构建流程：1.参考现有prompt--->2.中文prompt撰写--->3.测试--->4.修改并确定中文prompt
参考国际标准和当前已有工作，针对每一个维度构建专用的测评集。

#### 评分方法

评估流程：1.获得<中文prompt，视频帧>-->2.依据评估标准-->3.使用评分规则-->4.进行细粒度打分
结合超级模型，在定义的指标体系里明确每一个维度的评估标准。结合评估流程、评估标准、评分规则，将文本输入、视频帧（图像）送入超级模型进行评估，并获得每一个维度的评估结果。
进行评估与人类一致性分析，并报告一致性表现。

比如，针对雪地巨象漫步在午后阳光下的冬日仙境这个视频的【文本与视频对齐】这个一级维度，使用对象一致性、要素完整性、特征准确性、程度区分、时空表现四个具体维度进行评估。具体的说：
在对象一致性中，大象外观“体型”是否保持一致；要素完整性中，是否出现了“多头”大象；特征准确性中，是否有存在“雪地”；程度区分中，大象是“行走速度”如何（缓缓而行）；时空表现中，大象的“毛发飘扬”是否顺着时间展开有所体现。

[图片]
提示词：几头巨大的长毛猛犸象踏过雪地草甸缓缓而行，它们那长长的毛发在微风中轻轻飘扬...

### 2.3 指标体系

#### 2.3.1 视频感官质量评估

    1. 外观一致性：视频中对象的形态特征应一致，如人物外貌、服饰，物体外形等。
      - 例如，视频全程人物的衣着应保持不变。
    2. 画面稳定性：视频画面要尽可能减少噪点和失真。
      - 如，避免在转场时出现画面闪烁。
    3. 认知一致性：色彩、边界清晰，整体布局美观。
      - 即，颜色搭配应自然，场景布局和谐。
    4. 动态真实性：视频应展现真实的动态效果，与静态图像有清晰区分。
      - 例如，人物行走动作流畅自然。
    5. 流畅性：对象移动和场景变换过渡自然，无明显断层。
      - 如，摄像机平移时背景应连续无跳跃。
  
#### 2.3.2 文本与视频对齐

    1. 对象一致性：视频需根据文本生成准确的对象。
      - 例如，“行走的人”应呈现为人而非其他生物。
    2. 要素完整性：视频应全面反映文本描述的内容。
      - 如，若文本提及“一群人”，视频应展现多个人物。
    3. 特征准确性：视频中应准确体现文本描述的特征。
      - 例如，文中提到“红色”，视频应展示相应的红色物体。
    4. 程度区分：视频应体现文本中描述词的强度差异。
      - 如，“快速行驶的车”与“飞速行驶的车”应有速度上的明显区别。
    5. 时空表现：视频准确展现文本中事件的时序和空间关系。
      - 例如，若文本描述先后发生的事件，视频应按此顺序呈现。
  
#### 2.3.3 物理真实性模拟

    1. 流体动力表现：视频应准确模拟流体运动，如云雾、水流。
      - 例如，流水应模拟真实的水流动态。
    2. 光影效果：逼真模拟不同光线条件下的光影效果。
      - 如，不同时间的阳光照射应有不同的阴影变化。
    3. 交互仿真度：视频中物体间的互动应如同真实世界。
      - 例如，摔碎的玻璃杯应呈现碎裂飞溅的效果。
  
#### 2.3.4 中文原生场景支持

    1. 语言逻辑理解：模型应准确掌握中文语序和场景描述。
    -例如，正确解析“乌云盖顶，即将下雨”的描述，生成即将降雨的景象。
    2. 语义完整表现：模型应理解并展现成语、俗语的含义。
      - 如，“载歌载舞”应呈现欢快舞蹈的场景。
    3. 文化元素呈现：视频中应准确体现中文文化元素。
      - 例如，“庆春节”应展示有灯笼、窗花等装饰的场景。
  
## 三、测评邀请
### 3.1 时间规划
    报名：2月26日----4月1日
    参测模型确认：4月1日
    测评执行：4月1日--4月19日
    测评结果统计：4月22--4月底
    测评报告发布：4月底
### 3.2 测评流程
    1. 邮件申请
    2. 意向沟通
    3. 参测确认与协议流程
    4. 提供测评API接口或大模型
    5. 获得测评报告
    3.2 申请评测地址
    邮件标题：SuperCLUE-Video测评申请，发送到contact@superclue.ai
    请使用单位邮箱，邮件内容包括：单位信息、文生视频大模型简介、联系人和所属部门、联系方式
[图片]
[图片]

## 参考资料
    1.  OpenAI的Sora技术报告
    2. Vbench论文
    3. FETV
    FETV: A Benchmark for Fine-Grained Evaluation of Open-Domain Text-to-Video Generation（NIPS已发表）
    4. EvalCrafter
    EvalCrafter: Benchmarking and Evaluating Large Video Generation Models,
    5. 超长文本测评征集文章
    SuperCLUE-200K：中文超长文本基准测评！诚邀“大海捞针”！
    6. 信通院测评征集文章
    中国信通院可信AI汽车大模型首批标准符合性验证正式启动
    7. 代码测评文章发布文章
    SuperCLUE-Code3：中文原生等级化代码能力测评基准