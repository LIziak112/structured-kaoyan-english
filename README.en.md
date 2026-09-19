<p align="center">
  <img src="banner.jpg" alt="Structured Kaoyan English banner" width="100%">
</p>

# Structured Kaoyan English

[简体中文](readme.md) | **English**

![License](https://img.shields.io/badge/license-Layered%20%7C%20Questions%3A%20Free%20%7C%20Explanations%3A%20CC%20BY--NC%204.0-blue)

A machine-readable dataset of **China's National Postgraduate Entrance Examination English papers (1998–2025)**, covering both **English I** and **English II** — every paper digitized from scanned PDFs and messy Word documents into **structured JSON question banks** and **clean Markdown documents with detailed explanations**.

Built for exam preparation, AI-assisted learning, LLM fine-tuning, and RAG knowledge bases.

## 🌟 Why This Project

Most Kaoyan English materials circulating online are either poorly formatted Word files or non-searchable scanned PDFs, which makes them hostile to modern workflows:

- Hard to feed into an LLM for mistake analysis or long-sentence breakdowns;
- Hard to index into a personal retrieval knowledge base or an automated review pipeline.

So I used **300 million tokens of GLM-5.3-Flash** credits together with automation scripts to clean and restructure 28 exam years into this dataset. The goal: let every student and developer use authentic past-paper data with zero cleaning effort, and build their own AI-powered learning and review systems on top of it.

## 📦 What's Inside

**44 complete papers** organized by year. From 2010 onward, the exam splits into English I and English II, so directories carry a `-1` / `-2` suffix:

```
1998/           1998.json  1998.md  assets/
1999/           ...
2010-1/         2010-1.json  2010-1.md  assets/      # English I
2010-2/         2010-2.json  2010-2.md  assets/      # English II
...
2025-1/  2025-2/
```

Two complementary formats per paper:

- **JSON question banks** — passages, question numbers, options, and standard answers as strictly typed fields, designed for programmatic access, benchmarking, and quiz systems. Blanks in cloze passages are marked with `{{n}}` placeholders:

  ```json
  {
    "year": 2024,
    "exam": "英语一",
    "sections": [
      {
        "title": "Section I Use of English",
        "instructions": "Directions: Read the following text...",
        "score": 10,
        "groups": [
          {
            "type": "cloze",
            "passage": [
              "There's nothing more welcoming than a door opening for you. {{1}} the need to be touched to open or close, automatic doors are essential in {{2}} disabled access to buildings..."
            ],
            "questions": [
              {
                "number": 1,
                "options": { "A": "Through", "B": "Despite", "C": "Besides", "D": "Without" },
                "answer": "D",
                "explanation": "…detailed analysis in Chinese…"
              }
            ]
          }
        ]
      }
    ]
  }
  ```

- **Markdown explanations** — full translations, key-point analysis, long-sentence breakdowns, and solution reasoning, wrapped in collapsible `<details>` blocks; pleasant for humans to read and easy to chunk as RAG corpus.

- **Assets** — figures from cloze/reading/new-question-type sections, uniformly renamed to avoid numbering collisions, with relative paths inside the documents verified.

## 🚀 Quick Start

```python
import json, glob

papers = [json.load(open(p, encoding="utf-8")) for p in glob.glob("*/*.json")]
print(len(papers))  # 44

# License-aware usage: drop the `explanation` field to keep only
# the freely-licensed question data (see License section below)
def strip_explanations(paper):
    for section in paper["sections"]:
        for group in section["groups"]:
            for q in group["questions"]:
                q.pop("explanation", None)
    return paper
```

## ⚠️ Data Sources & Known Limitations

1. **Sources**: question texts were collected from publicly shared past-paper archives and prep communities; explanations were compiled from widely circulated digital study-guide scans.
2. **Accuracy**: the pipeline combined OCR, scripts, and an LLM, so typos, omissions, and occasional hallucinations are unavoidable — **100% fidelity is not guaranteed**.
3. **Contributions welcome**: if you spot a typo, a missing question, or a flawed explanation, please open an **Issue** or submit a **Pull Request**!

## ⚖️ License

This is a **mixed-content dataset**: questions and explanations carry different rights, so no single standard open-source license fits. The repository uses a **layered license** — full terms in [LICENSE.md](LICENSE.md):

| Layer | Scope | Terms |
| --- | --- | --- |
| **Question data** | All JSON fields except `explanation`; the question body of the Markdown files; exam figures in `assets/` | 🟢 **Free for any use**, commercial or non-commercial |
| **Explanation data** | The `explanation` field in JSON; the `<details>` blocks in Markdown | 🔴 **CC BY-NC 4.0 — non-commercial use only**; copyright belongs to the original authors/publishers |
| **Original contributions** | Schema design, field specifications, documentation | CC BY 4.0 |

- **Why explanations can't be commercialized**: they are compiled from third-party study guides whose copyright stays with the original authors/publishers; this project holds no commercial license and therefore **cannot grant any commercial rights** over them.
- **Fallback rule**: if you cannot reliably separate questions from explanations, treat the files as a whole under the non-commercial term.
- **Takedown**: rights holders who believe their content is included improperly can open a GitHub Issue with proof; disputed content will be removed promptly after verification.

## 💖 Support the Project

If this dataset helped your exam preparation or saved you hours of data cleaning for your AI experiments, please give the repo a **Star ⭐️** — that means a lot! Good luck to everyone taking the exam!

---

*This project is not affiliated with the Ministry of Education Examinations Authority (NEEA) or any publisher. Contents are provided "as is" and do not constitute official materials.*
