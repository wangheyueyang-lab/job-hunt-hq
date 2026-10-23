---
name: application-tailor
description: >
  This skill should be used when application materials need to be written, rewritten or checked for a
  role in the Job Hunt HQ pipeline, for example "写求职信", "帮我写动机", "改一下这段自我介绍", "这个表单问题怎么答",
  "write a cover letter", "draft my answers for this application", "make my intro sound more human",
  or "improve my CV". It uses only verified facts from facts_bank.md and follows voice.md.
metadata:
  version: "0.1.0"
---

# 写材料

## 输入
`facts_bank.md`（唯一的事实来源）、`voice.md`、`answers.md`、岗位的 `jobs/<文件夹>/jd.md`、`cv/` 里的简历。

## 步骤
1. **挑简历。** 从 `cv/` 里选最对口的现成版本，原样使用，记下文件名。用户明确要求为某个岗位改简历时才改，改动用改前改后给用户看。
2. **对照 JD。** 列出 JD 最重要的 4 到 5 项要求，每项对应事实库里的一条具体经历。写在 `jobs/<文件夹>/form_answers.md` 开头。
3. **写表单回答。** 动机栏、“为什么选我们”、“讲一次经历”等，逐题写进 form_answers.md，每题后面注明用了事实库的哪几条。自我介绍段的结构见 voice.md。
4. **写求职信。** 只要申请能放（上传栏、文本框、附加材料、邮件正文），就按 CLAUDE.md 的求职信规则写：
   * 围绕这家公司的一个具体的东西展开（业务、产品、客户群、正在进入的市场、JD 里的某项任务），说清楚为什么对它感兴趣。
   * 故事按 JD 的任务挑，不要每封都用同样两个经历；说清楚“这和你们的 X 很像，因为……”。
   * 一个小的具体瞬间（注意到了什么、学会了什么）胜过总结，但必须在事实库范围内。
   * 写明可实习时间。岗位时间和用户时间对不上时，如实写出用户能做什么。
   * 3 到 4 段，300 词以内，结尾按 voice.md 的礼貌规则。
   * 保存 `cover_letter.md`，并生成 A4 的 `cover_letter.pdf`（名字、联系方式、日期、收件方、正文、署名）。上传时另存一份 `<英文名>_Cover_Letter_<公司>.pdf`，因为招聘方看得到文件名。
5. **自查。** 每个数字和说法都能在事实库里找到；没有一句可以原封不动搬去另一家公司的空话；和最近写给别家的信对比一下，开头和故事不要重复；语言按目标地区（中文规范见 `references/writing-zh.md`，英文见 `references/writing-en.md`）。
6. **超出事实库的说法**（新数字、新结果、更强的动词）：列成改前改后给用户看，批准后写进事实库的“已确认的升级”，没批准就不用。

## 学习
用户改了你写的东西：照改，不要再把删掉的内容加回来，并把规则写进 voice.md（日期、规则、改前改后）。
