---
title: "BQ"
slug: "BQ"
published: 2027-12-05T01:55:00-05:00
description: ""
tags: ["C++"]
category: "笔记"
draft: true
typora-root-url: ../../../public
---

# BQ

牢记STAR

scenario

task

action

result

# Customer Obsession

1. Tell me a time when you made a suggestion forclients.
   - 告诉我你为客户提出建议的一次 **customer interaction 类**
2. When you're working with a large number ofcustomers, it's tricky to deliver excellent service tothem all.So how do you go about prioritizing your customers' needs?
   - 当您与大量客户合作时，很难为他们提供优质的服务。那么您如何优先考虑客户的需求？ **customer interaction 类**

3. Describe a difficult interaction you had with your client.
   - 描述您与客户的一次困难互动。  **customer interaction 类**
4. Tell me about a time that customers tell you they want something but you know that's not really what they want.
   - 告诉我有一次客户告诉你他们想要某样东西，但你知道那并不是他们真正想要的。  **customer interaction 类**
5. When do you think it's ok to push back or say no to an unreasonable customer request?
   - 您认为什么时候可以拒绝或拒绝不合理的客户要求？  **customer interaction 类**
6. Tell me about a project that you think the requirements are unreasonable or can't be done.When your delivery is different from your customer's expectation.
   - 告诉我一个您认为要求不合理或无法完成的项目。当您的交付与客户的期望不同时。  **customer interaction 类**
7. Give me an example of a time when you did notmeet a client's expectation.What happened, andhow did you attempt to rectify the situation?
   - 举一个你没有达到客户期望的例子。发生了什么，你是如何试图纠正这种情况的？  **customer interaction 类**
8. Who was your most challenging customer?
   - 谁是您最具挑战性的客户？  **customer interaction 类**



- 1 2 基础故事

我曾经和同学一起在软件工程课上开发过一个网站。模拟一个image-host-service. 我们有三个小团队。我们队伍负责服务器后端部分。另外两个队伍分别负责中间件开发和前端开发。

I developed a website with my classmates in a software engineering class. It is an image-host-service. We have three small teams. Our team is responsible for the backend part. The other two teams are responsible for middleware and front-end.

- 1 使用下面的

因为是从零开始开发。所以除了前端部分以外，如果我们服务器部分没有合适的接口，中间件部分很难下手。所以我们在第一次milestone的时候我提出了建议，让负责中间件部分的同学先以前端同学的部分为基础先适配前端的接口，等我把服务器基础部分开发完毕后再由我来进行接口适配。最后我们非常完美的完成了任务，实现了教授所要求的全部功能，比如拉取图片，图片下载，上传信息，登陆注册等等。

Because we developed it from scratch, it will be difficult for our middle-ware team if our back-end team doesn't provide proper API. Therefore, during our first milestone, I suggested that the middleware team develop the front-end related interfaces first. And I will implement the API between the middleware and back-end. In the end, we completed the task perfectly and realized all the functions required by the professor, such as pulling pictures, downloading pictures, uploading information, logging in and registering, and so on.

- 2 使用下面的。

因为是从0开始开发。所以除了前端部分以外，如果我们服务器部分没有合适的接口，中间件部分很难下手。所以我们在第一次milestone的时候我提出了建议，把所有需要的功能按照顺序排序绘制成一个Gantt chart，我会按照顺序开发服务器和中间件模块的接口。这样可以保证不会拖累进度和同步开发。最后我们非常完美的完成了任务，实现了教授所要求的全部功能，比如拉取图片，图片下载，上传信息，登陆注册等等。

Because we developed it from scratch, it will be difficult for our middle-ware team if our back-end team doesn't provide proper API. Therefore, during our first milestone, I suggested that we can sort all the required functions in order, and draw a Gantt chart. Then I will follow the order to develop the interface between middleware and the backend. This way ensures that the requirement will not slow down the development progress. In the end, we completed the task perfectly. We implemented all the functions required by the professor, such as pulling pictures, downloading pictures, uploading information, logging in and registering, and so on.

- 3使用下面的

在开发过程中，中间件的同学的文档功底非常差，因为他们没有任何的开发经验。所以我们后端团队非常难以理解中间件团队到底需要什么样功能的接口，只能不断地自己猜测然后不断的询问，效率非常差。为此，我们两个团队单独开了一次会议。详细地和他一起梳理了开发步骤，和具体可能会用到的功能模块。我们在白板上写下了每一个函数的功能，入参和返回值。两个团队彻头彻尾地规划了一遍具体需要的功能，并且规范化了参数和返回值。最后我们非常完美的完成了任务，实现了教授所要求的全部功能，比如拉取图片，图片下载，上传信息，登陆注册等等。

During the development process, the documentation is written by a member responsible for the middleware. And it is not good because he does not have any development experience. Therefore, it is tough for our back-end team to understand what kind of functional interfaces the middleware team needs. We can only ask constantly, which is very inefficient. For this, I held another meeting which the middleware team. I discussed the development steps and some modules that may be used in detail. We wrote and standardized each function's input parameters and return value. In the end, we completed the task perfectly. We implemented all the functions required by the professor, such as pulling pictures, downloading pictures, uploading information, logging in and registering, and so on.

- 4使用下面的

在开发过程中，我们需要实现一个拉取图片的功能。由于特殊原因所以我离开了项目两天因为我生病了。等我恢复后和我们队伍的另外一名成员开会讨论这两天的进度，我发现他把这个API连接的库的所有照片都预先存了下来，然后放到了数据库内，然后每次用户请求的时候从数据库返回。这明显不是教授想要的。因为为了方便开发和简化作业，这个拉取图片被设置为了固定关键字。所以我的另一名成员才这样做了。我向他阐述了为什么这样做不对，不需要这个数据库而且也不应该这样储存。因为教授真正想要的是让我们直接调用API然后返回。最后我帮助他修改了这部分代码。

During the developing process, I was away from the project for two days due to my illness. After I come back, I hold a meeting with another member to discuss the progress. We need to implement a function to pull the picture. This member misunderstood the professor's point. Because the API was provided by the professor, and it is a special one. The library only contains about 200 pictures, so he requests all photos at once and stores them in the database. And obviously, this is not what the professor wants. So I tell him this is the wrong way because we shouldn't do it like this. Professor's real intention is to let us request the picture each time and return it. Finally, I helped him to revise this part of the code.

- 5使用下面的。

在开发过程中，前端的同学想要通过每次随机的URL去获得同一张图片资源。我并不知道他为什么要这么做，因为URL是资源定位符，我不太可能让同一个资源有无数多个随机的定位符。这不makesence。所以我拒绝了他并且详细的告知了他为什么这样做是无用的，比如防止资源滥用并不应该从URL下手，而是应该从流量防火墙处切入。并且向他讲解了到底URL是什么。最后他和我达成了一致，放弃了这个想法。因为这个提议无论从技术上还是从意义上都是不makesence的。

During the developing process, a team member wants to use a randomized URL to get the same picture. I don't know why he wants to do this because the URL is used to locate a certain resource. Generating a randomized URL to get the same resource is not really possible and does not really make sense. I thought he wanted to prevent the DDOS attack. After that, I discuss some methods for this part. One solution is to splice the session ID into the URL. This will be a kind of randomized URL because the session ID is randomized. But this way is not really well because of its low-security level. Another way is to set up a firewall. After that, both of us agree to use a firewall. 

- 678

目前为止我从未遇到过这种情况。但是我想如果我无法完成的时候，我会给客户介绍我所完成的替代方案，并且告知他为什么这样做可行，也算是某种程度上减少了损失。并且在日后制定计划的时候要详细研讨客户方案的可行性，并及时和客户沟通。







# Are right a lot



1. Tell me about a time you failed/were wrong/made a mistake/had an error in judgment/made a bad decision/regret. 
   - 告诉我你失败/错了/犯了错误/判断错误/做出错误决定/后悔的时候。**mistake类**
2. Tell me about a time when you made a bad/wrong decision and the learning from the experience enabled you to make a good decision later. What did you learn that you were able to apply? 
   - 告诉我你做出错误/错误决定的一次，并且从经验中学习使您能够在以后做出正确的决定。 你学到了什么？ **mistake类**
3. Tell me about a time you disagreed with a colleague or boss. What is the process you used to work it out?
   - 告诉我你与同事或老板意见相左的时候。 你用来解决它的过程是什么？ **interpersonal conflict 类**
4. Tell me about a time you disagreed with a colleague or boss, and you were right. 
   - 告诉我一次你不同意同事或老板的方法，最后你是对的。 **interpersonal conflict 类**
5. Tell me about a time you disagreed with a colleague or boss, and you were wrong.
   - 告诉我一次你不同意同事或老板的方法，最后你是错的。 **interpersonal conflict 类**
6. Tell me about a time when you had to work with incomplete data or information. 
   - 告诉我你不得不在目前信息或数据不完整的情况下进行工作的一次。 **incomplete data 类**
7. Tell me about a time when you had to work with incomplete data and you failed.
   - 告诉我你不得不在目前信息或数据不完整的情况下进行工作的一次。并且你失败了  **incomplete data 类**





- **1, 2, 5可以用下面的故事**

  - 我曾经参与过字节跳动举办的一个青训营。具体目的是实现一个simplified server fo tiktok。
  
  
    - 一开始我们并没有预料到会有一个非常大的压测场景，也就是高并发。所以我当时开发的储存层没有设计缓存。当时在milestone的时候谈到了这个问题，但是我并没有同意在当时就增加缓存层。因为设计缓存层需要额外的时间和技术准备。增加缓存层会导致需要重新设计所有的数据库表项。并且此时已经到了项目中期，后续的所有开发都需要建立在储存层已经开发完毕的基础上。同时开发两套方案或立刻进行重构的成本太高。而且也并不一定会有高并发场景。
  
  I once participated in a summer camp held by ByteDance. Our mission is to implement a simplified server for TikTok. In the beginning, we didn't expect that there would have a  high concurrency stress test. So I didn't design the cache layer for our project. Actually, in our mid-project milestone, we discussed this topic. But at that time, adding a cache layer was too late, and it needed to redesign the repository layer and all database tables. It will cost extra time to do this, and all follow-up developments need the repository layer to continue.


