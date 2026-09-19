# 许可证（Layered License）

**Structured-Kaoyan-English（考研英语结构化数据集）**

本仓库是混合内容数据集：**试题数据可自由使用；解析数据涉及第三方著作权，仅限非商业用途**。任何单一的标准开源许可证都无法同时表达这两种授权，因此本项目采用**分层授权**——请先判断你所使用的内容属于哪一层，再遵守对应条款。

**使用本仓库中的任何内容，即表示你已阅读、理解并同意本文件的全部条款。**

---

## 第一层｜试题数据（自由使用）

### 范围

- 各 `*.json` 文件中除解析字段以外的全部题目结构字段：`year`、`exam`、`sections[].title / instructions / score`、`groups[].type / passage`、`questions[].number / options / answer`；
- 各 `*.md` 文件中的试题正文（Directions、阅读篇章、题干、选项与标准答案行）；
- `assets/` 目录中的试题配图。

### 条款

本项目对试题数据**不主张任何权利、不附加任何使用限制**。任何人可为任何目的（包括商业与非商业目的）自由使用、复制、修改、再分发，无需事先征得同意。

---

## 第二层｜解析数据（仅限非商业使用）

解析内容整理自网络流传的第三方数字化教辅资料，其著作权归**原作者 / 相关出版方**所有。本项目未获得著作权转让或商业性许可，仅以个人学习、学术交流为目的整理收录，因此**无权也不会授予任何商业性使用许可**。

### 范围

凡属以下内容，均视为解析数据：

- 各 `*.json` 文件中的 `questions[].explanation` 字段；
- 各 `*.md` 文件中 `<details><summary>解析</summary>…</details>` 折叠块内的全部内容；
- 其他明确以"解析 / 答案精析 / 考点精析 / 长难句剖析 / 解题思路 / 全文翻译"为性质的字段、段落或配文。

### 条款（以 [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.zh) 为基础）

- ✅ **允许**：在署名来源的前提下，为**个人学习、学术交流、科学研究**等非商业目的使用、引用、分享与再加工；
- ❌ **禁止**：将解析数据用于**任何直接或间接的商业目的**，包括但不限于付费售卖、付费课程 / 会员内容、商业培训、植入商业 App / 网站 / 小程序，以及以盈利为目的的题库或 AI 服务；
- **署名要求**：再分发或再加工解析数据时，须保留"整理自网络公开教辅资料，著作权归原作者 / 出版方所有"的说明。

---

## 第三层｜项目原创贡献

### 范围

本项目的数据结构设计与字段规范、清洗与转换方案、README 及其他文档等原创性内容（不含试题与解析内容本身）。

### 条款

采用 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.zh)：署名即可自由使用（含商业用途）。若仓库未来加入代码或脚本，代码部分将采用 MIT 许可证。

---

## 重要边界说明：如何区分试题与解析

试题数据与解析数据在同一文件内**混存**，请按下表区分：

| 文件类型 | 试题数据（第一层） | 解析数据（第二层） |
| --- | --- | --- |
| JSON | `explanation` 之外的全部题目字段 | `questions[].explanation` 字段 |
| Markdown | 正文、Directions、题干、选项、`> **答案**` 行 | `<details>` 折叠块内的全部解析内容 |

> ⚠️ **兜底规则**：若你无法可靠地将试题与解析分离，请将所使用的文件**整体按第二层（非商业）条款**执行。

---

## 侵权处理（Takedown）

本项目秉持开源交流与学习分享的初衷，无意侵犯任何第三方合法权益。若你（或你所代表的机构）是相关内容的著作权人，认为本仓库收录的试题或解析内容侵犯了你的权益，请通过 [GitHub Issue](../../issues) 提交权利声明（附权利证明与具体文件路径）。经确认后，我们将在第一时间下线 / 删除争议内容。

---

## 免责声明（无担保）

1. **无担保**：本仓库内容按"现状"提供，不附任何形式的明示或默示担保。数据经扫描件识别与大模型辅助转换获得，可能存在错漏，不保证其准确性、完整性或适销性，使用后果由使用者自行承担。
2. **非官方**：本项目与教育部教育考试院及任何命题机构、出版方均无关联，仓库内容不构成官方资料，亦不代表任何机构立场。
3. **试题权利提示**：本项目不对试题数据主张权利，并不代表试题必然处于公有领域；试题的著作权状况以相关法律法规及权利方的正式主张为准。如拟作商业性使用，建议使用者自行评估风险。
4. **使用者责任**：使用者应自行确保其使用方式符合本许可证条款及所在司法辖区的法律法规。因不当使用引发的任何纠纷，与本项目管理人无关。

---

## License Summary (English)

This repository is a mixed-content dataset licensed under a **layered scheme** (the Chinese text above is authoritative):

1. **Exam question data** — question stems, passages, options, standard answers, and exam figures; i.e. all JSON fields except `explanation`, and the question body of the Markdown files. *Free for any use, commercial or non-commercial. This project claims no rights over it and imposes no restrictions.*
2. **Explanation / analysis data** — the `explanation` field in the JSON files and the `<details>` blocks in the Markdown files. *Copyright belongs to the original authors/publishers. Licensed under* [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en)*: **non-commercial use only**, attribution required. If you cannot separate questions from explanations, treat the files as a whole under this non-commercial term.*
3. **Original contributions of this project** — schema design, field specifications, and documentation. Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.en).

**Takedown**: if you are a rights holder and believe any content in this repository infringes your rights, please open a GitHub Issue with supporting proof; the disputed content will be removed promptly after verification.
