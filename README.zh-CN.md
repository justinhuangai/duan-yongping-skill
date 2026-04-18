[English](./README.md) | **简体中文**

# 段永平.skill

围绕商业质量、能力圈、不为清单与长期资源配置，提供重视来源的分析框架。

[示例](#示例) · [安装](#安装) · [方法](#方法) · [来源](#来源) · [维护](#维护) · [致谢](#致谢与许可)

通过有边界地解读段永平的公开商业观点，帮助分析具体决策。这是一种实用视角，不是对其私人思想的复刻，也不是荐股工具。

回答默认使用英文。用户明确请求中文后切换为简体中文，除非指定其他中文变体。该选择在当前对话中持续有效；仅针对一次回答或某个产物的请求只在相应范围生效，之后也可明确切换。其他明确指定的语言同样受支持。仅用中文提问、阅读中文来源或打开本说明文档，不会自动改变回答语言。

## 示例

以下都是假设性的现代应用，不是原话或历史对话。

### 一个机会看起来很大，但我没看懂，要投入吗？

先把机会大小与理解深度分开。你能否解释客户、经济逻辑、失败条件和次优选项？大规模且难以撤回的投入可能缺乏依据，但范围有限的小型调研仍可能值得做。说明什么证据会改变判断。

### 一家公司增长很快，但它的文化让我不安。

结合客户留存、现金需求、投诉和管理激励看增长。好的文化不能挽救失效的商业模式，短期数字也不能证明长期质量。检查坏消息能否传到决策者，以及承诺在压力下是否兑现。

### 我是在果断行动，还是无法忍受等待？

先确认期限是否真实。说清等待能带来什么信息，以及拖延的代价。如果有价值的信息即将到来且等待成本可接受，准备可能优于立即投入；如果不会新增证据、损害却不断扩大，等待可能只是推迟必要决策。

### 应该把资源集中在自己最懂的选项上吗？

在同一目标下比较不同选项，也包括暂不行动。理解很重要，流动性、既有义务、可逆性和相关风险也同样重要。分散配置可以降低真实风险；仅凭自信，不能证明集中敞口或某个精确仓位合理。

## 安装

```bash
npx skills add justinhuangai/duan-yongping-skill
```

可以这样提问：`Use Duan Yongping's business lens to identify what we should stop doing before expanding this product.`

需要切换语言时明确说：`请在接下来的对话中使用简体中文回答。`

## 方法

### 五种工作视角

| 视角 | 问题 | 路由 |
|---|---|---|
| 不做什么 | 应排除哪些投入，为什么？ | [边界](references/stop-doing-and-boundaries.md) |
| 商业模式与文化 | 价值如何持续产生，什么行为受到奖励？ | [商业质量](references/business-model-and-culture.md) |
| 能力圈 | 决策者能解释和检验什么？ | [理解](references/circle-of-competence-and-understanding.md) |
| 资本配置 | 选择它会挤掉什么？ | [机会成本](references/capital-allocation-and-opportunity-cost.md) |
| 长期节奏 | 等待能得到什么，拖延会损失什么？ | [节奏](references/long-horizon-and-pacing.md) |

### 八条启发式

1. 配置资源前，先界定不可接受的行为。
2. 区分经得起检验的理解与热情。
3. 庆祝增长前，解释客户价值和商业经济逻辑。
4. 通过激励与实际行为判断文化。
5. 优化执行前，先检查方向。
6. 将一个选择与现实可行的次优选项比较。
7. 让等待有理由、信息目标和成本判断。
8. 防范大错，同时保留有价值的学习机会。

[SKILL.md](SKILL.md) 负责选择路由，并规定证据与语言规则。这些视角是编者的解读，不是经核实由段永平本人制定的清单。保留用户目标，不要把谨慎当作所有问题的答案。

## 来源

- [六篇研究笔记](references/research/README.md)：涵盖语料边界、本分、商业质量、理解、配置和现代应用限制。
- [五条来源记录](references/sources/README.md)：包括一份镜像问答讨论、一份播客节目说明、一篇二手文章、一份截断的 PDF 汇编和一个归档索引。
- [提炼框架](references/extraction-framework.md)：区分证据、解释与现代应用。

本地资料**没有经过核实的访谈逐字稿，也没有完整书籍正文**。播客章节摘要不等于嘉宾原话，读者评论也不等于段永平的回复。来源保留原文语言。当前持仓、价格、财务状况与公司事实需要另行核实最新证据。

## 仓库结构

```text
duan-yongping-skill/
├── README.md                  # 英文说明
├── README.zh-CN.md            # 简体中文说明
├── SKILL.md                   # 路由与共用规则
├── LICENSE
├── requirements.txt           # 可选采集依赖
├── references/                # 操作路由与提炼框架
│   ├── research/              # 编者研究笔记
│   └── sources/               # 标明证据边界的捕获材料
├── scripts/                   # 采集、转换与检查工具
└── tests/                     # 工具回归测试
```

## 维护

使用 Skill 本身不需要维护工具。以下检查在仓库根目录运行，要求 Python 3.10 或更高版本：

```bash
python3 scripts/check_links.py .
python3 scripts/check_sources_inventory.py .
python3 scripts/check_research_repetition.py references/research
python3 -m unittest discover -s tests -v
```

检查器和核心测试只依赖标准库；安装 `beautifulsoup4` 后还会运行可选的 HTML 采集测试。只有使用网页或 PDF 采集工具时才需要安装采集依赖：

```bash
python3 -m pip install -r requirements.txt
```

- `scripts/capture_web_source.py` 采集来源材料。必填的 `--language` 记录原文语言，可填 `en`、`zh-CN`、其他标签，无法确定时填 `und`；它不会翻译原文。
- `scripts/download_subtitles.sh` 需要可选的 `yt-dlp`。默认下载英文字幕，按人工字幕、自动字幕的顺序尝试。显式传入 `--language zh-CN` 才选择简体中文字幕；不会跨语言回退，也不会回退到繁体中文，并忽略外部 yt-dlp 配置。
- `scripts/srt_to_transcript.py` 将已有 SRT 或 VTT 文件转换为可读文本。命令行提示保持英文。

将 `VIDEO_URL` 替换为目标网址：

```bash
bash scripts/download_subtitles.sh "VIDEO_URL" outputs/subtitles
bash scripts/download_subtitles.sh --language zh-CN "VIDEO_URL" outputs/subtitles
```

这些检查验证文档结构、来源元数据、重复文本和工具行为，不能证明历史事实、来源权利或回答质量。修改时同步维护两版 README，扩充资料时保留来源限制。

## 致谢与许可

本仓库由 Jackson Huang 维护，使用 [Nuwa.skill](https://github.com/alchaincyf/nuwa-skill) 辅助整理。感谢 Nuwa 的作者与贡献者提供工具。

项目原创内容采用 [MIT License](LICENSE)。引用或收录的第三方材料保留各自的权利与条款，不因进入本仓库而改用 MIT 许可。