- **针对5 增加下面这一部分**

  - **我非常能理解我的队友为什么考虑到了这样的问题，因为高并发量是所有项目一定会遇到的问题，只是时间早晚的问题。所以我提出的解决方案是暂时先不增加缓存层，采用任务队列的方式限制一下链接请求，这样可以保证已有的链接的稳定性。但是最后我错了。**
  
  I can fully understand why my teammates have considered such a problem because high concurrency is a problem that all server projects will encounter. It's just a matter of time. So the solution I proposed is to add a task queue to limit the connection request, which can ensure the stability of the existing link rather than add a cache layer. But in the end, I was wrong.
  
  - 在后续准备项目上线的时候，突然主办方提出：每一个小组的项目需要压测。结果放到平台进行压测的时候出现了非常大的延迟和超时导致的链接丢失现象。因为每一次用户请求都需要查找对应的表。而且表的设计有一些粗糙，导致可能有的请求需要多次查表才能返回。
  
  When we were going to submit our project, the organizer suddenly proposed that each team's project needed to do stress testing. When we were doing stress testing, we found some problems. First, some client connections have high latency, and some connection was lost because of the time out. We found this problem is because every user request needs to look up the corresponding table in the database. Moreover, the table's design is somewhat imperfect, so servers need to access multiple tables in some scenarios to get a result for a single request.
  
  
    - 我们发现了这个问题，用三天时间紧急增加了一个缓存层，也就是重新设计了整个流程，添加了redis做为mysql的缓存部分。同时针对多个表进行了索引优化。成功的经受住了压力测试。
  
  
    - 在这次经历中我学到了在实际项目开发中，必须要考虑到极端情况比如高并发场景，并且预留充分时间进行系统调优。
  
  We found this problem and urgently added a cache layer in three days. We added Redis as the cache layer of MySQL. At the same time, we redesigned some tables and applied some index optimization and query optimization. After that, we passed the stress test successfully. In this experience, I learned that we have to consider extreme situations, such as high concurrency scenarios in the real project, as early as possible and reserve some time to test the project.


- **3 4可以用下面的故事**
  - 在我大学的软件工程课上，我们被要求开发一个软件。最后我们的项目是一个在线的马赛克风格照片的生成器。你可以上传自己的照片池来使用你自定义的照片生成马赛克风格的图样。由于这个软件是一个在线的，所以我们会有一个登陆系统。一开始我们在第一次milestone的时候，团队里的其中一位成员并不打算在页面艺术上花时间，他认为界面样式无所谓，功能才是核心。但是我并不同意。因为我认为页面的样式是吸引客户点击我们网站非常重要的因素。为此我特意设计了一个全新的UI界面，并且把两种界面截图，以问卷的形式发放给了我们的同学和朋友，问他们哪一种更好。答案非常明显是我的那一种更好。但是我也能非常理解为什么他并不同意在艺术风格花时间，因为可能会影响项目进度。为此，我额外承担了这部分任务。以在追求更好的UI的同时跟上项目进度。最后在项目验收阶段，教授针对我们的UI界面提出了额外表扬。

I took a software engineering class, and we were asked to develop an application. We decide to make an online mosaic art-style photo generator. Users can upload their own photo pool to generate mosaic-style photos. Since it is an online application, we will have a login/register system. At the beginning of our first milestone, one of the team members didn't plan to spend time on the UI of the webpage. He believed that the interface style didn't matter. But I disagree with him. Because I think the style of the page is very important for attracting customers to use our application. So, I designed a brand new UI for our webpage. I take some screenshots of the before-modified UI and the after-modified UI and use them to make a questionnaire. Then send it to our classmates and friends, asking them which one is better. The answer is obvious. Mine is better. But I can also understand why he doesn't agree to spend time on the UI because it might affect the project's progress. To this end, I took on this additional task. Keep up with projects while pursuing a better UI. Finally, our professor praised our UI when we were presenting our project.


- **6 7 可以用下面的故事**
  - 我曾经尝试过使用一个叫做WDL 的框架去尝试开发一款音频插件。因为这个框架非常小众，并没有多少人参与维护，所以文档非常简陋。并且在网上并不能查到相关的教学或介绍。所以 我尝试通过读源代码来找到一些问题的答案。但是我不可能读完整个框架的源代码，所以我决定给作者发邮件并且去stack overflow提问。

I have tried to develop an audio plugin using a framework called WDL. Because this framework is not popular and does not has many people involved in maintaining it, so the document is not very useful. And also, for this reason, I didn't find too many instructions or tutorials for this framework. So I try to find answers of some questions by reading the source code. But I couldn't read the entire source code of the framework, so I decided to email the author and ask questions via stack overflow.


  - **如果是6，成功了**
    - 作者回复了我的邮件，告诉了我大概的步骤和思路。

  - **如果是7，失败了**
    - 作者没有回复邮件，也没有人回答stack overflow的问题

# Ownership

1. Provide an example of when you personally demonstrate ownership.
     - 举一个例子你关于你展示了你的主人翁意识 **above & beyound 类**
2. Tell me about a time you went above and beyond.
     - 举一个例子你做到了更多 **above & beyound 类**
3.  Tell me about a time you decided to take on a project instead of being assigned to you.
      - 举一个例子你自己主动承担了一个项目而不是等候别人给你分配。 **above & beyound 类**
4. Tell me about a time you step outside of your job scope and solved a problem
     - 举一个例子你在超出自己工作范围的时候解决了一个问题 **above & beyound 类**
5. Tell me about a time when you took on something significant outside your area of responsibility. Why was it important? What was the outcome?
     - 告诉我你有一次在你的职责范围之外承担了一些重要的事情。 为什么它很重要？ 结果是什么？ **above & beyound 类**
6. Describe a project or idea (not necessarily your own) that was implemented primarily because of your efforts.What was your role? What was theoutcome?

     - 描述一个主要由于您的努力而实施的项目或想法（不一定是您自己的）。您的角色是什么？ 结果是什么？ **above & beyound 类**


- **基础故事：**
  - 在校期间，我曾经有一个项目是关于推特的词汇热度分析并生成热度图。我们有六个人，分成了两个小组。我所在的小组是负责拉取推特数据并进行分割和过滤。由于我对这个项目非常感兴趣，而且也做过相似的一些小项目，所以我同时也关注着另一个小队的任务。他们主要负责计算热度并且生成热度图，也负责UI部分。
  
  I did a course project which is analyze the frequency of words from Twitter. And it will generate a heatmap to display the result. We have six group members and are split into two groups. My mission is to pull the data from Twitter, split it into words, and do some data cleaning. Because I'm really interested in this project and have done some similar projects, I kept my eye on another team. Their mission is to calculate the heat, generate the head map and do some UI parts.
  
- **1 2 3 4都可以用下面这部分。**
  - 在另一小组进行milestone的时候，我也经常会旁听然后给予一些建议。因为我曾做过相似的可视化项目。在项目中期，我们小组的数据部分已经开发完毕，下一步就是交给他们继续做可视化部分。但是他们的进度不太乐观，因为他们没有之前的开发经验。所以我主动加入了另一个小队。协助他们进行热度图的生成并且进行UI的调整。最后我们是第一个完成任务的小队，并且在综合评分中得到了第一。
  
  I always join another team's meeting and give them some advice because I have similar development experiences. Halfway through the project, I finished my part. And I didn't stop there. I found the other team was got some issues and got stuck. So I joined that team initiatively and tried to help them. I help them to use some libraries to generate the heat map and adjust some layout and UI. Finally, we were the first team to finish the project and get the highest score in the class.


- **5额外添加**
  
  - 并且中间由于教授提供的文档有错误，所以我还额外花了部分时间和教授沟通关于文档的问题。教授弄反了经纬度的入参导致我们一直无法得到正确的结果。教授甚至都没有意识到这个错误因为我们是速度最快的队伍。
  
  And during the project, I found that the document provided by our professor had some errors. Such some function is wrong, and the parameter of the dataset is incorrect. One of the issues is professor reversed the latitude and longitude, so I could not get the correct result. So I spent some extra time revising the document and talking with the professor. Professor even didn't realize this problem because we were the fastest group. And professor re-distributed the document and added my name on the document as the reviser.
- **6 去掉1234和5的部分改为下面部分**
  - 在进行数据处理的操作中，我提出可以新增一个额外的feature，就是保留原推特的语句，也就是维持语义。因为可能会有人想查看每一个词汇在不同地区的热度的同时，查看具体的推文或者语句。但是我的小队成员似乎并不感兴趣，于是我独立完成了这个模块的开发。在最后期末的项目展示上，这个模块的效果非常好，得到了教授的额外表扬和extra credit。

When I was doing the data processing, I proposed that we can add an additional function: keep the original twitter content and its link. Because there may be some people who want to check the popularity of each word in different regions, and also check specific tweets simultaneously. But my teammate doesn't get interested in it. So I developed this module individually and presented this module as an additional function during the presentation. Our professor gave me some extra credit and acknowledged my thought.





7. Did you have to push back a request/ask?
   - 你是否经历过必须推脱的请求？ **push back & conflict 类**
8.  lf you have conflicting goals, how do you make trade-offs?
   - 如果你有相互冲突的目标，你如何权衡 **push back & conflict 类** 
9. Tell me about a time you had to sacrifice short term gains for long-term goals.
   - 告诉我你不得不为了长期目标而牺牲短期收益的时候。**push back & conflict 类**
10. Tell me about a time when you had to leave a task unfinished.
    - 告诉我你不得不离开未完成的任务的的时候 。**push back & conflict 类**
11. Tell me about a time when you had to work on a project with unclear responsibilities.
    - 告诉我你曾经在一个职责不明确的项目上工作的经历。 **push back & conflict 类**

- **基础故事：**
  - 我曾经和别人一起开发过一个linux web server。
- **7 8 9 10** 
  - 我负责除HTTP解析以外的全部部分。另一名成员想速战速决，不想为了性能浪费太多时间。所以他希望我可以尽快的服务器的基础部分。但是我觉得不应该这么做。首先我非常理解他的想法，因为服务器基础部分没有完成的时候，他没有办法更深入的进行HTTP解析模块的开发。但是我告诉他，linux webserver的性能非常重要，所以我们需要使用IO 多路复用和线程池来提升性能。同时为了方便我们后序的debug，我应该同时把日志模块加入进去。这样在后续的开发过程中，不仅性能可以提升，而且还可以更快速的定位开发中的问题。
  - 7 ：所以我pushback了他的快速开发请求。
  - 8：所以我们最后还是决定了使用我的方案
  - 9：因为开发完毕后，重新开发底层模块非常费时。所以着眼于长期收益，可以牺牲现在的开发进度。
  - 10：但是开发中途，我们发现开发一个性能很好的异步日志模块难度较大。最后我们为了可以按时开发完毕整个项目，我们选用了同步日志的方式，不得不暂停异步日志模块。
  - 最后我们成功开发了webserver并且满足了C10k的性能指标。

- 11
  - 当时我们对整个webserver的架构并不是很清晰，也没有经验。于是我主动和他说，我可以负责服务器的基础部分。你先进行HTTP模块的开发。在开发过程中，为了之后的性能和便于查找开发过程中遇到的问题，我决定先进行线程池和日志系统的开发。但是开发中途，我们发现开发一个性能很好的异步日志模块难度较大。最后我们为了可以按时开发完毕整个项目，我们选用了同步日志的方式。并且在现有场景下，同步日志和异步日志的差距并不算大。所以我们决定继续使用同步日志的方案。最后我们成功开发了webserver并且满足了C10k的性能指标。

12. Describe a time you transitioned a project to another person/team.
    - 描述一下你把项目转移给其他人的时候 **transition 类**

这个可以照着上面的改一改来

