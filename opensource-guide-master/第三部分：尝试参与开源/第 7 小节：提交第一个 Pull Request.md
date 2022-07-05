# 第 7 小节：提交第一个 Pull Request

```
merge pull request的流程相对简单，是通过两个自己项目的repo进行的阐述，需要补充权限说明，code review，approve，CI机制等  
```

## 什么是 Pull Request

Pull Request 也叫做 PR（下文统称为 PR），其本质上是一种协同工作的机制，它可以进行基于网络的多人提交，帮助大家参与到项目中，通过审核机制对内容进行审核，最终合并到主分支中。与此同时，PR 也是一种通知机制，可以将你的修改通知仓库的管理者，管理者接到通知后，会对你的修改审查并决定是否合并本次修改。

主流的代码托管平台均提供 PR 功能，例如：GitHub、Gitee 等。

## Pull Request 的权限

**按平台角色划分**

| 操作    | 访客 | 报告者 | 观察者 | 开发者 | 管理员 | 项目组管理员 |
| ------- | ---- | ------ | ------ | ------ | ------ | ------------ |
| 查看 PR | ✅    | ✅      | ✅      | ✅      | ✅      | ✅            |
| 评论 PR | ✅    | ✅      | ✅      | ✅      | ✅      | ✅            |
| 创建 PR | ✅    | ✅      | ✅      | ✅      | ✅      | ✅            |
| 审核 PR | ❌    | ❌      | ❌      | ❌      | ✅      | ✅            |
| 合并 PR | ❌    | ❌      | ❌      | ❌      | ✅      | ✅            |

**按项目角色划分**

| 操作    | User | Contributor | Committer | Maintainer |
| ------- | ---- | ----------- | --------- | ---------- |
| 查看 PR | ✅    | ✅           | ✅         | ✅          |
| 评论 PR | ✅    | ✅           | ✅         | ✅          |
| 创建 PR | ✅    | ✅           | ✅         | ✅          |
| 审核 PR | ❌    | ❌           | ✅         | ✅          |
| 合并 PR | ❌    | ❌           | ✅         | ✅          |

## Pull Request 的步骤

在了解了 PR

第一步，你需要 Fork 别人的仓库。也就是将别人的仓库复制到你自己的仓库中。

第二步，在你自己的仓库上，修改然后提交之后，在网页端点击「New pull request」按钮。

在接下来的网页上有 base 仓库和 head 仓库，其中 base 是你想要提交的仓库，head 分支是你已经提交变更的仓库。

第三步，在提交中，描述提交本地提交的说明。

### 操作示例

**Gitee 平台**

