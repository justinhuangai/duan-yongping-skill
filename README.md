**English** | [简体中文](./README.zh-CN.md)

# Duan Yongping.skill

A source-aware framework for business quality, competence boundaries, stop-doing decisions, and long-term resource allocation.

[Examples](#examples) · [Installation](#installation) · [Method](#method) · [Sources](#sources) · [Maintenance](#maintenance) · [Credits](#credits-and-license)

Use a disciplined interpretation of Duan Yongping's public business ideas to examine a decision. This is a practical lens, not a reconstruction of his private mind or a stock recommender.

Responses default to English. An explicit request for Chinese switches to Simplified Chinese unless another variant is specified. The choice persists for the conversation unless limited to one answer or artifact, or changed later. Other explicitly requested languages are honored. A Chinese prompt, source, or README alone does not change the response language.

## Examples

These are hypothetical modern applications, not quotations or historical dialogue.

### An opportunity looks large, but I do not understand it. Should I commit?

Separate the size of the opportunity from the quality of your understanding. Can you explain the customer, economics, failure conditions, and next-best alternative? A large irreversible commitment may be unjustified while a small, bounded investigation is worthwhile. State what evidence would change the decision.

### A company is growing quickly, but its culture worries me.

Compare the growth with customer retention, cash demands, complaints, and what managers reward. A strong culture cannot rescue a broken business model, and good short-term numbers cannot establish durable quality. Investigate whether bad news reaches decision makers and whether promises survive pressure.

### Am I being decisive, or am I uncomfortable with waiting?

First check whether the deadline is real. Identify what waiting could reveal and what delay could cost. If useful information is coming at acceptable cost, preparation may beat immediate commitment. If no new evidence is expected and harm is growing, waiting may simply postpone a necessary decision.

### Should I concentrate resources on my best-understood option?

Compare alternatives under the same objective, including doing nothing. Understanding matters, but so do liquidity, obligations, reversibility, and correlated failure. Diversification can reduce real risk. Confidence alone does not justify concentrated exposure or a precise portfolio weight.

## Installation

```bash
npx skills add justinhuangai/duan-yongping-skill
```

Try: `Use Duan Yongping's business lens to identify what we should stop doing before expanding this product.`

To change languages explicitly: `Please answer in Simplified Chinese for the rest of this conversation.`

## Method

### Five working lenses

| Lens | Question | Route |
|---|---|---|
| Stop doing | Which commitments should be excluded, and why? | [Boundaries](references/stop-doing-and-boundaries.md) |
| Business model and culture | How does value recur, and what behavior is rewarded? | [Business quality](references/business-model-and-culture.md) |
| Circle of competence | What can the decision maker explain and test? | [Understanding](references/circle-of-competence-and-understanding.md) |
| Capital allocation | What does choosing this displace? | [Opportunity cost](references/capital-allocation-and-opportunity-cost.md) |
| Long-horizon pacing | What does waiting buy, and what does delay cost? | [Pacing](references/long-horizon-and-pacing.md) |

### Eight heuristics

1. Define unacceptable actions before allocating resources.
2. Separate demonstrated understanding from enthusiasm.
3. Explain customer value and business economics before celebrating growth.
4. Examine culture through incentives and actual conduct.
5. Check direction before optimizing execution.
6. Compare a choice with its realistic next-best alternative.
7. Give waiting a reason, an information target, and a cost.
8. Protect against large mistakes without refusing useful learning.

[SKILL.md](SKILL.md) selects a route and defines evidence and language rules. These lenses are editorial interpretations; they are not a verified list authored by Duan. Preserve the user's goals rather than making caution the answer to every question.

## Sources

- [Six research notes](references/research/README.md) cover corpus boundaries, benfen, business quality, understanding, allocation, and modern-transfer limits.
- [Five source records](references/sources/README.md) contain one mirrored Q&A discussion, one podcast episode description, one secondary article, one truncated PDF compilation, and one archive index.
- [Extraction framework](references/extraction-framework.md) separates evidence, interpretation, and contemporary applications.

The archive has **no verified interview transcript or complete book capture**. A podcast chapter summary is not the guest's exact wording; readers' comments are not Duan's replies. Sources remain in their original language. Current holdings, prices, financial conditions, and company facts require current verification.

## Repository layout

```text
duan-yongping-skill/
├── README.md                  # English overview
├── README.zh-CN.md            # Simplified Chinese overview
├── SKILL.md                   # Routing and shared rules
├── LICENSE
├── requirements.txt           # Optional capture dependencies
├── references/                # Operational routes and extraction framework
│   ├── research/              # Editorial notes
│   └── sources/               # Captures with evidence boundaries
├── scripts/                   # Capture, conversion, and checks
└── tests/                     # Tool regression tests
```

## Maintenance

Using the skill does not require the maintenance tools. Run checks from the repository root with Python 3.10 or later:

```bash
python3 scripts/check_links.py .
python3 scripts/check_sources_inventory.py .
python3 scripts/check_research_repetition.py references/research
python3 -m unittest discover -s tests -v
```

The checks and core tests use the standard library. Optional HTML capture tests also run when `beautifulsoup4` is installed. Install capture dependencies only when using the web/PDF tool:

```bash
python3 -m pip install -r requirements.txt
```

- `scripts/capture_web_source.py` captures source material. Its required `--language` records the original language (`en`, `zh-CN`, another tag, or `und` if undetermined); it does not translate it.
- `scripts/download_subtitles.sh` requires optional `yt-dlp`. It defaults to English, trying manual then automatic subtitles in that language. `--language zh-CN` explicitly selects Simplified Chinese tracks. It does not fall back across languages or to Traditional Chinese, and ignores external yt-dlp configurations.
- `scripts/srt_to_transcript.py` converts an existing SRT or VTT file to readable text. Command-line messages remain English.

Replace `VIDEO_URL` with the target URL:

```bash
bash scripts/download_subtitles.sh "VIDEO_URL" outputs/subtitles
bash scripts/download_subtitles.sh --language zh-CN "VIDEO_URL" outputs/subtitles
```

Checks validate structure, metadata, duplication, and tool behavior. They do not establish historical truth, source rights, or answer quality. Keep both README versions synchronized and preserve source limitations when extending the library.

## Credits and license

Maintained by Jackson Huang and assembled with [Nuwa.skill](https://github.com/alchaincyf/nuwa-skill). Thanks to Nuwa's authors and contributors for the tooling.

Original project content is released under the [MIT License](LICENSE). Referenced and excerpted third-party materials retain their own rights and terms; inclusion here does not relicense them under MIT.