- 我曾经开发过一个linux web server。当时我有一个同学也想学习C++，并且想尝试做一个项目。我给他推荐了linux webserver。因为这个项目不仅可以学习c++，而且可以学习一些操作系统底层和网络通信相关的知识。他想让我给他提供一些资料。于是我依照我的code，写了非常详细的具体过程，可能用到的函数，可能需要进行的操作和一些需要注意的事情。包括一些功能近似的函数的区别。同时提供给他几套网上的资料让他学习网络通信相关的内容。最后他也成功开发出来了一个webserver。

13. Give an example of when you saw a peer struggling and decided to set in and help. What was the situation and what actions did you take?What was the outcome? 
    - 举一个例子，说明你看到一个同伴在挣扎并决定介入并提供帮助。 当时情况如何，你采取了哪些行动？结果如何？  **help peers 类**

这个可以参照前面的推特来说。

- 在校期间，我曾经有一个项目是关于推特的词汇热度分析并生成热度图。我们有六个人，分成了两个小队。我所在的小队是负责拉取推特数据并进行分割和过滤。由于我对这个项目非常感兴趣，而且也做过相似的一些小项目，所以我同时也关注着另一个小队的任务。他们主要负责计算热度并且生成热度图，也负责UI部分。
- 在项目中期，我们小组的数据部分已经开发完毕，下一步就是交给他们继续做可视化部分。但是他们的进度不太乐观，因为他们没有之前的开发经验。所以我主动加入了另一个小队。协助他们进行热度图的生成并且进行UI的调整。最后我们是第一个完成任务的小队，并且在综合评分中得到了第一。



# Bias for Action

Calculated risk指的是能感知项目的潜在风险，并且进行评估。知道如果项目走向不好，最坏的结果，是否会影响目前的工作。如果会影响，为什么需要承担风险。看到了哪些收益大于风险的地方？如果失败了如何恢复？



1. Describe a time you took a big risk. **calculate risk类**
   - 描述一次你冒很大风险的经历。
2. How to take a calculated risk? **calculate risk类**
   - 如何承担计算风险？
3. Tell me about a time when you took a calculated risk. **calculate risk类**
   - 讲述一次你承担过的计算风险。
4. Tell me about a time when you took a risk in yourwork and then failed **calculate risk类**
   - 告诉我你在工作中冒险然后失败的时候。





- 基础故事：云服务部署。1 2 3可以用。

我们曾经合作部署过一个分布式系统的数据储存服务。主要功能是用户可以上传下载储存在云端的文件。这是一个course  project。但是在学期结束的时候，我们的期末考试就是把我们的项目展示给来参加这个展示的人。我们教授真的请来了六七个不同公司的人，其他课程的教授和一些路人来对每一个组的项目进行评估。最开始我们没有考虑特别多，因为资源受限所以我们只有四个云服务器。然后部署的时候采用的是手动部署。开发都比较顺利。但是在临进行评估的前两周的时候我突然意识到，我们相对于course project，更多的是一种产品。我们的产品肯定不能只有四台服务器，一旦数据量很大或者用户很多的时候这是根本不可能承受得住的。但是我们可以手动部署四台服务器，但是手动部署四十台，四百台是不可能的。所以我紧急和团队成员开会，讨论如何解决这个问题。我的方案是使用ansible进行自动化部署，然后编写playbooks来对节点进行注册。因为项目采用的是kafka。所以需要向zookeeper进行节点注册。但是风险在于这是一个工程量比较大的任务，很有可能无法完成。我没有自动化部署的丰富经验，必须相当于从空白开始。而且自动化部署可能会导致很多奇怪的难以排查的错误，会十分耗费时间。最坏的情况就是我们在项目结束之前无法使用自动化部署，必须使用手动部署。但是我最后依旧决定开始使用ansible进行自动化部署。然后编写对应的脚本。最后我大约花费了两周时间对服务器进行了ansible的部署，playbook的编写并且对服务器进行了测试。自动化部署非常成功。尽管我们只有四个server instance能够让我们进行测试，但是用于服务的服务器的部署方案都是相通的。四台和四十台区别不大，所以我们认为是非常成功的。同时我们在报告中提出了自动化部署方案，教授和评审对这个功能表示非常满意。因为非常贴合用户需求。

- 4的话就是修改一下时间，导致时间范围内没有完成任务。



5. Tell me about a time you needed to get information from someone who wasn't very responsive. What did you do? **missing information 类**
   - 告诉我你需要从反应不快的人那里获取信息的时间。 你做了什么？
6. Tell me about a time you had to make a decision with incomplete information. How did you make it, and what was the  outcome? **missing information 类**
   - 告诉我你不得不在不完整信息的情况下做出决定的时候。 你是怎么做到的，结果如何？
7. Tell me about a strategic decision you had to make without clear data or benchmarks. **missing information 类**
   - 告诉我你必须在没有明确数据或基准的情况下做出的战略决策。
8. Tell me about a time when you didn't have enough data to make the right decision. **missing information 类**
   - 告诉我你没有足够的数据做出正确决定的时候。
9. Tell me about a time when you had to analyze facts quickly, define key issues, and respond immediately to a situation. What was the outcome? **missing information 类**
   - 告诉我你必须快速分析事实、定义关键问题并立即对情况做出反应的经历。 结果是什么？
10. Tell me about a time when you have worked against tight deadlines and **didn't have the time to consider all options** before making a decision. How much time did you have? What approach did you take? **missing information 类**
   - 告诉我你曾经在紧迫的期限内工作，并且没有时间在做出决定之前考虑所有选项。 你有多少时间？ 你采取了什么方法？



- 基础故事。5~10都可以用。注意括号。参考字节那一次

我曾参加过一个字节跳过官方举办的青训营。目标是组队完成一个mini tiktok server。很显然，我们不可能拿得到一个非常official的client app，所以字节官方给我们制作了一个scratch的满足basic requirement的客户端用来进行服务端的测试。但是他的文档和底层细节都没有公布。在项目即将收尾的时候，这个客户端增加了几个新的接口。可以允许用户更换avatar， banner和签名。签名没有问题，但是涉及到图片的地方出现了问题。这个图像在上传后显示不出来。一直显示无法解析链接。***我们查阅了文档部分没有相关信息。（体现消息不完整）* *然后我们又去询问了举办方这个问题的答复。但是显而易见这个回复不会那么快，又恰逢周末。（体现反应不快）***

***同时项目截止时间只有两天了，也就是下一周的周一。等候主办方回复显然不现实。（第六个问题）*** 

之后我尝试了许多方法，比如使用wireshark抓包去查看请求。这个部署还是相对麻烦的，因为需要在android 虚拟环境下抓包。然后我突然发现客户端压根就没有发送这个获取头像和banner的请求。所以我严重怀疑是http链接的解析被屏蔽了！！因为为了方便测试，我们当时使用的avatar和banner的链接是一个静态的链接并且只使用了HTTP。在用HTTP的时候客户端可以进行和服务端通信，完成基础请求。但是针对banner和avatar的获取，客户端屏蔽掉了HTTP的链接。所以无法获取对应的图片。之后我们紧急把图片上传到支持HTTPS的image hosting service后。可以进行正常的通信了。圆满完成任务。

这一点其实我们也很奇怪。可能是因为自签证书非常麻烦，客户端被修改为了可以使用HTTP进行服务端基础通信。所以我们没有被要求服务器使用HTTPS。但是可能是avatar和banner这部分主办方忘记修改了，导致为了安全所以屏蔽掉了HTTP链接。







11. Describe a time when you saw some problem and took the initiative to correct it rather than waiting for someone else to do it. **take action类**
   - 描述一次你看到一些问题并主动纠正而不是等待别人去做的时候。
12. Describe a situation where you made an important business decision without consulting your manager. What was the situation, and how did it turn out? **take action类**
   - 描述您在未咨询经理的情况下做出重要业务决策的情况。 当时情况如何，结果如何？
13. Have you ever done something without asking for permission from your manager? **take action类**
   - 您是否曾在未经经理许可的情况下做某事？
14. Give an example of when you had to make an important decision and had to decide between going forward or gathering more information. What did you do? What information is necessary for you to have before acting? **take action类**
   - 举例说明您何时必须做出重要决定，并且必须在继续前进或收集更多信息之间做出决定。 你做了什么？ 在采取行动之前，您需要哪些信息？
15. Tell me a time when you have to compromise something to meet the deadline **take action类**
   - 告诉我一个你必须妥协以赶上最后期限的时间
16. Tell me a time when you must deliver an unperfect result/project.  **take action类**
   - 告诉我你必须交付不完美的结果/项目的时间。
17. Made a difficult decision with input from many different sources **take action类**
   - 根据来自许多不同来源的意见做出了艰难的决定



- 11 复用ownership的第三个。
- 12和13没有经历
- 14 复用第二个
- 15 16
  - 曾经在软件工程课上，我们的期末考试是在24小时之内实现一个拥有文档中列出的全部功能的网站。我把它视为一个真正的挑战。因为只要我拿到了100%那么我这门课最后的总成绩也会是100%。大概要求是使用bootstrap框架和给定api实现一个美国部分大学的信息预览页面。整体来说并不十分困难。但是有一个小的细节问题让我卡住了很久，就是这个网页如果其中某一行的grid的layout会由于文字数量过多导致拉长，会导致这一行的每一个grid都会更长，比较影响美观。最后的评分有一项是针对网页的美观度进行评分的。所以我花了大约四个小时思考这个问题如何解决。我本想制作成浮动卡片的样式，但是由于我不精通HTML和CSS，而且限定了必须使用bootstrap框架导致这个功能最后还是无法实现。做为compromise，我使用了一个read more按钮，如果文字过长则直接跳转至学校官网。也算是在某种程度上实现了在功能要求和美观要求上的折中。在我心目中这个项目也算是并不完美。因为没有达成我想要展示的目标。最后在项目报告里面我详细解释了这个问题。教授的回复是他原本没有想到这个问题，但是我是为数不多的主动去解决了这个问题的学生。所以我依旧拿到了满分。
- 17 复用第一个模板云服务部署。
  - 我们曾经合作部署过一个分布式系统的数据储存服务。主要功能是用户可以上传下载储存在云端的文件。这是一个course  project。但是在学期结束的时候，我们的期末考试就是把我们的项目展示给来参加这个展示的人。我们教授真的请来了六七个不同公司的人，其他课程的教授和一些路人来对每一个组的项目进行评估。在开始的时候，由于是云服务，并且是分布式部署。我打算把一些功能使用rpc的方式实现。但是有几位成员不同意。首先是rpc的安装和编译复杂。其次是大家都没有使用过，上手并不容易。第三点是我们的服务不会有如此大的负载。我向他们说明了这是学习rpc的一个不错的机会，并且我们要假设我们会面临这种高负载的场景，因为我们要模拟直面客户去推销产品。但是他们依旧不同意。finally，We vote to decide whether to use this method. The result is not to use rpc. So I have to give up my plan.



# Think Big

1. Tell me about a time when you went way beyondthe scope of the project and delivered. **achievement 类**
   - 告诉我次你超越项目范围并交付。