1. 在 Gitee 上建立两个帐号 A 和 B。
![账号A](https://images.gitee.com/uploads/images/2021/0410/150351_aaf54390_8456984.png "账号A.png")
![账号B](https://images.gitee.com/uploads/images/2021/0410/150408_a80b686f_8456984.png "账号B.png")

2. 使用 A 帐号，新建仓库 pull_request_demo
![新建仓库1](https://images.gitee.com/uploads/images/2021/0410/150429_3f7cb023_8456984.png "新建仓库1.png")
![新建仓库2](https://images.gitee.com/uploads/images/2021/0410/150447_58b43a00_8456984.png "新建仓库2.png")
![新建仓库3](https://images.gitee.com/uploads/images/2021/0410/150501_421219a8_8456984.png "新建仓库3.png")

3. 在本地提交 README.md

   ```
   echo "pull_request_demo from A" >> README.md
   git init
   git add README.md
   git commit -m "first commit"
   git branch -M main
   git remote add origin https://gitee.com/A/pull_request_demo.git
   git push -u origin master
   ```

![本地提交](https://images.gitee.com/uploads/images/2021/0410/150531_69fb8ed9_8456984.gif "在本地提交 README.md.gif")

4. 使用 B 帐号登录 Gitee，然后 Fork 该项目。
![Fork项目1](https://images.gitee.com/uploads/images/2021/0410/150546_b6c50179_8456984.png "B账号fork项目1.png")
![Fork项目2](https://images.gitee.com/uploads/images/2021/0410/150559_4e6f6afc_8456984.png "B账号fork项目2.png")
![Fork项目3](https://images.gitee.com/uploads/images/2021/0410/150610_4351a9ea_8456984.png "B账号fork项目3.png")

5. 下载项目到本地

   ```
   git clone https://gitee.com/B/pull_request_demo
   echo "pull_request_demo add form B" >> README.md
   git add README.md
   git commit -m "modify commit"
   git push
   ```

![下载到本地](https://images.gitee.com/uploads/images/2021/0410/150637_0c8c1499_8456984.gif "下载项目到本地.gif")

6. 使用 B 帐号登录 Gitee，进入 pull_request_demo 仓库，点击 「+ Pull request」链接。
![Pull-1](https://images.gitee.com/uploads/images/2021/0410/150654_687717a7_8456984.png "pull_requests1.png")
![Pull-2](https://images.gitee.com/uploads/images/2021/0410/150708_fe12dee3_8456984.png "pull_requests2.png")

7. 选择 源分支 和 目标分支。
![源分支](https://images.gitee.com/uploads/images/2021/0410/150915_d55c2b70_8456984.png "源分支.png")
![目标分支](https://images.gitee.com/uploads/images/2021/0410/150928_84fd4489_8456984.png "目标分支.png")

8. 填写提交说明后，点击「创建」按钮。
![填写说明](https://images.gitee.com/uploads/images/2021/0410/150946_953a2d7e_8456984.png "pull_requests3.png")
![点击创建](https://images.gitee.com/uploads/images/2021/0410/155106_78a14137_8456984.png "点击创建.png")

9. 使用 A 帐号登录 Gitee，进入 pull_request_demo 项目。
![进入项目](https://images.gitee.com/uploads/images/2021/0410/160712_621d0351_8456984.png "进入项目.png")

10. 可以看到 Pull request 中有新的数据。
![有数据](https://images.gitee.com/uploads/images/2021/0410/160726_a311f8f8_8456984.png "有新数据.png")

11. 点击「合并」按钮，即可完成。
![合并](https://images.gitee.com/uploads/images/2021/0410/160740_eff52230_8456984.gif "合并.gif")

**GitHub 平台**

1. 在 GitHub 上建立两个帐号 A 和 B。
![账号A](https://images.gitee.com/uploads/images/2021/0412/210726_a1f2fb20_8456984.png "账号A.png")
![账号B](https://images.gitee.com/uploads/images/2021/0412/210742_4cf5244b_8456984.png "账号B.png")

2. 使用 A 帐号，创建项目 pull_request_demo
![新建仓库](https://images.gitee.com/uploads/images/2021/0412/210813_1923ef71_8456984.gif "新建仓库.gif")

3. 在本地提交 README.md

   ```
   echo "pull_request_demo from A" >> README.md
   git init
   git add README.md
   git commit -m "first commit"
   git branch -M main
   git remote add origin https://github.com/A/pull_request_demo.git
   git push -u origin main
   ```
![本地提交](https://images.gitee.com/uploads/images/2021/0412/210834_1996cb81_8456984.gif "本地提交 README.md.gif")

4. 使用 B 帐号登录 GitHub，然后 Fork 该项目。
![Fork项目1](https://images.gitee.com/uploads/images/2021/0412/210900_ec78c0a3_8456984.png "B账号Fork项目1.png")
![Fork项目2](https://images.gitee.com/uploads/images/2021/0412/210912_81ab2e4b_8456984.png "B账号Fork项目2.png")

5. 下载项目到本地

   ```
   git clone https://github.com/B/pull_request_demo
   echo "pull_request_demo add form B" >> README.md
   git add README.md
   git commit -m "modify commit"
   git push
   ```
![下载项目到本地](https://images.gitee.com/uploads/images/2021/0412/211003_c2c14ec9_8456984.gif "下载项目到本地.gif")

6. 使用 B 帐号登录 GitHub，进入 pull_request_demo 仓库，点击 Pull request 链接。
![Pull项目1](https://images.gitee.com/uploads/images/2021/0412/211325_db7cf976_8456984.png "pull_request1.png")
![Pull项目2](https://images.gitee.com/uploads/images/2021/0412/211338_5f0754d0_8456984.png "pull_request2.png")

7. 选择 base 和 head 仓库。点击「Create pull request」按钮。
![选择Base仓库](https://images.gitee.com/uploads/images/2021/0412/211356_5be9f12f_8456984.png "base仓库.png")
![选择Head仓库](https://images.gitee.com/uploads/images/2021/0412/211415_eb747ed6_8456984.png "head仓库.png")
![点击Create pull request按钮](https://images.gitee.com/uploads/images/2021/0412/211618_853d205c_8456984.png "点击Create pull request按钮")

8. 填写提交说明后，点击「Create pull request」按钮。
![填写说明](https://images.gitee.com/uploads/images/2021/0412/211746_ebc51069_8456984.png "填写说明.png")
![提交](https://images.gitee.com/uploads/images/2021/0412/211802_7f52d86e_8456984.png "提交.png")

9. 使用 A 帐号登录 GitHub，进入 pull_request_demo 项目。
![进入项目1](https://images.gitee.com/uploads/images/2021/0412/211815_7a8e3dab_8456984.png "A账号进入项目1.png")
![进入项目2](https://images.gitee.com/uploads/images/2021/0412/211832_21255b22_8456984.png "A账号进入项目2.png")

10. 可以看到 Pull request 中有新的数据。
![有数据](https://images.gitee.com/uploads/images/2021/0412/211849_884cb0ca_8456984.png "有新数据.png")

11. 点击 Confirm merge，完成合并。
![合并](https://images.gitee.com/uploads/images/2021/0412/213111_8df051bf_8456984.gif "合并.gif")

### 补充：参与公共的 PR 仓库来完成第一次PR尝试

当然，如果你不想注册两个账户亦或由于某些原因对此感到比较麻烦的话，你也可以按照上面的说明来选择参与到一些公共且活跃维护的 仓库。

> **注意：PR 提交测试请在自己个人仓库或公共维护的 PR 测试仓库尝试，切勿提交无用的 PR 到公共的正式仓库！！！**

你可以尝试提交一次 PR 到「[开源指北仓库 - 开源示例 - 提交 Pull Reqeust 示例.md](../开源示例/提交 Pull Request 示例.md)」文件中。

此外，还可以提交到 GitHub 的 [first-pr 测试仓库](https://github.com/ituring/first-pr) （第一次提交时你只能作为提交者进行尝试）。在这个仓库中，当你的 PR 被通过合并后，你的账户通常也会得到管理员权限，在此时你也可以来尝试作为管理员的身份来合并其他人的提交。

是的，在此时你的心中可能已经有了一个猜想，而我们在这里也可以告诉你这个猜想没有问题，像这些仓库其实还有很多，而且通常是由全体自发的贡献者来自愿进行维护的，而你也可以成为其中的一员。

## Pull Request 的审核规则

审核 PR 也被称作 Code Review，审核 PR 是整个流程中极其重要的一步。我们通过人工审核来区分 PR 的有效性，当越来越多的人参与到项目中，为了保证项目能够高效有序的处理 PR，需要制定一套标准的审核流程。当然，我们想到的问题，代码托管平台已经帮我们想到了，下面就让我们看一下它们是怎么做到的吧！

### 审核原则

GitHub 提供了一份审核原则，帮助大家更加友好高效地进行 PR 审核的审核原则。下面列举其中部分原则：

> ### 针对所有人的审查
>
> - 接受这样的事实：很多编程上的主张都是一种个人观点。应该讨论它们的利与弊，提出你的倾向观点，迅速的达成一种解决方案。
> - 提问，而不是命令。(“把这个变量命名成`:user_id`你觉得怎样？”)
>
> ### 让别人审查你的代码
>
> - 对审查者的建议表示感激。(“谢谢提醒。我会把它改正。”)
> - push提交要基于最早的一轮反馈，并形成一个独立的分支。等这个分支上的任务完全完成了再合并。这让审查者能够根据早先的反馈找到你的单独的更新。
>
> ### 代码审查的过程
>
> 先要清楚你提交的代码的必要性(是修补bug，提升用户体验，重构…)。然后：
>
> - 针对你感觉非常好的地方以及不是很好的地方与作者交流。
> - 如果讨论变得过于哲学或理论，把讨论转到线下，做成一个有规律的每周五下午的讨论会。同时，是否采用你提出的实现方案，让作者自己做决定。
>
> ### 关于程序风格样式的评论注释
>
> 审查者应该对那些不符合[样式](https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2Fthoughtbot%2Fguides%2Fblob%2Fmaster%2Fstyle)指导的地方进行注释。例如这样注释：
>
> ```
> [Style](../style):
> 
> > 按名称的字母顺序排列多个路由。
> ```
>
> 对上面这个提醒的一个回复的例子：
>
> ```
> 哦。你眼真尖，谢谢。已在 a4994ec 修复。
> ```
>
> 如果你不同意某个指导原则，请在指导repo里创建一个问题，而不要再代码审查中争论它。同时，请运用这个指导原则。

更多审核原则请参考 [Github 官方给出的代码审查指导原则](https://www.oschina.net/news/38067/github-code-review)（[英文原文： [code review](https://github.com/thoughtbot/guides/tree/main/code-review#code-review) ]）。

### 审核规则配置

> 以 Gitee 平台为例

步骤说明：

1. 打开想要配置审核规则的仓库，点击「管理」页面；
2. 在「管理」页面左侧功能栏，点击「代码审查设置」按钮；
3. 在右侧页面中，「指定审查人员」、「指定测试人员」，并选择通过规则；
4. 点击「保存」按钮，保存审核规则。

具体步骤如下图所示。

![输入图片说明](https://images.gitee.com/uploads/images/2021/0701/153036_247bbc53_1899066.png "屏幕截图.png")

## Pull Request 持续集成与部署

在学习了以上这些 PR 相关的基本操作以后，下面介绍一下 PR 后的高级操作：

- 持续集成（Continuous Integration）：持续集成是指提交代码到仓库后，进行代码编译、测试、输出结果等一系列自动化流程，帮助我们控制开发流程、快速定位错误，有效提高项目的集成效率。

- 持续交付（Continuous Delivery）：持续交付是指在持续集成的基础上，将持续集成的成果物进行产品化，最终形成可交付产品的自动化流程，能够缩短软件产出到交付所需要的时间，提高产品交付可靠性。

- 持续部署（Continuous Deployment）：持续部署是指将产品部署到指定环境的自动化流程，可以提高产品发布速度、部署流程的可靠性。

由于持续交付、持续部署的英文缩写相同，因此这三种操作也被简称为 ：「CI/CD」。

**GitHub Actions**

GitHub 提供了 GitHub Actions 功能，通过构建 workflow、job、step、action 实现了 CI/CD 的操作。

[官方文档](https://docs.github.com/cn/actions)中描述如下：

> 在 GitHub Actions 的仓库中自动化、自定义和执行软件开发工作流程。 您可以发现、创建和共享操作以执行您喜欢的任何作业（包括 CI/CD），并将操作合并到完全自定义的工作流程中。

- workflow （工作流程）：持续集成一次运行的过程，就是一个 workflow。

- job （任务）：一个 workflow 由一个或多个 jobs 构成，含义是一次持续集成的运行，可以完成多个任务。

- step（步骤）：每个 job 由多个 step 构成，一步步完成。

- action （动作）：每个 step 可以依次执行一个或多个命令（action）。

如下图所示，在仓库下点击 Actions 页面，可以通过“set up a workflow yourself”创建一个自定义流程，也可以从下方选择对应的 Action 成品。

![输入图片说明](https://images.gitee.com/uploads/images/2021/0701/153011_d625f1ff_1899066.png "屏幕截图.png")

此外，GitHub 还提供了 [Actions 集市（Actions Marketplace）](https://github.com/marketplace?type=actions)，集市中囊括了所有 Action。你可以从集市中挑选你需要的 Action 成品，也可以将自己构建好的 Action 通过集市分享出来。

**Gitee DevOps**

Gitee 提供了 Gitee DevOps 功能，通过集成第三方服务来实现 CI/CD 的操作。

如下图所示，Gitee 平台目前支持：Gitee Go、百度效率云、腾讯云托管、腾讯云 Serverless、Jenkins for Gitee 等集成方式。

![输入图片说明](https://images.gitee.com/uploads/images/2021/0701/153021_0701f7f6_1899066.png "屏幕截图.png")

## 本部分内容贡献者

[brace](https://gitee.com/awang)、[李志鹏](https://gitee.com/lizhipeng1992)、[ORH](https://gitee.com/orh)、[ShardingSphere](https://gitee.com/dangdangdotcom_zhangliang)、[冰彦糖](https://gitee.com/bingyantang)、[西狩](https://gitee.com/lihuimingxs)  

> 发现内容中的错误？还是想要补充更多符合主题的内容？《开源指北》欢迎你进行贡献，点击[贡献指南](./../贡献指南.md)了解贡献的具体步骤。