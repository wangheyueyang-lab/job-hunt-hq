---
name: interview-prep
description: >
  This skill should be used when an interview, assessment, case interview or recruiter call comes in for a
  role in the Job Hunt HQ pipeline, or when the user asks to prepare or debrief, for example "帮我准备面试",
  "收到笔试邀请", "case 怎么准备", "这个 HR 电话聊什么", "prepare me for the interview", "how do I prepare for
  this case", or pastes interview notes afterwards.
metadata:
  version: "0.1.0"
---

# 面试准备

## 收到邀请时
1. tracker.csv 状态改为 `interview` 或 `assessment`，写日期、轮次、形式、联系人。
2. 读 `jobs/<文件夹>/jd.md`，以及用户提交给这个岗位的简历、表单回答和求职信。他们说过的话要能接上。
3. 需要回复邀请或给出可用时间的：起草回信，等用户确认后再发。

## 准备材料（`jobs/<文件夹>/interview_prep.md`）
1. **公司**：做什么、这个团队或业务线、和这个团队相关的近期新闻、主要竞争对手。注明来源。
2. **面试官**（如果知道名字）：只看公开的职业信息（职位、负责领域、公开文章或演讲），用来推测对方关心什么。不涉及任何私人信息。
3. **可能的问题**：动机、行为面试题；咨询类岗位加一道和公司业务相关的 case 或市场规模估算题，附解题框架。
4. **用户的故事**：5 到 6 个 STAR 故事，只用事实库里的内容，每个标明能回答哪类问题。
5. **薄弱点**：比如年级偏低、实习时间短、为什么选这个方向、签证和工时，每个给一个诚实的回答角度。
6. **反问**：4 到 5 个针对这个团队的问题。

## 不熟悉的形式
用户没见过的形式（比如笔试 case、群面、录像面试）：先查公开资料。找不到这个公司的具体经验时，按同类公司的通常做法准备，并明确告诉用户这是推测。可以出一道限时模拟题，另附答案和评分要点，请用户先做再看答案。

## 测评
在线测评由用户本人完成。可以准备测评类型说明、答题思路和练习建议。

## 面试后
用户发来笔记时，写 `jobs/<文件夹>/debrief.md`：问了什么、怎么答的、哪里好、哪里要改、对岗位的新了解。反复出现的、关于怎么介绍自己的经验，写进 voice.md 的“从修改里学到的”。