2. Tell me about a time you took a calculated risk inorder to achieve a professional goal. What werethe tradeoffs? What was the outcome? **achievement 类**
   - 告诉我你有一次为了实现职业目标而承担了一定的风险。有哪些权衡？结果是什么？
3. Tell me about your proudest professional achievement. **achievement 类**
   - 告诉我你最自豪的职业成就。
4. Give me an example of a radical approach to aproblem you proposed. What was the problemand why did you feel it required a completely different way of thinking about it? Was yourapproach successful? **achievement 类**
   - 举一个你提出的解决问题的激进方法的例子。问题是什么？为什么你觉得它需要一种完全不同的思考方式？你的方法成功了吗？
5. How do you drive adoption for your vision/ideas?How do you know how well your idea or vision hasbeen adopted by other teams or partners? Give aspecific example highlighting one of your ideas. **achievement 类**
   - 您如何推动采用您的愿景/想法？您如何知道您的想法或愿景已被其他团队或合作伙伴采用的程度？举一个具体的例子来突出你的一个想法。
6. Tell me about the time you were working to naninitiative or goal and saw an opportunity to do something much bigger than the initial focus. **achievement 类**
   - 告诉我你在制定计划或目标的时候，看到了做一些比最初关注更大的事情的机会。
7. Tell me about a time you looked at a key process that was working well and questioned whether it was still the right one. What assumptions wereyou questioning and why? Did you end up makinga change to the process? **achievement 类**
   - 告诉我有一次你看到一个运行良好的关键流程并质疑它是否仍然是正确的。你质疑什么假设，为什么？你最终改变了流程吗？



- 1 参考ownership
- 2 参考bias的1
- 3 问到了就随机应变
- 4 5故事使用马赛克项目的故事。
  - 在我大学的软件工程课上，我们被要求开发一个软件。最后我们的项目是一个在线的马赛克风格照片的生成器。你可以上传自己的照片池来使用你自定义的照片生成马赛克风格的图样。我们的软件有一个特殊功能，就是你可以点击已经生成的照片的某一部分（那是一张照片池里的图片），然后使用这张图片做为新的参考图片。生成照片并不是最大的难点，因为有很多成熟的技术。最大的难点是如何处理照片池。因为这个项目是一个在线的项目，基于HTML。所以需要思考如何处理meta data。一开始我们是打算使用类似于SQL的方法来查找每一张照片，然后把照片信息放入HTML页面然后arrange it. 不过性能很差，页面会卡顿严重。随后我的思考是使用key-value的方式对每一张照片进行encode，然后直接使用key来进行查找，使用redis这种非关系型数据库。速度提升的非常快。
- 6使用服务器的例子。参考线程池和异步日志。
- 7：我曾经参与过一个开源项目。主要是和他人一起协作编写一些设计模式的教程。在有一个设计模式的代码示范部分，我记得是 state pattern，他没有回收内存，我提交了issue之后他们修改了这一部分代码。后来也没有什么反应。又一次我无意间看过代码后觉得非常疑惑因为有一个函数被重复调用了。于是我亲自跑了这个代码，果然发生了段错误。然后我提交了pull request修复了这个错误。最后我发邮件给项目的发起者，建议他们在放出示例代码之前务必亲自跑一下代码，以免对读者产生误导。

# Invent & Simplify

1. What improvements have you made at your current company? **innovation & improvement 类**
   - 你在现在的公司做了哪些改进？
2. Tell me a time when you solved a problem in aninnovative way.  **innovation & improvement 类**
   -  告诉我你以创新方式解决问题的经历。
3. Tell me about a time when you invented something.**innovation & improvement 类**
   - 告诉我你发明某物的时间。
4. What is the most innovative project you've workedon?**innovation & improvement 类**
   - 你做过的最具创新性的项目是什么？
5. What is your proudest/biggest innovation?**innovation & improvement 类**
   - 您最自豪/最大的创新是什么？
6. Tell me about an out-of-the-box idea you had or adecision you made that had a big impact on your business. 
   - 告诉我你有一个开箱即用的想法或你做出的对你的业务产生重大影响的决定。
7. Tell me about a time when you have a simple solution to a complex problem.
   - 告诉我你有一个复杂问题的简单解决方案的时候。



- 1 3 6 7 没经验
- 2 勉强使用think big的 4和5
- 4，5套用multi band equalizer。创新点在于用户可以自定义UI，也就是背景图片和对应组件的颜色。



# Learn and Be Curious

1. Tell me about a time you did something outsideyour responsibility? **learn new thing类**
   - 告诉我你有一次做过超出你职责范围的事情吗？
2. Tell me about a time when you influenced a change by only asking questions. **learn new thing类**
   - 告诉我一次你只通过提问就影响了一个改变的决定。
3. Tell me about a time when you solved a problemthrough just superior knowledge or observation. **learn new thing类**
   -  告诉我一次你通过高超的知识或观察解决问题的经历。
4. Have you ever learned something new by yourselfand ended up using what you learn to solve problems at work? **learn new thing类**
   - 你有没有自己学过一些新东西并最终用你学到的东西来解决工作中的问题？
5. How do you find the time to acquire newknowledge? **learn new thing类**
   - 你如何找到时间获取新知识？

# Dive Deep

1. Give me an example of when you used data tomake a decision/solve a problem. **with data类**
   - 给我一个例子，说明你何时使用数据做出决定/解决问题
2. Give me an example of you diving deep into datato figure out the root cause of an issue. **with data类**
   - 给我一个你深入研究数据以找出问题根本原因的例子
3. Have you ever leveraged data to develop astrategy. **with data类** 
   - 您是否曾经利用数据制定战略
4. Tell me about a problem you had to solve thatrequired in-depth thought and analysis. How didyou know you were focusing on the right things?
   - 告诉我一个你必须解决的需要深入思考和分析的问题。 你怎么知道你专注于正确的事情？
5. Walk me through a big problem in your organization that you helped to solve. How did youbecome aware of it? What info did you gather,what was missing, and how did you fill the gaps?Did you do a postmortem analysis and what didyou learn?
   - 告诉我您帮助解决的组织中的一个大问题。 你是怎么知道的？ 你收集了什么信息，遗漏了什么，你是如何填补空白的？你做了事后分析，你学到了什么？
6. when you were trying to understand a complexproblem on your team and you had to dig into thedetails.
   - 当您试图了解团队中的一个复杂问题时，您必须深入研究细节。
7. Give me two examples of when you did more than what was required in any job experience.
   - 给我两个例子，说明你比要求的做得更多。
8. Tell me about something that you learnt recently inyour role.
   - 告诉我你最近在你的角色中学到的一些东西。

# Insist on the highest standards

1. Tell me about a time when you couldn't meet your expectations on a project. **miss expextration/goal 类**
   - 告诉我你不能满足你对项目的期望的一次。
2. What was a goal you didn't reach or wish you could have improved on? **miss expextration/goal 类**
   - 哪一个目标是你没有达成的或是你希望去提升的。
3. Give me an example of a goal you've had where you wish you had done better. What was the goaland how could you have improved on it? **miss expextration/goal 类**
   - 举一个你希望自己做得更好的目标的例子。 目标是什么，你如何改进它？
4. Tell me about a time when you've been unsatisfiedwith the status quo（现状）. What did you do to change it? Were you successful? **improve an already good system 类**
   - 告诉我你对现状不满意的时候。 你做了什么来改变它？你成功了吗？
5. Tell me about a time you wouldn't compromise on achieving a great outcome when others felt something was already good enough. What wasthe situation?  **improve an already good system 类**
   - 告诉我有一次当别人觉得某件事已经足够好时，你不会为了取得好的结果而妥协。 当时情况如何？
6. Describe the most significant, continuous improvement project that you've led. What wasthe catalyst for this change and how did you go about it?  **improve an already good system 类**
   - 描述您领导的最重要的持续改进项目。 这种变化的催化剂是什么，你是如何做到的？
7. Tell me about a time when you worked to improvethe quality of a product / service / solution thatwas already getting good customer feedback?Why did you think it needed more improvement?  **improve an already good system 类**
   - 告诉我你曾经努力提高已经获得良好客户反馈的产品/服务/解决方案的质量？为什么你认为它需要更多改进？
8. Give an example where you refused to compromise your standards around quality/customer service, etc.Why did you feel sostrongly about the situation? What were the consequences? The result?  **improve an already good system 类**
   - 举个例子，你拒绝在质量/客户服务等方面妥协你的标准。为什么你对这种情况感觉如此强烈？ 后果是什么？ 结果如何？



# Earn Trust

1. Have you ever worked on something hard andthen failed? **mistake / failure 类**
   - 你有没有很努力的做一件事情然后失败了？
2. Tell me about a time you made a mistakel failed. **mistake / failure 类**
   - 告诉我一次你犯错失败的经历
3. Tell me about a time when you couldn't meet yourexpectations on a project. **mistake / failure 类**
   - 告诉我一次你无法达到你对项目的期望的经历。
4. Tell me about a time when you had to tellsomeone a harsh truth. **mistake / failure 类**
   - 告诉我有一次你不得不告诉别人一个残酷的事实。
5. Tell me about a time you were 50%/75% on aproject and found you have made a mistake andhad to change direction. **mistake / failure 类**
   - 告诉我一次你在一个项目上 50%/75% 的时候发现你犯了一个错误，不得不改变方向
6. Tell me about a time you uncovered a problem on your team. **inpersonal interaction 类**
   - 讲述一次你在团队中发现了一个问题的经历。
7. Do you suggest something to the team and help toachieve a better outcome?  **inpersonal interaction 类**
   - 您是否向团队提出建议并帮助取得更好的结果？
8. How do you handle teammates you don't like?Tell me about a time when you had to work with a'difficult' coworker.  **inpersonal interaction 类**
   - 你如何处理你不喜欢的队友？告诉我你不得不和一个“难相处”的同事一起工作的时候。
9. Tell me about a time you gave team members suggestive feedback.  **inpersonal interaction 类**
   - 告诉我你给团队成员建议性反馈的一次
10. Tell me about a time you had a conflict with your teammates, how did you persuade them?  **inpersonal interaction 类**
    - 说说你和队友发生冲突的时候，你是怎么说服他们的？
11. Tell me about a time you help your teammate .  **inpersonal interaction 类**
    - 告诉我你帮助队友的一次经历
12. What's the worst feedback your boss gave you?   **inpersonal interaction 类**
    - 你的老板给你的最糟糕的反馈是什么？
13. Give me an example of a time when someone onyour team challenged you to think differently about a problem.  **inpersonal interaction 类**
    - 举个例子，当你团队中的某个人挑战你以不同的方式思考问题时
14. Tell me about a time your teammates had adifferent opinion than you and you were pursued. inpersonal interaction 类
    - 说说有一次你的队友和你意见不同，我被迫接受了。
15. Tell me about a time when someone (peer, teammate, supervisor) criticized you about a pieceof work/analysis that you delivered.How did youreact? What was the outcome?  **inpersonal interaction 类**
    - 告诉我有一次有人（同事、队友、主管）批评了你所做的工作/分析。你的反应如何？ 结果是什么？

