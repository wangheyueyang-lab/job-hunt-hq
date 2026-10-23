---
name: cold-outreach
description: >
  This skill should be used when the user wants to email companies that have no open posting, or to
  write or send cold emails in the Job Hunt HQ pipeline, for example "写冷邮件", "帮我联系几家公司", "send 1, 3",
  "draft cold emails", "reach out to boutique consulting firms", or "find who to email at this firm".
  It picks firms, finds a named recipient and a published address, writes a researched opening, and
  sends only emails the user approves by number.
metadata:
  version: "0.1.0"
---

# 冷邮件

经验：写给中小型公司有名有姓的人、开头有真实细节的冷邮件，回复率明显高于门户网站申请。

## 选公司
1. 按 CLAUDE.md 的冷邮件规则确定今天写几封、写给哪些地区。
2. 优先中小型公司（精品咨询、研究机构、行业智库、初创公司），方向对口 criteria.md 的前几个 Tier。
3. 查 tracker.csv，联系过、投过或排除过的公司跳过。
4. 每家写一句为什么适合用户。

## 找收件人和地址
1. 找一个具体的人：创始人、合伙人、地区负责人、招聘负责人。
2. **只用公司公开的地址**：官网、团队页、招聘页、官方新闻稿、本人公开资料上写着的邮箱。没有个人邮箱就用公司公开的 careers@ / hr@ / info@，信里写明请转给哪位。
3. 只有当同一个域名下公开过同样格式的其他地址时，才能按这个格式推测，并在草稿里标明“推测”。凭空猜的地址常被退信（550 收件人不存在）。
4. 只有网页表单的：写好表单文字交给用户，用户同意后可以代填。

## 写开头
1. 找对方最近的一个真实内容：一篇文章、一份报告、新办公室、一个项目。打开原文核实，记下链接和日期。
2. 写一两句：读到了什么、让你想到了什么。像一个学生在说话，不罗列公司成就，一个细节就够。
3. 然后按 voice.md 和写作规范（`../application-tailor/references/writing-zh.md`、`writing-en.md`）写正文：自我介绍、一两个和对方业务最接近的经历、可实习时间、请求。研究型小公司可以加一句“也可以按项目合作”。

## 保存
每封存为 `jobs/<公司>_cold-outreach/email.md`，正文前写一段给用户看的说明：
* 收件人、职位、邮箱，以及邮箱是公开的还是推测的（附出处）
* 附哪一份简历
* 主题
* 开头细节的来源链接和日期
* 用了事实库的哪几条
tracker.csv 写一行，状态 `outreach_drafted`。

## 发送
1. 在清单里编号列出（公司、收件人、开头用的细节、一句理由）。用户回复“send 1, 3”才发，只发点到的。
2. 从用户已登录的邮箱发送。发之前读一遍收件人、主题、正文长度、附件名，确认无误。
3. tracker 改为 `outreach_sent`，写发送时间。
4. 第二天查有没有退信，退回的标 `outreach_bounced`，不重复尝试同一个地址。
5. 默认不追发跟进信；没回复就把精力放在新公司上。用户要求跟进时，在原邮件线程里回复，简短、礼貌。

## 回复
有回复时读出要点写进清单和 tracker（replied_positive / replied_no_opening / replied_holding），需要回信的先起草，等用户批准再发。
