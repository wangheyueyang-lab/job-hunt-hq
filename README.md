# 求职指挥部 job-hunt-hq

**一个 Claude 插件：装好后说一句“开始设置”，Claude 帮你搭好整套找实习的系统。**
每天帮你找岗位、写求职信、填申请表、给公司写邮件、准备面试。所有提交和发信都等你点头。

---

## 安装（两种方法，选一种）

### 方法一：在 Claude 里输入名字（推荐，不用下载）
1. 打开 Claude 电脑版，点左边的 **Customize**，再点 **Plugins**。
2. 点 **Add marketplace**，输入：
   ```
   wangheyueyang-lab/job-hunt-hq
   ```
3. 在出现的列表里找到 **job-hunt-hq**，点 **Install**。

### 方法二：下载文件再上传
1. 下载这个文件：**[job-hunt-hq.plugin](https://github.com/wangheyueyang-lab/job-hunt-hq/raw/main/job-hunt-hq.plugin)**（点开后会直接下载，不用注册）。
2. 打开 Claude 电脑版，**Customize → Plugins**，选择上传，选中刚下载的文件。

## 开始用
1. 在电脑上新建一个空文件夹，比如“文稿/Job Hunt HQ”。
2. 在 Claude 电脑版里新建一个项目，选择“使用已有文件夹”，选中它。
3. 在这个项目里说：**开始设置**。

Claude 会让你上传简历，然后一个一个问你问题，大约 20 分钟。之后每天给你一份清单，你回复编号就行，比如“submit 1, 3”“send 2”。

想填表和读邮件的话，还需要装 **Claude in Chrome** 扩展，并在那个 Chrome 里登录你的邮箱和招聘网站。

## 你始终说了算
- Claude 不输密码、不替你注册账号、不做验证码和在线测评。
- 邮件只发你点名同意的。
- 申请默认每份都先问你，你可以随时说“短的表直接交”。
- 写的所有经历和数字只来自你的简历和你确认过的内容。

## 更多说明
详细说明、文件夹里每个文件是做什么的、局限和注意事项，见 [插件说明](plugins/job-hunt-hq/README.md)。

---
作者：Yueyang · 许可：MIT
