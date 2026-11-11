# Old-School Researcher

[简体中文](README.md) | [English](README.en.md)

[![MIT License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/aidealee/old-school-researcher/pulls)

**快捷入口：** [Skill](old-school-researcher/SKILL.md) · [AGENTS.md](paper-project/AGENTS.md)

**让中英文学术写作更自然、直接、准确。** 当前版本：**1.1.2**。

Old-School Researcher 为 AI 写作助手提供一套完整的学术写作与修改指令。它帮助作者围绕研究贡献组织论述，清理机械套话和防御性措辞，同时保留原文观点、数据、公式、引用与复现信息。

项目提供 **Skill** 和 **AGENTS.md** 两种独立入口，适用于论文、学位论文、审稿回复、研究报告和基金申请。

## 能做什么

- **突出研究贡献**：把问题、方法、结果与意义讲清楚，用已有证据说明工作的优势。
- **改善中英文表达**：处理模板化开头、重复总结、空泛强调、连接词堆叠、中文长修饰和英文语法搭配。
- **采用直接的学术语气**：将散文中的限定、否定、让步及防御式表达改为具体对象、适用范围、证据类型和工作状态的正面陈述，保持原有含义与确定程度。
- **保护研究内容**：保留全部数字、正式命题、作者观点和复现信息，核对“对象—指标—数值—条件—引用”的对应关系；公式、正式命题与引语保持原文。
- **按任务控制修改幅度**：提供诊断、清理、润色、重构／压缩和起草五种模式，并结合作者或目标期刊的表达习惯处理文本。

## 选择 Skill 还是 AGENTS.md

| 你的使用场景 | 选择 | 使用入口 |
|---|---|---|
| 在不同论文和任务中按需调用 | **Skill** | 安装 [Skill 目录](old-school-researcher)，调用 `$old-school-researcher` |
| 让一个论文项目持续采用这套写作规范 | **AGENTS.md** | 将 [项目指令文件](paper-project/AGENTS.md) 放入论文项目，由客户端加载 |

两份文件包含相同的完整写作规则，各自独立生效。规范正文为中文，适用于中英文写作；任选一份完整加载即可使用全部规则。以下安装说明以 Codex 为例。

## 安装

先获取仓库：

```sh
git clone https://github.com/aidealee/old-school-researcher.git
cd old-school-researcher
```

安装入口位于仓库内：

```text
old-school-researcher/          # 仓库根目录
├── old-school-researcher/      # Skill 安装源目录
│   ├── SKILL.md                # 完整写作规则
│   └── agents/
│       └── openai.yaml         # 展示名称、默认提示语与调用策略
└── paper-project/
    └── AGENTS.md               # 可独立使用的项目指令
```

### 方式一：安装 Skill

1. 复制仓库内含 `SKILL.md` 的 **内层 `old-school-researcher/` 目录**，连同 `agents/` 子目录一起放入客户端的 Skill 目录。
2. Codex 的用户级安装位置为 `~/.agents/skills/old-school-researcher/`；项目级安装位置为 `<论文项目>/.agents/skills/old-school-researcher/`。已有自定义 Skill 目录的环境，沿用客户端正在扫描的目录。路径中的 `~` 表示用户主目录。目录规则见 [Codex Skills 文档](https://developers.openai.com/codex/skills)。
3. 在技能列表中选择 **Old-School Researcher**，或在 Codex 提示词中使用 `$old-school-researcher`。安装后可在新会话中检查技能列表。

安装后的入口应为 `<Skill 目录>/old-school-researcher/SKILL.md`。全部写作规则都包含在该文件中。

### 方式二：使用 AGENTS.md

1. 将仓库中的 `paper-project/AGENTS.md` 复制到论文项目根目录，文件名保持为 `AGENTS.md`。
2. 项目已有 `AGENTS.md` 时，将本文件的完整规则与现有项目规范整合。
3. 以该论文项目为工作目录开启新会话，让助手列出已加载的指令文件并概述写作规则，然后提交写作任务。

Codex 按目录作用域和指令优先级加载项目规范。项目包含多份指令时，检查覆盖关系及 `project_doc_max_bytes` 配置，确保完整规则进入上下文。具体设置见 [Codex AGENTS.md 文档](https://developers.openai.com/codex/guides/agents-md)。

### 在其他助手中使用

支持 Skill 或 AGENTS.md 的客户端，按其安装与指令加载方式放置对应文件。使用支持读取附件或粘贴长文本的聊天助手时，提供任意一份完整规则，并明确要求“完整读取这份文件，作为本次写作任务的指令执行”。

## 使用

### 用 Skill 润色英文论文

```text
使用 $old-school-researcher 润色下面的英文论文段落。
正文保持英文，修改说明用中文。
保留原文观点、全部数字、公式、引用与复现信息。

[粘贴论文段落]
```

### 用 AGENTS.md 清理中文定稿

在已加载项目指令的会话中提交：

```text
按本项目 AGENTS.md 清理下面的中文论文段落。
采用最小修改，保持段落和句序，无问题的句子逐字保留。
返回完整改稿和简短修改说明。

[粘贴论文段落]
```

### 选择修改模式

| 模式 | 适用任务 | 修改范围 |
|---|---|---|
| **诊断** | 检查问题、评估稿件 | 定位问题、说明原因并给出最小改法，保留原稿 |
| **清理** | 定稿整理、去套话、最小修改 | 只处理命中的词句，保持段落和句序 |
| **润色** | 一般草稿修改，默认模式 | 改善语法、搭配与衔接，保持标题层级和段落结构 |
| **重构／压缩** | 重写摘要、重组论证、压缩篇幅 | 按明确授权调整结构，保留实质观点、数据与引用 |
| **起草** | 根据研究材料写新内容 | 依据所给证据写作，以 `[[EVIDENCE: 所需证据]]` 标记材料缺口 |

提供原稿或研究材料，并说明修改模式、目标语言和期刊／作者风格。说明语言跟随你的提问，正文语言遵循指定语言或原稿语言。默认交付完整改稿与简短修改记录，也可指定“只返回正文”。

## 参与改进

欢迎通过 [Pull Request](https://github.com/aidealee/old-school-researcher/pulls) 改进表达、使用说明或写作规则。修改规则时同步更新 Skill 与 AGENTS.md，保持两份正文一致且各自完整；修改使用说明时同步维护中英文 README。

## 来源与许可

本项目在以下作品基础上重新组织和改写学术写作规则：

- [Academic-Humanizer](https://github.com/junbolian/Academic-Humanizer/tree/62b0a02627e063015466c70f0a4dd4929a9f7f5b)，作者 Junbo Lian；相关贡献来自 AIScientists-Dev（基于 blader 的 humanizer）和 shiujan。
- [anti-defensive-writing-Skill](https://github.com/Adkid-Zephyr/anti-defensive-writing-Skill/tree/82d31402caa0db1790026824399044538483171b)，作者 Adkid-Zephyr。

本项目采用 [MIT 许可证](LICENSE)，Copyright © 2026 aidealee。第三方作者归属、固定来源版本和完整许可见 [第三方通知](THIRD_PARTY_NOTICES.md) 与 [licenses/](licenses/)。Skill 和 AGENTS.md 各自保留第三方署名与完整许可文本，独立分发时一并保留。

复制或分发任一入口时，也保留根目录 [LICENSE](LICENSE) 中的本项目版权与许可声明，可随文件附带或合并到目标项目的第三方许可说明中。

开发协作规范见同系列项目 [Old-School Programmer](https://github.com/aidealee/old-school-programmer)。