# Deliver Results

1. Describe a project that you not only finish but alsoaccomplish more.
   - 描述一个你不仅完成而且完成更多的项目。
2. Describe a time when you had to face a particularly challenging situation while working ona project and what you did to overcome it.
   - 描述你在一个项目上工作时不得不面对一个特别具有挑战性的情况的时候，以及你为克服它所做的事情。
3. Give me an example of a time you struggled with something and then turned it around.
   - 给我一个例子，你曾经为某事挣扎，然后茅塞顿开
4. Tell me a project you finish where no clearinstruction was given.
   - 告诉我一个你完成的项目，但没有给出明确的指示。
5. What's your most challenging problem/project?What's the project you are most proud of?
   - 你最具挑战性的问题/项目是什么？你最引以为豪的项目是什么？
6. What's the most complicated problem you've everworked on?
   - 你解决过的最复杂的问题是什么？



# 杂项

linux webserver涵盖了很多的知识。包括socket programming，multi threading，operating system和比较深层的c++知识。 在这个过程中我没有使用任何的第三方库。实现的功能包括线程池，HTTP解析，超时链接检测和异步日志系统都是我自己写的。同时使用了IO多路复用。
在开发过程中遇到了比较多的难点。第一个难点是HTTP解析的部分。因为这里必须要小心计算每一个部分的长度然后进行分割，再分段解析。其次就是需要注意线程安全。尤其是在使用多线程模型的时候，我花费了比较长的时间去调整mutex的粒度。因为粒度过大会影响服务器的性能。最后我采用了生产者消费者模型和阻塞队列来实现这一部分。针对内存泄漏，我使用了valgrind来进行检查。



Linux webserver covers a lot of knowledge. It includes socket programming, multi-threading, operating system, and more in-depth c++ knowledge. I didn't use any 3rd part library in this project. I implemented functions including thread pool, HTTP parsing, timeout link detection and asynchronous logging system. All of those are written by myself.  I also used IO multiplexing to improve the performance of the server.

The first difficulty is HTTP parsing. Because we must carefully calculate the length of each part and then divide it, and then parse it into segments.

The second is thread safety. Especially when using a multi-threaded model, I spent a lot of time adjusting the granularity of mutex. Because if the mutex granularity is too coarse, it will affect the server's performance.

In the end, I used the producer-consumer model and blocking queue to implement this part. For memory leaks, I used valgrind to check.





展现领导力：

我曾参加过一个字节跳过官方举办的青训营。目标是组队完成一个mini tiktok server。我们的队伍一共有三个人。由于在这之前我完成了我的linux webserver，所以对整个开发过程有一些了解。所以在第一次meeting的时候，我就针对项目内容进行了深入讨论。首先我讨论了有哪些框架可以使用。由于这个项目必须使用golang进行开发，我们对golang并不是很熟悉。但是我提前进行了调查，最后我选定了GIN框架。GIN框架可以比较轻松的进行HTTP解析。然后我和他们阐述了我们应该使用MVC结构来进行开发，模块化的开发使得代码容易维护而且易于新增功能。最后我向他们讲述了几个需要考虑的问题。首先是并发问题。由于golang语言本身有协程支持。所以在HTTP解析层面不需要过于操心。但是针对数据库的并发和竞争是必须要考虑到的。尤其是数据库的设计。数据库的设计会直接影响效率。所以我向他们讲述了几个案例。比如视频的展示页面不仅要获取视频链接，同时需要获取点赞数量，评论数量等等。同时用户点击评论还需要显示评论内容，评论者名字和评论日期等等。简单的两次点击可能涉及到了多次数据库查询请求。如果表设计不好则会严重降低服务器性能。为此我们探讨了使用Redis做为mySQL的缓存层的可行性。其次，我们决定使用事务来保证数据的安全和鲁棒性。最后决定使用对象储存来储存视频和封面这样的非关系型数据。在开发过程中，我会负责测试其他成员完成的代码，并且安排下一阶段的内容。同时我经常去项目登记表上提供的链接查看其他的队伍进度，学习其他队伍使用的技术。比如在开发临近末尾的时候，很多队伍提前完成了项目准备好了slides，我会去查看他们的slides来看看是否有可以学习的地方。我们就从中新增了JWT鉴权来保证用户体验和snowflake算法进行ID生成。

这次的青训营中有很多实力很强的队伍。他们大多都是有很多实际开发经验的人。尽管如此，我们最后仍在所有队伍中排名前5%。并且获得了证书。我的两名组员也对我的能力表示了认可，我们到现在还在经常联系，会讨论一些技术相关的话题。

I have joined a training camp which was organized by Bytedance. Our mission is to complete a mini TikTok server. There are three people in our team. Since I finished my Linux web server earlier, I have some experience with the whole development process. So during the first meeting, I discussed the project's content in-depth. First, I discussed the framework. Although this project must be implemented using golang, and we are unfamiliar with that, I still did some research on this part. I propose we can use the GIN framework, which can parse HTTP requests easily. Then I explained to them that we should use the MVC structure for development. It makes the code easy to be maintained and scalable. Third, I tell them some problems and scenarios we must consider. The first is concurrency. Because golang supports coroutine, there is no need to worry too much when we are using the GIN framework to parse HTTP requests. But we must consider the race condition and thread safety when using the database. Also, we need to design the database carefully. The design of the database directly affects efficiency. So I told them some cases. For example, the video's display page needs to obtain the video link and the number of likes, comments, and so on. At the same time, when the user clicks on the comment button, the server also needs to send a SQL query to get the comment's time, name, and content. So we can see user just clicks twice, but it may involve multiple database queries. Poorly designed tables can severely reduce the server's performance. To this end, we discussed the feasibility of using Redis as a caching layer for mySQL. Second, we decided to use transactions to keep data safe and robust. Also, we decided to use object storage to store non-relational data like videos and covers. During the development process, I was responsible for testing the code written by other members and assigning the next stage's mission to team members. At the same time, I often check the other team's progress and try to find some new techniques used by other teams. For example, when the project is nearing the end, many teams have already completed their projects and posted their slides to the website. I checked their slides to see if there are anything new. By this, we added JWT authentication to ensure user experience and used the snowflake algorithm to generate user ID.
There are many strong attendees at this camp. Most of them have a lot of practical development experience. But my team still is top 5% of all teams, and I obtained a certificate. My team members also recognized my abilities.





## 反问

- Does Roblox have any plans to make triple-A games or just focus on a UGC platform?
- What do you think about meta's metaverse?  In what aspect do you think Roblox is doing better than or different from Meta?
- What are the engineering challenges that the company is facing?
- I know about 67% of users are under the age of 16.  Is it an advantage or disadvantage? Do you think attracting users older than 16 years old is a big challenge?
- Only about 15 percent of users are from Asia. How do you think the overseas market, especially in Chinese? I know Roblox is cooperating with Tencent. But China has an independent and strict regulatory system. Will that be a big obstacle to promoting in the Chinese market?
- What's your non-programming related hobby?
- I played some games on Roblox, and one game called Phantom Forces gave me a really deep impression. Roblox studio provides full functional SDK, and I can know its potential. But It seems like we don't have any anti-cheat method. I think this would be an important thing. Do we have any plan for adding an anti-cheat feature? Maybe providing some API, SDK, or allowing developers to ban some cheater's account?



It's a great honor for me to have this interview.  我很荣幸参加这次面试



实习

- 关于做一件事情中途放弃了的经历
  - WDL
  
- 过去的六个月当中，你学到的最significant的life lessons
  - never give up
  
- 谈论一个自己喜欢的项目
  - 均衡器


## 谈论一个很难的项目，但自己还是艰难的做完了 -- 嵌入式系统

我曾经上过一门嵌入式系统的课。期末项目是设计一个飞行避障系统。

这个项目对于我来说非常难。第一个原因是它是嵌入式系统。所以我们必须遵循嵌入式系统的设计原则。第二个原因是我们必须使用状态机模型去画出我们的整个项目流程。并且要使用公式来证明我们的代码是bug free的。第三个原因是我们同时需要提交论文级别的项目报告。这其实是非常难的。嵌入式系统的理论本身就非常难以理解，同时很多的逻辑运算条件也是经常让我感到非常困惑。在项目过程中，我一开始的第一个版本非常糟糕，因为包含了非常非常多的嵌套分支，导致根本无法使用状态机来表达出来。然后我比对着模型重新写了第二个版本的代码。这一次看起来好了很多。尤其是各个分支的条件不再模糊不清而是有顺序的。在提交之前我们必须在报告中附上代码测试的结果。我花了不少时间针对很多的edge case去进行测试然后继续修改我的代码。幸运的是我最后拿到了90分的成绩。扣掉了10分的原因是我的论文的结构有一点点的问题。

I had taken a class called advanced embedded systems. The final project of this course is to design a flight collision avoidance system. 
This is a really hard project, and I even don't know how to describe it. The first reason is it is an embedded system, so I have to follow the rules of an embedded system to design my project. The second reason is I have to draw my project to a state machine model and use some formula to prove that my code is bug-free. The third reason is I have to provide a paper-level project report. 
The theory of the embedded system itself is very difficult to understand. At the same time, those logical operations always make me confused. The first version of my code is not good enough because it has a lot of nested conditions, and I can't arrange it to the state machine model. So I revised and the second version is better. I rearranged the order and made the condition clear. And I did many tests to prove my project is robust under some edge or extreme cases. Finally, I got a 95% on this project. 



## 谈论一个小组完成的项目 * 2

- 推特

在校期间，我曾经有一个项目是关于推特的词汇热度分析并生成热度图。我们有六个人，分成了两个小组。我所在的小组是负责拉取推特数据并进行分割和过滤。由于我对这个项目非常感兴趣，而且也做过相似的一些小项目，所以我同时也关注着另一个小队的任务。他们主要负责计算热度并且生成热度图，也负责UI部分。

I did a course project which is analyze the frequency of words from some tweets. And it will generate a heatmap to display the result. We have six group members and are split into two groups. My mission is to pull the data from Twitter, split it into words, and do some data cleaning. Because I'm really interested in this project and have done some similar projects, I kept my eye on another team. Their mission is to calculate the heat, generate the head map and do some UI parts.



在进行数据处理的操作中，我提出可以新增一个额外的feature，就是保留原推特的语句，也就是维持语义。因为可能会有人想查看每一个词汇在不同地区的热度的同时，查看具体的推文或者语句。但是我的小队成员似乎并不感兴趣，于是我独立完成了这个模块的开发。

When I was doing the data processing, I proposed that we can add an additional function: keep the original twitter content and its link. Because there may be some people who want to check the popularity of each word in different regions, and also check specific tweets simultaneously. But my teammate doesn't get interested in it. So I developed this module individually

在另一小组进行milestone的时候，我也经常会旁听然后给予一些建议。因为我曾做过相似的可视化项目。在项目中期，我们小组的数据部分已经开发完毕，下一步就是交给他们继续做可视化部分。但是他们的进度不太乐观，因为他们没有之前的开发经验。所以我主动加入了另一个小队。协助他们进行热度图的生成并且进行UI的调整。最后我们是第一个完成任务的小队，并且在综合评分中得到了第一。

