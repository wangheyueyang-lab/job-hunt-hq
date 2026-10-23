---
name: setup
description: >
  This skill should be used when the user wants to set up their internship or job hunt system for the
  first time, or says "开始设置", "帮我开始设置", "设置求职系统", "setup job hunt", "set up Job Hunt HQ",
  "start my job search", or installs the job-hunt-hq plugin and asks what to do next. It interviews the
  user, builds the whole Job Hunt HQ folder with filled-in rules, a facts bank from their CV and a
  tracker, schedules the daily run, and runs the first calibration round. Also use it when the user
  asks to redo or change the setup ("重新设置", "改一下我的设置").
metadata:
  version: "0.1.0"
---

# 开始设置

目标：用户只说一句“开始设置”，一次对话完成全部设置，不需要一条条下指令。整个过程大约 20 分钟，可以中途暂停，下次说“继续设置”从断点接着来。

## 原则
* 和用户说话用他们的语言（默认中文），口语、简短，不提文件路径和技术名词，除非用户问。
* **一次只问一个问题。** 有固定选项的用 AskUserQuestion；开放问题直接在聊天里问。能从简历里读出来的信息不要再问，直接请用户确认。
* 所有生成的规则文件里，用户亲口说的话尽量保留原话。
* 不收集用不到的个人信息。出生日期、证件号、家庭住址这类不主动问；证件号、银行卡号永远不写进任何文件。

## 第 0 步：检查环境
1. 确认这次对话能读写一个本地文件夹（Claude 桌面端的项目文件夹或已连接的文件夹）。如果不能，停下来告诉用户：
   * 在电脑上新建一个空文件夹，比如“文稿/Job Hunt HQ”；
   * 在 Claude 桌面端新建一个项目，选“使用已有文件夹”，选中它（或在当前对话里连接这个文件夹）；
   * 然后在这个项目里再说一次“开始设置”。
2. 检查有没有浏览器工具（Claude in Chrome 扩展或内置浏览器）。没有也能继续设置，但要告诉用户：填表、读招聘网站和 Gmail 需要装好 Chrome 扩展，并在那个 Chrome 里登录各个招聘平台和邮箱。
3. 检查文件夹里是否已经有 CLAUDE.md。有的话说明之前设置过：问用户是要从头重来、只改某几项，还是继续上次没完成的部分。从头重来前先把旧文件备份到 `Claude outputs/backup_<日期>/`。

## 第 1 步：开场
用三四句话告诉用户接下来会发生什么：先要简历，然后问十来个问题，接着自动建好整套文件、设好每天的定时任务，最后给出第一份 10 个岗位的候选名单让用户挑。强调两点：所有提交和发信默认都要用户点头；用户之后说的每一句“以后都……”都会被记住。

## 第 2 步：拿到简历
1. 请用户把简历（PDF 或 Word，可以多个版本，中英文都行）拖进对话或放进文件夹的 `cv/`。有成绩单也可以一起放。
2. 读每一份简历，记下各版本的侧重（比如咨询版、数据分析版、产品版、中文版）。
3. 把每个版本重命名成招聘方看了也体面的文件名（比如 `姓名_CV_Consulting.pdf`、`姓名_学校_专业_简历.pdf`），先问用户同不同意。

## 第 3 步：访谈
按 `references/interview.md` 的顺序问，一次一个。每个问题问完，把答案对应到模板里的占位符。用户说“跳过”或“你决定”时，用访谈文件里写的默认值，并告诉用户默认值是什么。

## 第 4 步：整理事实库
1. 用 `references/templates/facts_bank.md` 的结构，把简历里的每一条经历、数字、技能整理进去。不同版本说法强弱不一样时，取保守的那个，另一个标 [ASK]。
2. 给用户看一个简短的摘要（每段经历一两行），请他们确认有没有遗漏或写错。
3. 主动问 2 到 4 个能让经历更有说服力的数据问题（比如“这个项目最后有多少人用？”“社团活动一共多少人参加？”）。用户给的新数字写进去；用户不知道的就不写。

## 第 5 步：建文件夹
1. 建好 `cv/`、`jobs/`、`Claude outputs/`。
2. 用 `references/templates/` 里的模板生成 CLAUDE.md、criteria.md、facts_bank.md、answers.md、voice.md、tracker.csv、batch.md，替换所有 `{{占位符}}`。生成后搜一遍，确认没有残留的 `{{`。
3. 地区部分：
   * 新加坡：读 `references/regions/singapore.md`。
   * 中国内地：读 `references/regions/china-mainland.md`。
   * 其他国家或地区：按 `references/regions/other-regions.md` 的方法当场调研，结果写进 criteria.md 和 answers.md，并写明来源链接和查询日期。
   * 工作许可这类会变的规定，一律在设置时用网页搜索到官方来源核对一遍，不要只凭记忆写。
4. 在 CLAUDE.md 的“长期决定”里写下第一条：设置日期、当前放权档位、每日运行时间。

## 第 6 步：设定时任务
1. 用这次对话里可用的定时任务工具（scheduled task）新建一个每天运行的任务，时间用访谈里的答案，提示词写成一段独立完整的指令，例如：“打开 Job Hunt HQ 文件夹，读 CLAUDE.md，运行 daily-run 技能，按规则完成今天的清单。”
2. 如果没有定时任务工具，告诉用户可以每天自己说一句“跑今天的清单”，效果一样。
3. 提醒用户：定时任务运行时电脑、Claude 桌面端和 Chrome 要开着；电脑睡眠时它读不到文件夹。无人值守时点“提交”按钮可能会被安全检查拦下，这时任务会把材料准备好，等用户在线时再交。

## 第 7 步：第一轮校准
1. 运行 job-scout 技能，给出最多 10 个通过门槛的岗位，按分数排序，每个附 2 到 3 句决定性的 JD 原句。**停在这里。**
2. 请用户逐个说要不要、为什么。每个理由按 CLAUDE.md 规则 12 写进 criteria.md。
3. 用户选中的岗位，一次一个跑 application-tailor，给用户看动机段或求职信。用户的每处修改写进 voice.md（改前改后）。
4. 前 10 个岗位左右都这样走一遍，然后问用户要不要进入批次模式，以及要不要调高放权档位。

## 第 8 步：收尾
用几句话告诉用户以后每天怎么用：
* 每天打开当天的清单，回复编号就行，比如“submit 1, 2, 4”“send 1, 3”“skip 5，太偏销售”。
* 想改方向就直接说，比如“这周只看咨询”“以后不要再投银行”。
* 收到面试或测评邀请，说一句“帮我准备 XX 的面试”。
* 想放更多权或收回权限，直接说。

## 参考文件
* `references/interview.md`：访谈问题、顺序、默认值和占位符对应关系。
* `references/templates/`：所有规则文件的模板。
* `references/regions/`：各地区的平台、身份规定和经验。
