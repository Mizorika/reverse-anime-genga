# 生成与定向修订

## 生成提示词的组织顺序

不要只写“Japanese genga style”。把镜头方案转换成明确约束：

1. **参考与任务**：以给定截图为形状和构图依据，逆向为一张可读的动画原画工作稿。
2. **几何锁定**：写出有效画幅比例和重要接触点；框内大小、姿势、视线、相对位置不变。
3. **主体**：描述当前角色的辨识特征，明确哪些主要人物必须完整保留。
4. **省略**：点名本图应省掉的具体背景/纹理/重复装饰；说明哪些接触道具保留。
5. **框外计划**：逐侧列出要补的局部、自然结构终点和所需留白；大段缺失的身体不强行补全。
6. **素材和注释**：列出组字母与圈号的对象、采用哪几条短注释以及指向哪里；不要让生成模型自由填满文字。
7. **色线**：点名截图中重要影界和高光界的位置，避免笼统“添加红蓝线”。
8. **手写与覆盖**：要求一笔一划只画一次，松散不均匀而可辨认；交叉线保持连续。
9. **成图表面**：纯白、平面、无纸纹定位孔，无字幕水印。
10. **交付**：一个完成稿，避免多面板、教学海报、并排前后对比或自发拆成多张设定图。

可用的英文短约束（按需要嵌入，不必每次全部照抄）：
- A functional reverse-engineered animation key drawing sheet, with selective omission, not a sketch filter.
- Preserve the screenshot composition inside the inset camera frame. Expand the paper, not the camera framing.
- Complete the specified small cropped anatomical or clothing units beyond the frame; do not invent a full body or room.
- Sparse functional annotations, single-pass handwritten strokes, uneven size and spacing, naturally hurried but readable. No retracing, doubled contours, hollow lettering or jitter.
- Annotation ink is laid over the existing drawing. All original contour and color-trace lines remain uninterrupted beneath crossing leaders and letters. No white knockout, halo, erasure strip or label background.
- Keep the red highlight boundaries and blue shadow boundaries consistent with the source shapes; mostly unfilled white interiors.

## 图像工具的调用

使用当时可用的图像生成工具，先遵循其读取和参考图输入要求。只有用户要修订某张已生成图时，把该图作为主编辑参考；需要校正造型时同时参考原截图。不同工具的参数不要互相套用。

有本地图片时先查看；没有路径但图片在当前对话中时使用工具支持的会话图片引用。若工具无法访问旧图再取回文件；不要把不相关的最新图当作目标。缺少必要参考且不能获取时才请用户重新提供。

用户仅问“止め什么意思”“为什么分层”“编号怎么选”时，不生成新图。

## 定向修订模板

- **补画肘部**：保持框内人物和全部已有线稿不变，扩展指定侧纸面，延续两段手臂以形成一个自然弯肘；框仍切过手臂，完整肘部在框外；别改肩或手的位置。
- **修字**：只替换现有文字笔迹，保留原文字内容、组号、位置和指向；用单笔不均匀字，取消反复描线。不要给轮廓添乱线。
- **修白边**：保留注释位置，重建被其周围白色带误擦掉的黑轮廓与红蓝线，使其沿原切线连续穿过标注下方；指示线直接与底线相交。不能通过平移标签掩盖结构缺损。
- **补色线**：保留白底与全部造型，只恢复截图中实际影/高光边界；不重新上色，不改成彩色插画。
- **减层**：保留画面位置，把没有独立管理理由的嘴/泪/汗等并回所属人物，改正相关组号和引线；无需删除这些视觉形状。
- **省背景**：保持接触/遮挡所需边界，删减装饰和材质线；不要连同抓握道具或人物轮廓一起消失。

每次修订后再检查相邻部位、画框、色线和笔迹，防止局部修好却引入新的变化。不要把模型的提示词遵从承诺当成已经完成的视觉检查。
