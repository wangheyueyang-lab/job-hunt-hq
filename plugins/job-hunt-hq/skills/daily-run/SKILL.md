---
name: daily-run
description: >
  This skill should be used for the daily Job Hunt HQ pipeline, whether a scheduled task fires it or the
  user says "跑今天的清单", "今天的求职任务", "run today's batch", "daily run", or "what's new in my job hunt".
  It checks replies, finds and screens new roles, prepares and submits applications within the
  permission level, drafts cold emails, and writes one numbered batch for the user to approve.
metadata:
  version: "0.1.0"
---

# 每日运行

## 0. 开工
1. 读 `CLAUDE.md`、`criteria.md`、`voice.md`、`answers.md`、`facts_bank.md`、`tracker.csv`，以及 batch.md 最前面一段。
2. 读不到文件夹（电脑睡眠或断开）：不要开始任何申请，写一句说明后结束；有必须保存的内容先暂存，下次连上后补写进文件夹。
3. batch.md 显示另一个对话正在处理某些申请：那些不碰。
4. 用电脑的时钟记录时间，不凭感觉估计。

## 1. 查回复（先做）
在用户已登录的邮箱和各平台里查：新的回信、面试或测评邀请、拒信、退信、平台上的状态变化。打开邮件会标为已读，在清单里说明。面试或测评邀请：提醒用户，并说可以用 interview-prep 准备。

## 2. 找新岗位
运行 job-scout，按 criteria.md 的信息源顺序和“今天的重点”。数量不设死，以真正合适、仍然开放的为准。

## 3. 准备和提交
对每个通过的岗位：用 application-tailor 写材料，用 application-filler 填表，按放权档位决定提交还是留给用户。

## 4. 冷邮件
按 CLAUDE.md 的冷邮件规则，用 cold-outreach 起草当天的数量。只起草，不发送，除非用户在聊天里点名。

## 5. 写清单
按 batch.md 顶部的格式写当天清单，放在文件最前面，并存一份到 `Claude outputs/batch_<日期>.md`：
* 一句话结果
* 回信和状态变化
* 准备好的申请（编号、分数、JD 原句、简历版本、要勾的声明、特殊情况）
* 需要用户注册或登录的
* 冷邮件草稿（编号）
* 看过并排除的（每个一句原因）
* 需要用户回答的问题（编号，最多 5 个，最重要的在前）

## 6. 收尾
* tracker.csv 里每一个变化都已记录。
* 无人值守的定时运行中，点击提交被系统拦下属于正常情况：准备好材料，写明“等你在线时一句话就能交”。
* 最后在对话里留一段简短总结，用户回来时能一眼看到今天的结果和需要他做的事。