I always join another team's meeting and give them some advice because I have similar development experiences. Halfway through the project, I finished my part. And I didn't stop there. I found the other team was got some issues and got stuck. So I joined that team initiatively and tried to help them. I help them to use some libraries to generate the heat map and adjust some layout and UI. Finally, we were the first team to finish the project and get the highest score in the class. At the sametime, because my additional feature, Our professor gave me some extra credit and acknowledged my thought.







## 谈论一个自己从头到尾做的项目 * 2

- 24小时网站项目

曾经在软件工程课上，我们的期末考试非常有意思。因为内容是在24小时之内实现一个拥有文档中列出的全部功能的网站。This final exam has a name called something like 24hours challange. 因为教授想要模拟出一种快速或紧急部署的场景。

项目要求是使用bootstrap框架和给定api实现一个美国部分大学的信息预览页面。整体来说并不十分困难。但是有一个小的细节问题让我卡住了很久，就是这个网页如果其中某一行的grid的layout会由于文字数量过多导致拉长，会导致这一行的每一个grid都会更长，比较影响美观。最后的评分有一项是针对网页的美观度进行评分的。所以我花了大约四个小时思考这个问题如何解决。我本想制作成浮动卡片的样式，但是由于我不精通HTML和CSS，而且限定了必须使用bootstrap框架导致这个功能最后还是无法实现。做为compromise，我使用了一个read more按钮，如果文字过长则直接跳转至学校官网。也算是在某种程度上实现了在功能要求和美观要求上的折中。在我心目中这个项目也算是并不完美。因为没有达成我想要展示的目标。最后在项目报告里面我详细解释了这个问题。教授的回复是他原本没有想到这个问题，但是我是为数不多的主动去解决了这个问题的学生。所以我依旧拿到了满分。



This project is our final exam. Yes, it is the final exam, not the final project, because we have a separate final project. Our mission is to deploy a website and implement all functions listed in the documents in 24 hours. This final exam is called a 24-hour challenge because our professor wants to simulate a fast or emergency deployment scenario.
This exam requires using the bootstrap framework and some API to make a website will display some information about universities in the united states. It is not too hard at all. But because it is a website, the appearance of the website will be included in our grade. So I do a lot of work on it. And I do encounter some problems. One problem is if the length of the text is too long, it will stretch the grid. The overall layout of my website is a kind of grid, and it is a requirement because we must use the grid as the basic layout. So if the certain line's grid is stretched, it will look really ugly. The other line's length may be 5 centimeters, but the stretched line's length may be 8 - 10 centimeters. In the beginning, I tried to add a float-card animation to it, but I didn't have too much time, and I had to use the bootstrap framework so I couldn't implement this function. But as a compromise, I added a read more button. If the text is too long, I will omit some parts of it, and the user can click the button and then redirect to the school's official website. Finally, I explained this problem in detail in the exam report and described my solution. I get a 100% in this exam because not too many students are trying to solve this problem. And my solution is not bad. 





## 谈论一个自己简历上体现不出来的东西 * 2

- 坚韧

perseverance

我从3岁就开始学钢琴。在小学的时候每天放学都要回家坐在那里练习几个小时。小孩子很难坚持得住但是我家里人强迫我必须完成每天的任务。所以可能在那之后养成了一种习惯，就是坚韧。包括我几乎没有说因为什么原因而完全放弃过某件事，尤其是分配给我的任务我会想办法去完成。比如资料或者资源不够我会去自己查找或者问教授。写题也一样。每一道力扣的题我都有反复的练习过，并且都留有笔记和注释。尽管我到现在可能说，没有一个offer，但是我依旧没有放弃过努力。

I think it is perseverance. I have been learning piano since I was three years old. In elementary school, every day after school, I went home and practiced piano for several hours.
For a child, it is really hard to sit here and practice tedious scales for several hours. But my parents force me to do that. So I think I acquired the habit from it gradually. I rarely gave up something completely for any reason, especially the tasks assigned to me. I would find a way to complete it. For example, if there is not enough information or resources, I will find it by myself or ask the professor. 
Another example is when I practice my coding skills, such as solving leetcode questions. I didn't solve too many questions, such as some people already solved 500 or 1000 questions, but I didn't. But I practiced and pondered each question I solved several times. At the same time, I will write notes and comments on the question.



全职

## 从其他人身上学到的经验。怎么学的结果如何 * 5

- 讲述学习经历

首先我觉得“他人（others)”这个词的限定可以不局限于身边的同学或朋友。而且也可以不局限于直接和某人沟通。也可以不局限于某一个技术领域。这个经验(experience)也不局限于具体的rules或tips。也可以扩展为学习的过程。这个学习也可以不局限于某些技术。但是我打算主要着重在技术领域。

我的主要语言是c++。就语言本身而言，c++是一门非常复杂深奥的语言。它的学习曲线比较长，而且要不断的学习。

我经常和同学，朋友一起针对一些技术进行探讨。这些技术包括C++本身的一些原理的理解，一些新特性和应用。我经常会把一些不太明白或者不太理解的具体问题整理下来然后和朋友约一个时间进行详细的讨论。从语言特性来说比如如何理解萃取，智能指针使用的陷阱。从项目层面来说比如设计模式。从特性来讲比如协程。

同时我也会加入一些社群，比如discord 频道和论坛。然后针对一些问题和技术进行探讨。我也经常观看一些讲座，比如每年的cpp conference，从中可以学到很多的技巧，一些现有的不足，妥协和对未来技术的展望。我也会阅读书籍然后整理笔记和内容分享给身边共同学习的人，共同学习和探讨。

结果是我在社群中结交了很多朋友，有问题也可以随时向他们请教。同时我也丰富了我自己的知识，基础比较牢固。语言本身是一种工具，使用工具越熟练，我越能应对更复杂的实际需求和更严苛的质量要求。





My primary language is c++. For the language itself, C++ is a very complex and massive language. It contains a lot of things. In some books, people think C++ is not a single language. It is a combination of several languages. It depends on how you would use C++. So, people need to spend a lot of time and practice a lot when learning C++.
I often discuss some c++ topics with my classmates and friends. These techniques include some theories of C++,  some new features of C++, and some new usage. I often write down some questions I don't understand and discuss those things with my friends. For example, On the language level, I discussed how to understand traits and how to avoid traps when using smart pointers. For the project level, I discussed some design patterns. For the feature level, I discussed coroutines.

I also join some communities, such as discord channels. I often ask some questions or answer some questions at there. I also attend some lectures, such as the CPP conference. That is a really useful way to learn something new. I also read books, organize their contents into notes, share them with my friends and discuss them together.

As a result, I have made many friends in the community. At the same time, I enriched my knowledge and practiced my skills. Programming language is a tool, and the more skilled I use it, the more I can deal with the complex scenario.









## 遇到挑战怎么解决的 * 3

- 马赛克

在我大学的软件工程课上，我们被要求开发一个软件。最后我们的项目是一个在线的马赛克风格照片的生成器。你可以上传自己的照片池来使用你自定义的照片生成马赛克风格的图样。

第一个挑战是UI。由于这个软件是一个在线的，所以我们会有一个登陆系统。为了能让在线程序在外观层面上与众不同，我们需要在这方面花一些时间。在此之前我对HTML和CSS并没有过多深入的了解，所以我花了大约一周时间参考很多不同的网站设计出了六种不同的前端UI界面。并且把这些界面截图，以问卷的形式发放给了我们的同学和朋友，问他们哪一种更好。所以第二个挑战是功能问题。为了凸显我们这个项目的与众不同，我们为我们的程序新增了一个功能。用户看到生成的图片后，可以点击这个图片的每一个组成部分查看细节。也可以使用这个组成部分,也就是这张照片做为新的基础照片，然后生成新的马赛克风格的照片。所以第二个挑战并不在于如何生成马赛克风格的图片，因为这种算法比比皆是。关键在于如何在应用这部分算法的同时并不直接生成整合完毕的图像。简而言之就是保留每一个组成部分的原信息，并展示出来。一开始我们团队的成员打算使用python来实现这部分算法，但是发生了一些问题。当用户上传的image pool 过大或分辨率需求很高的时候，生成的延迟会很高，并且网页会变得卡顿。最后我协助队友使用C++重写了这部分算法。我们会先把每张图片的特征信息抽取出来，然后赋予一个一个的编码。处理过程中实际操作的是这些图片的编码，最后处理完毕后，再根据编码，统一对每一张图片进行实际处理。比如颜色调整。最后输出的是图片对应的连接。然后前端部分负责解析每一个链接这样可以实现一张大图片的每一个组成部分都是可点击的。第三个挑战是网页卡顿，我们对前端页面的技术不是很精通，我们一开始为每一个组成部分实现了动画效果，也就是鼠标悬浮在上面的时候会有一个卡片样式的动画。但是实际使用的时候在图片比较多的场景下效果并不好，而且卡顿严重，最后我们取消了这个动画。在最后我们的项目展示中，教授对我们的创意提出了额外的肯定，并且由于UI设计的比较美观，我们还获得了额外的加分。





I had finished a course team project which was to develop an application. My topic is to make an online mosaic art-style photo generator. Users can upload their own photos and get mosaic-style photos. Furthermore, user can upload their photo pool which means each component of the generated photo will be selected from the user's photo pool.
The first challange is UI. Since it is an online application, we will have a login/register system. To make our project different from others on the appearance level, I decide to design something new. Before this, I didn't know much about HTML and CSS, so I read a lot of tutorials, documents, and videos. Finally, I spent about a week on this and designed six different kinds of UI. I take some screenshots of the webpage and use them to make a questionnaire. Then send it to our classmates and friends, asking them which one is better. 

The second challenge is the function. Mosaic art-style photo generator is not a rare idea, so I have to do something special. I decide to add a unique function. After the user gets the generated photo, they can click each component of the big photo. So they can take a look at the details. Also, they can select one component and use this photo as a new base photo to generate a new mosaic-style photo. The mosaic generator algorithm is not too hard because there already have some resources we can use as a reference. But because of the new function, I have to rewrite the algorithm. So I use K-V storage to store our image. We extract the picture's eigenvalues. And encode this value with some other important values into a combined value. And the file name of the picture is the key. 

We are actually processing the value, not the image itself. And we didn't actually modify the picture during the calculation process. When all calculations are done, we will apply all changes to the picture at once and then return the link of those pictures as a list. After that, our webpage will parse each link and display each picture. So all component of the picture is clickable. But there are still some problems. That is the third challenge.

When the user uploads too many photos as a photo pool or the photo's resolution is too high, sometimes the webpage will crash. I think the reason is that we add an animation when the user clicks the component. It has a float-card animation. So I think that is the reason. So we decided to use three different ways to display the result depending on the number of those components. We still have the animation when the number of components is relatively small. When it is a little bit more, we will disable the animation. When the user chooses a really high resolution and causes the number of components to be greater than 1000, we will disable all clickable components. Users can only get a single picture for the result. 
Finally, my team got a great score because of our idea. Also, our professor gave my team extra credit because I did a great job on UI. 



## 展现领导力 * 2

- 字节

 我曾参加过一个字节跳过官方举办的青训营。目标是组队完成一个mini tiktok server。我们的队伍一共有三个人。由于在这之前我完成了我的linux webserver，所以对整个开发过程有一些了解。所以在第一次meeting的时候，我就针对项目内容进行了深入讨论。首先我讨论了有哪些框架可以使用。由于这个项目必须使用golang进行开发，我们对golang并不是很熟悉。但是我提前进行了调查，最后我选定了GIN框架。GIN框架可以比较轻松的进行HTTP解析。然后我和他们阐述了我们应该使用MVC结构来进行开发，模块化的开发使得代码容易维护而且易于新增功能。最后我向他们讲述了几个需要考虑的问题。首先是并发问题。由于golang语言本身有协程支持。所以在HTTP解析层面不需要过于操心。但是针对数据库的并发和竞争是必须要考虑到的。尤其是数据库的设计。数据库的设计会直接影响效率。所以我向他们讲述了几个案例。比如视频的展示页面不仅要获取视频链接，同时需要获取点赞数量，评论数量等等。同时用户点击评论还需要显示评论内容，评论者名字和评论日期等等。简单的两次点击可能涉及到了多次数据库查询请求。如果表设计不好则会严重降低服务器性能。为此我们探讨了使用Redis做为mySQL的缓存层的可行性。其次，我们决定使用事务来保证数据的安全和鲁棒性。最后决定使用对象储存来储存视频和封面这样的非关系型数据。在开发过程中，我会负责测试其他成员完成的代码，并且安排下一阶段的内容。同时我经常去项目登记表上提供的链接查看其他的队伍进度，学习其他队伍使用的技术。比如在开发临近末尾的时候，很多队伍提前完成了项目准备好了slides，我会去查看他们的slides来看看是否有可以学习的地方。我们就从中新增了JWT鉴权来保证用户体验和snowflake算法进行ID生成。

这次的青训营中有很多实力很强的队伍。他们大多都是有很多实际开发经验的人。尽管如此，我们最后仍在所有队伍中排名前5%。并且获得了证书。我的两名组员也对我的能力表示了认可，我们到现在还在经常联系，会讨论一些技术相关的话题。

I have joined a training camp which was organized by Bytedance. Our mission is to complete a mini TikTok server. There are three people in our team. Since I finished my Linux web server earlier, I have some experience with the whole development process. So during the first meeting, I discussed the project's content in-depth. First, I discussed the framework. Although this project must be implemented using golang, and we are unfamiliar with that, I still did some research on this part. I propose we can use the GIN framework, which can parse HTTP requests easily. Then I explained to them that we should use the MVC structure for development. It makes the code easy to be maintained and scalable. Third, I tell them some problems and scenarios we must consider. The first is concurrency. Because golang supports coroutine, there is no need to worry too much when we are using the GIN framework to parse HTTP requests. But we must consider the race condition and thread safety when using the database. Also, we need to design the database carefully. The design of the database directly affects efficiency. So I told them some cases. For example, the video's display page needs to obtain the video link and the number of likes, comments, and so on. At the same time, when the user clicks on the comment button, the server also needs to send a SQL query to get the comment's time, name, and content. So we can see user just clicks twice, but it may involve multiple database queries. Poorly designed tables can severely reduce the server's performance. To this end, we discussed the feasibility of using Redis as a caching layer for mySQL. Second, we decided to use transactions to keep data safe and robust. Also, we decided to use object storage to store non-relational data like videos and covers. During the development process, I was responsible for testing the code written by other members and assigning the next stage's mission to team members. At the same time, I often check the other team's progress and try to find some new techniques used by other teams. For example, when the project is nearing the end, many teams have already completed their projects and posted their slides to the website. I checked their slides to see if there are anything new. By this, we added JWT authentication to ensure user experience and used the snowflake algorithm to generate user ID.
There are many strong attendees at this camp. Most of them have a lot of practical development experience. But my team still is top 5% of all teams, and I obtained a certificate. My team members also recognized my abilities.

Entity relationship diagram





## 有技术难题的项目 *4 -- 说过了

- 服务器

我曾经自己开发过一个linux web server。 服务器支持文件的传输，比如预览图片和视频，也支持用户的注册登录。首先我认为有技术难度的原因是在我写这个项目的时候，我此前对如何开发服务器和网络编程并不是很熟悉。也就是属于一个一边学习一遍做的项目。而且它涵盖了非常多的内容。包括socket programming，multi threading，operating system和比较深层的c++知识。 

第二点是因为我在项目中没有使用任何的第三方框架或library。仅使用了标准模板库中的内容。实现的功能包括线程池，HTTP解析，超时链接检测和异步日志系统都是我自己写的。同时使用了IO多路复用。仅使用了标准模板库中的内容。

第一个难点是HTTP解析的部分。我使用了有限状态机来实现这一部分。因为这里必须要小心计算每一个部分的长度然后进行分割，再分段解析。

第二个难点是多路复用。在项目刚开始的时候，我花了不少时间来理解socket和epoll的概念，同时学习中也顺带看了一些epoll的源码。由此对其有了一些深入理解。

第三个难点是线程安全。尤其是在使用多线程模型的时候，我花费了比较长的时间去调整mutex的粒度。因为粒度过大会影响服务器的性能。最后我采用了生产者消费者模型和阻塞队列来实现这一部分。

第四个难点是数据库的使用。为了防止每次进行query都要反复建立链接的额外开销，我使用了数据库连接池。同时为了防止SQL注入我也进行了额外的处理。

第五个难点是异步日志。我同时实现了同步日志和异步日志系统。异步日志也采用了任务队列的方法。但是令我非常奇怪的是在我进行压力测试的时候我发现异步日志的性能并没有同步日志好，我目前没有找到具体的原因。

其他的部分例如线程池中线程数量的选择也是花了时间去尝试。针对内存泄漏，我使用了valgrind来进行检查。最后我的服务器也满足了C10K的要求。

I think the most difficult project is my Linux web server. This web server can support viewing videos and pictures, user login, and registration. Also, my web server fulfills the C10K requirement. The reason why I think this project is technically challenging is I was not really know how to implement a server at that time. So I was implementing the server and learning how to implement it simultaneously. Also, the Linux webserver covers a lot of knowledge. It includes socket programming, multithreading, operating system, and more in-depth c++ knowledge. The second reason is I didn't use any 3rd part library or framework in this project except the standard template library. I implemented functions including thread pool, HTTP parsing, timeout link detection, and an asynchronous logging system. All of those are developed by myself. I also used IO multiplexing to improve the server's performance.

The first obstacle is understanding the socket programming and IO multiplexing. It is hard to understand those things for me at that time. So I spend a lot of time on it. At the same time, I also read some source code of epoll. It really helps me to understand the theory of it.

The second difficulty is HTTP parsing. I used a finite-state machine for this part. And I have to calculate the length of each part carefully, divide it into different parts, and invoke different functions to parse it.

The third is thread safety. Especially when using a multi-thread model, I spent a lot of time adjusting the granularity of mutex. Because if the mutex granularity is too coarse, it will affect the server's performance. In the end I used the producer-consumer model and blocking queue to implement this part.

The fourth difficulty is the use of the database. I implemented a connection pool to prevent additional overhead when repeatedly establishing a connection to MySQL. At the same time to prevent SQL injection, I also added additional processing. Such as Regular Expression matching.

The fifth difficulty is the logging system. I implemented both synchronous and asynchronous logging system. I also used a blocking queue to implement asynchronous logging system. But one thing that makes me feel strange is that when I did the stress test, I found that the performance when using the asynchronous logging system is not as good as that when using the synchronous logging system, and I have not found a specific reason.

For the rest of the part, such as thread pool and memory leak detections, I also spend some time on it. Finally, my server can fulfill the C10K requirement, and I also learned a lot of things from this project.



## 自己有激情投身于中的项目 *2

- 均衡器

我最有激情的项目是我做的基于JUCE框架的多段均衡器。我非常喜欢音乐，我从3岁开始学习钢琴，然后中间学习了很多理论知识，比如和声学，曲式学等等。在进入高中之前，我其实非常想要进入艺术院校继续学习音乐，最后考入音乐大学。但是我的父母并不同意这一点，因为音乐这条路，前路不太明朗。尤其是在亚洲文化里，这样的路就是不应该选择的。最后我还是妥协了并没有去读音乐学院。选择了计算机。但是在我的大学生涯中，我经常自己作曲，也参与了不少音乐社团，也参与过几次演出。尽管现在我的空闲时间非常的少，我也会挤出时间来练习我的钢琴或制作一些小的demo。所以我在暑假的时候想我是不是也可以把计算机和音乐结合起来做一点事情呢？我选择了做一个VST插件。以我目前的能力，制作出一个非常精美的VST 乐器不太现实。均衡器是音乐制作中必备的东西。而且实现起来理论不是很复杂。所以我决定做一个均衡器。我使用了JUCE框架，这个框架对于音频的支持非常棒。同时网上也会有一些资料。因为这是一个纯粹的兴趣项目，我没有截止日期或者需求的压力，完全是我想怎么做就怎么做。我为这个插件提供了更换背景图片的功能，也提供了调整UI的功能，比如旋钮的大小，背景颜色或边框颜色等等。其中我花了大约3天时间只为了增添一个功能，就是毛玻璃效果。我想为我的插件的旋钮部分的背景图片增添毛玻璃效果，这样的UI看起来会更加高级。但是我花了很长时间都没有找到合适的解决方案，因为JUCE框架没有直接提供毛玻璃效果的接口。最后我不得不采用另一个方案，也就是单独渲染按钮的部分。裁切出来按钮对应的图片然后单独渲染成毛玻璃效果后导入框架，这样一来背景图片其实和旋钮图片是两个图片了，这也造成了一个问题，用户选择的自定义图片不会更改旋钮图片。这个问题还没有得到妥善的解决。所以我不得不妥协，放弃毛玻璃效果采用调整透明度的方式。其次，我花了大约两天时间来让我的窗口是可缩放的。因为随着窗口比例的变化，UI的位置也需要调整。项目结束后我把这个插件上传到了一个音乐爱好者社群，并且发给了我的朋友们让他们体验。有一个非常有意思的事情是一开始导出的时候我忘记切换到静态链接了，导致他们在他们的设备里无法运行这个插件。最后我又重新打包了一份。他们的反馈还是很不错的，但是仍旧有一些极端情况下的UI的逻辑问题。比如如果图片的比例比较特殊会导致一些UI方面的问题。由于C++写UI是非常痛苦的事情，所以这一部分我在空闲的时间里还会继续去寻找解决方案。





My most passionate project is a multiband equalizer based on the JUCE framework. I started to learn piano when I was three years old. And I also learned a lot of theoretical knowledge, such as harmonics, Orchestration, etc. Before I got into high school, I told my parents I wanted to attend an art school to continue studying music. But they refused it because this way has a high risk. So I have to agree with them. But I never give up learning music. When I'm in college, I always make some music, join some music clubs, and also participated in some performances. Even though I don't have too much spare time right now, I still always practice piano and make some demos. During this summer vacation, I thought I could do something related to both music and computer science. So I decide to make an equalizer because equalizer is a necessary tool and not really hard to make. I use the JUCE framework because this framework has great audio support. Also, because this is a hobby project, I don't have any pressure from deadlines or clients. I can do anything I want. I feel really excited at each progress during this project because I'm doing something I love. My plug-in provides a special function is the user can customize the background image and change the UI, such as the color of the knob. I spend about three whole days just to add one feature. It is the aero effect. I want the knob and oscilloscope 发音（a silly scope) part can have this kind of visual effect, just like windows vista. But I didn't find a way to solve it properly because the JUCE framework doesn't provide this function as an API. So I have to use another way to approach it. I clipped a certain part of the image, and apply the effect individually and then put the image back into the framework. So I can let the different images be rendered separately. But it still has the problem that when users try to change the background image, they have to import the image of the knob simultaneously. That might be annoying. So I have to discard this effect and use the translucent effect. I also spend about three days on letting my window zoomable. Because I need to change the UI dynamically when the scale of the window changes. After I finished my project, I send this VST plug-in to my friends and some music community. One really interesting thing is that I forgot to change the export settings to the static library, which is a little bit awkward. But finally, I repackaged the plug-in, and I got really positive feedback from those people, and I feel really happy. I'm still working on this project when I have some free time because I need to revise some minor issues, like when the background image has a special Aspect ratio, it will cause some strange UI problems.



## 面临风险怎么做的 -- 说过了

- 云计算

我们曾经合作部署过一个分布式系统的数据储存服务。主要功能是用户可以上传下载储存在云端的文件。这是一个course  project。但是在学期结束的时候，我们的期末考试就是把我们的项目展示给来参加这个展示的人。我们教授真的请来了六七个不同公司的人，其他课程的教授和一些路人来对每一个组的项目进行评估。最开始我们没有考虑特别多，因为资源受限所以我们只有四个云服务器。然后部署的时候采用的是手动部署。开发都比较顺利。但是在临进行评估的前两周的时候我突然意识到，我们相对于course project，更多的是一种产品。我们的产品肯定不能只有四台服务器，一旦数据量很大或者用户很多的时候这是根本不可能承受得住的。但是我们可以手动部署四台服务器，但是手动部署四十台，四百台是不可能的。所以我紧急和团队成员开会，讨论如何解决这个问题。我的方案是使用ansible进行自动化部署，然后编写playbooks来对节点进行注册。因为项目采用的是kafka。所以需要向zookeeper进行节点注册。但是风险在于这是一个工程量比较大的任务，很有可能无法完成。我没有自动化部署的丰富经验，必须相当于从空白开始。而且自动化部署可能会导致很多奇怪的难以排查的错误，会十分耗费时间。最坏的情况就是我们在项目结束之前无法使用自动化部署，必须使用手动部署。但是我最后依旧决定开始使用ansible进行自动化部署。然后编写对应的脚本。最后我大约花费了两周时间对服务器进行了ansible的部署，playbook的编写并且对服务器进行了测试。自动化部署非常成功。尽管我们只有四个server instance能够让我们进行测试，但是用于服务的服务器的部署方案都是相通的。四台和四十台区别不大，所以我们认为是非常成功的。同时我们在报告中提出了自动化部署方案，教授和评审对这个功能表示非常满意。因为非常贴合用户需求。



I had deployed a cloud storage platform. It allow user to upload or download their files. This is a course project but it is special one. Becasue at the end of semester, professor will invite some other professors and some engineers from different company to our presentation and rate our project. At the beginning, we didn't consider too much such as scale up. Because we only has four cloud servers. So we deploy all machines manually. During the development progress, everyting is going well. But when only two weeks before the presentation date, I suddenly realize that I have to treat this project as a real product and we need to treat those guests as customer. So our product certainly can't only has four servers, we have to support dynamic scale-up. But it is impossible to deploy those machines manually, we have to find out a way to do those things automatically. So I held a meeting and try to find a solution for this. I purpose that we can use some tools like ansible to do this thing. We can write come configure files, in ansible it called playbooks. The risk is i don't has too much experience on automation deployment. So I might missed the deadline if the progress is not going well. But we don't have any better solutions. So I decided to take this mission. I did a lot of researchs. It is a quite complex and tedious progress. Because we use chamelion cloud and restart the server will take five to ten minutes. We also use kafka in our project so we need to write commands to let machine to the registuration to zookeeper automatically.  Finally, I took about 10 days to do this thing. And we didn't find any bugs there. Although we have only four machines but I think it is pritty similar with deploy 400 machines by using this method. At the end we add this feature to our project discription and both professor and guests are satisfy with our solutions because it is fulfill some industral requirements.







## 主动去做一些有影响力的事 * 3

- 个人博客


我个人主动做的有影响力的事情并不是一个项目本身，应该算是一个我学习过程的附属品。我这学期正在上一门课叫做open source software in medical image processing. 我们的期末项目是要使用ITK/VTK框架去实现一个自己的针对于医学图像处理的软件。在这个领域绝大部分软件和框架都是使用C++写的，ITK和VTK也不例外。然而，我的同学几乎都没有使用C++的经验。因为他们有很多人主要使用python或matlab进行图像处理。而且他们当中的大部分人本科并不是计算机专业的。所以这是一个大问题。这门课是研究生级别的课程，属于special topics。所以教授肯定没办法像入门课那样去教学生如何使用C++。所以他们想完成这样一个project是非常困难的。这个困难主要有三个方面。

第一个方面是基础部分。就是一些c++的基本知识，语法和规范。比如指针，引用等等。这一部分并不是很困难。

第二个方面是C++的标准模板库的使用。他们没有C++的使用经验，肯定不知道vector是什么，尖括号里面的是什么东西。什么是智能指针。如何使用自定义比较器。什么是迭代器。为什么对map使用下标访问运算符会添加一个键值对。也就是说如果他们不了解这一层面的知识，他们难以去实现特定的功能。同时难以理解代码。这部分是非常重要的。更关键的是普通的文档或教程会假定读者有一定的前置知识。但是他们其实没有，所以他们在读一些教程的时候可能还需要查找包括在这个教程里的知识。这样一来会有一个非常长的study chain。非常浪费时间而且意义并不大。

第三个方面最重要的是我们要使用ITK或VTK框架。使用框架就必须要读文档。如果上一个部分他们不理解的话，他们根本没有办法理解文档和一些给定的函数如何去使用。如何获取想要的结果等等。

学习这些东西需要非常长的时间和积累。同时要查阅很多资料。显然如果让他们从头去学习是不显示的。而我的主要语言是C++，我对这些事情足够了解。并且我在学习过程中记录了非常多的笔记，也整理了非常多的tips和一些标准模板库的使用方法和底层原理。我就想能不能让这些东西派上用场。

当然了，他们不需要理解很多很深入的部分，但是有一些浅层的原理还是需要了解，不然使用起来可能不会很方便。我的个人笔记已经在我的个人博客上了，但是是中文写的。于是我把我整理过的笔记再次使用英文整理了一遍，主要包括了标准模板库的使用技巧，方法 和一些常用的语法。尤其是使用模板编程的时候更要注意语法。我找到教授和她探讨了关于学生没有c++基础的问题。她表示也很头疼，因为每次office hour人都很多，而且很多学生问的问题是比较相似的。于是我和她提出了我的想法，我和她说我整理了我过去的笔记，也许可以放到课程网站上，让学生们先去我的笔记里查找相关的部分，如果没有包含在内可以再问你，同时我也可以为同学解答一部分C++相关的知识。但是对于ITK/VTK框架，由于我也是beginner，所以我也没办法在这方面给出很多的回答。但是对于C++本身而言我会尽我所能去回答问题。教授表示非常惊讶而且非常高兴。因为我能够帮助她分担压力。我自己也觉得非常的开心。因为我真的以我的个人努力为我身边的人提供了帮助。我觉得还是算很有影响力的。因为我能为教授分担压力，我能帮助同学解决他们遇到的问题，能加快他们的项目进度。而且，在他们提问的时候我也可以增加我的经验，因为有很多问题我也没有遇到过，我也可以从中学习到很多。





For this experience, it is not an actual project. It is an appendage of my learning path. I'm taking a course called open source software in medical image processing. Our final project is to use ITK or VTK framework to implement our own medical image processing application. Most applications and frameworks in this field are developed using C++. So I need to use C++ to finish my project. But the problem is here. Most of my classmates have no experience with C++. And most of them are not majoring in computer science in college. Also, they often use python or Matlab to do some image processing. This course is a graduate-level course, so of course, the professor can't teach us C++ step by step just like those intro-level classes. So letting them use C++ to develop software is a really big challenge. 

The challenge comes from three-part. The first part is basic knowledge of C++. It includes some basic grammar, rules, and knowledge such as pointers and references, how to compile it and what CMake is. What is a heap, and What is operator new? This is not the biggest challenge because learning this part won't take too long.

The second part is the biggest challenge. It is the usage of the standard template library. They don't have any experience using c++, so they don't know how to use it properly or even don't know it exists. For example, the container. Some students who only use python can not understand what is vector and what kind of thing should be typed in the angle bracket after the vector. And they don't know what the iterator is. For something more advanced, what is a smart pointer? What are function pointers, and how to use call-back functions? Something more may be multi-threading. There are tons of things they need to know.

At the same time, if they want to find something on the internet, that will be a disaster. Because most of those blogs, and tutorials need their audience has some prerequisites. Unfortunately, they don't have it. So they have to search for those prerequisites, so and so on. They will waste a lot of time on it. 

The third part is to read the code. We must use ITK/VTK skeletons. So if they don't have the knowledge I mentioned before, that is really hard. 

So studying those things need a lot of C++ knowledge and practice. Obviously, letting them study c++ from the beginning is impossible. 

But my primary language is C++; I have some experience with it. Also, I wrote many notes and summarized many tips from books while studying C++. So I decide to use those materials to help my classmates. I rearrange my notes. I discard some complex theories and add more tips, rules, cases, and examples. And rearrange the order of the content. Then I discussed this thing with my professor. During the discussion, I found that my professor is also annoyed with this problem. There are always many students in office hours, and some questions are similar. So I told her I arranged my note into a pdf, and maybe we could post it on the course website. Then students can check the pdf first, and if that doesn't cover their question, they can come to the office hour. At the same time, I say I can help her to answer those C++ questions. But I might can't answer some questions related to ITK/VTK because I'm also a beginner with this framework. She is really surprised and happy. And she posts the pdf to our slack channel. And my classmates also feel really happy because they really need a guide to help them finish their projects. I was also happy because I did something based on my work and helped my professor and classmates a lot. 



- 最难的课程
  - 操作系统
- 和cs无关的爱好
  - 音乐

