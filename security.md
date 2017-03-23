## 第一阶段：在客厅工作（或工作和休息在一起）

### 共享管理员密码

* 任何产品至少都会有一个用户：管理员。当你的小型初创企业有大约4人时，你至少可以把缺省的管理员密码换成一个复杂的然后分享给密码管理器并负责共享给别人。

* 共享的目的，是避免出现当只有一个员工有对系统的权限，而其他员工需要的情况。

* 理想的情况是每个人在每个服务上有自己的账号。一个折中的方法是创建一个'admin'(特殊情况下使用)，一个'developer'(作为日常工作用)，一个'service'(给程序使用)。这样做的意义是当你的一位开发者(developer)离开的时候你不需要替换你的服务(service)密码。

* 解释给你的员工听，他们需要最后记住两个密码：笔记本的密码和密码管理器的密码。

* 解释给你的员工听，不要使用他们的家庭或个人密码。否则密码很容易被公开或者已经公开。参见 [https://haveibeenpwned.com](https://haveibeenpwned.com)

* 解释如何选择密码管理器的密码。这里有一个[简短的视频(作者Sophos)](https://nakedsecurity.sophos.com/2014/10/01/how-to-pick-a-proper-password)可以帮你解释。
![如果选择合适的密码](/images/image_0.png)

### 钓鱼邮件，色情和bt是伪装的魔鬼

* 员工很可能同时用他们的工作笔记本在家作为个人电脑使用。这很正常。但是，从第一天起，解释给你的员工，不要用于bt下载，或者色情或其他有问题的网站。请他们买一个二手笔记本用于那些目的。

* 如果你被黑了，很可能是从一位员工点击一封钓鱼邮件开始的。作为你的初创企业有趣活动之一： [钓鱼测试](https://www.google.com/search?q=Phishing+Quiz).

* 停止使用邮件附件。习惯于打开邮件附件的员工总会不小心安装恶意软件。可以用Google Drive来分享文档，或者你在一个受监管的环境可以[付费使用Box](https://www.box.com/security/it-admin-controls)。

* 其他内部交流使用Slack。电子邮件是用来联系客户和供应商。

* 用密码管理器来分享密码，证书和秘密的笔记。

* 停止使用U盘：明确禁止使用这些恶心的设备。他们是[黑客控制你系统最快的方法](https://www.youtube.com/watch?v=CvI_mrQYaF8)。教会你们员工把他们识别为最主要的威胁！

* 更多的背景信息请参考[DBIR报告](https://www.google.com/search?q=DBIR%2520Report).

### 今天开始加密，只需一个单击

如果你的笔记本丢掉或者被偷，你不会想要你的数据一同泄漏。

* Mac用户可以单击加密磁盘。
* Windows用户需要Pro版本并硬件支持TPM。
* Linux用户可能需要重新格式化。

关于选择笔记本的注意事项。如果将来，您需要根据合规性要求（例如MDM）集中控制所有笔记本电脑，需要知道大多数供应商并不支持Linux。他们支持Mac, Windows Pro, Android, iPhone。Linux通常部分支持或者不支持。

没有越狱的iPhone比起Android来要难破解许多。他们缺省还有屏幕锁和启用加密。确保你的经理和系统管理员有开启屏幕锁和启用加密。

### 修复已知的漏洞

绝大多数操作系统（在你笔记本上或着云端）都有一个自动安全升级的选项。通常他只需一行配置，但可以10倍减少可被攻击的范围。

### 买至少2到3个域名

你至少需要一个域名给你的网站，一个给你的API，一个内部使用。

* 第一个域名通常是公司的正式名字或者品牌。他作为对外营销（网站）和员工电子邮件。两者通常由第三方服务提供商管理。用SPF和DKIM保护这个邮件域名。这其实没有那么困难并可以减少黑客攻击你的经理或管理员的钓鱼尝试。许多安全事故食欲员工打开钓鱼邮件，因此这很重要。
* 第二个域名是SaaS服务本身需要的，例如rest api。参见www.google.com之于www.gmail.com之于maps.googleapis.com。这个域名需要额外关照，和公司域名不同，他很可能需要架设在AWS Route 53上，并由他们的服务工程师团队管理。

* 第三个域名用来作为内部和后台办公室系统使用。这个域名需要明显于其他两个不同，并且容易写。有些公司使用公司域名的二级域名。但是，这也意味着它不能由后台办公室系统开发者管理，而他们需要为小型内部服务频繁更新。二级域名还会让人混淆 - 到底哪个是内部使用，哪个是外部可见。还有一个附带的好处是如果你匿名注册这个域名。大多数情况余名解析服务也是内部的（私有Route 53域名）。

* [大批量邮件发送](http://resources.mailgun.com/email-reputation.html)服务应该针对目标市场，交际性质邮件，公司邮件分别维护域名或者二级域名。这可以隔绝每种邮件类型的名声并保证时间敏感的交易性质和公司邮件不会延迟或标记为垃圾邮件。当你使用独立的营销用邮件域名时，确保他不是[雪靴垃圾邮件](https://www.spamhaus.org/faq/section/Glossary#233)并保证使用web转发到你的公司或服务网站，好让你的客户找到你。

### 在所有地方使用SSL/TLS/HTTPS！

在任何可以的地方使用SSL。在你的网站，API，后台办公室系统，如果不是太麻烦，甚至内部服务之间也应该使用。

可以通过AWS ACM, 或Let's Encrypt ACME更简单的完成这件事情。

监控你的访问节点的公开证书的过期日期，避免其过期。

牢记SSL加密网络流量，但不做认证。也不是两步认证(2FA)的替代品。


### 选择SaaS供应商

* 一旦选择基础架构供应商，就很难再切换了。未来，你可能需要减少供应商对你的组织的数据的访问。因此，在选择云端基础架构供应商时，尽量选择大的供应商（Amazon, Google, Microsoft），或至少拥有SOC2 Type2证书的供应商（针对基础架构供应商而言），拥有PCI的支付供应商，或其他有相关领域资质的供应商。

* 这并不意味他们的服务就是好的。而是接下来你不需要替换他们尽管他们的服务是好的。

* 缺省AWS用户选择俄勒冈（us-west-2）。如果你知道你的目标市场在哪里，你应该让你的数据中心靠近你的目标市场。

* 数据中心所在国家（数据驻留）也存在监管影响。对于欧洲客户来说，这可能是一个决定性的因素，并且迁移到其他地区可能成本过高。

### API管理

如果你们公司公开API（软件即服务），确保每一个客户都有他们自己的访问证书，否则你的服务可能会因为其中一个客户的测试脚本中有bug而下线。

* 考虑使用一个API管理解决方案，而不是把自己搞进去。他们提供browser2server， mobile2server和server2server登陆令牌支持，包括吊销令牌和与标准协议整合。

### 使用Git

在变更管理方面，使用git和pull-request是事实上的标准做法。部分合规性要求，你需要显示你的初创企业有适当的变更管理控制和测试。最好现在就开始。

使用git可以让你通过给予和取消提交权限，来在一段时间内增加外包/自由开发者。

## 第二阶段：签下你的第一个用户 / A轮

### 稍微带一点偏执

* 对你使用的所有服务启用两步验证。这对你的开发团队尤其重要，因为如果这些服务被入侵，你的产品也将会下线。如Google accounts，Dropbox，Github，Microsoft等。所有都要！

* 目标定位企业用户或在监管环境中工作的初创企业，通常在第一天就启用两步验证。

* 这里有一个完整并容易使用的两步验证实现：[TOTP 2FA implementation](https://en.wikipedia.org/wiki/Time-based_One-time_Password_Algorithm)。员工可以安装[Google Authenticator](https://en.wikipedia.org/wiki/Google_Authenticator) 在他们的手机上，他将生成一次性6位数字随密码输入。

* 一个更容易使用的方式是通过推送。很多SaaS供应商提供一个app，它会收到一个推送而不是生成密码。这比每次登陆复制一个6位数字要方便很多。缺点是，你可能需要不同的app对应不同的服务，而且没有网络不行，或者推送提供商下线时也不工作。

* 手机端两步验证的问题始于一个员工丢失／遗忘／替换他们的手机，或电池没电，然后他们就登入不了系统。有些员工不喜欢强化他们的手机（加密，锁屏以保护两步验证app），并感觉公司需要为两步验证的app买一台手机给他们。这也是为什么一些组织用yubikey（一个小型的usb设备可以识别用户指压）。类似于手机推送，yubikey防止恶意软件和黑客窃取你的键入信息。缺点是，与他们的手机不同，yubikey更可能与笔记本一起丢失。所以如果一个偷来的笔记本落入专家手中，专家可以从笔记本中得到密码然后还可以用yubikey登陆任意服务。另一个问题是，yubikey是一个USB设备，那你需要能将U盘（不允许）和yubikey（允许）区别开。 

* 用短信作为第二步验证是不建议的，应该被禁用。一个有经验的黑客可以说服你的手机网络客户[从你的线挪到他的](http://www.forbes.com/sites/laurashin/2016/12/20/hackers-have-stolen-millions-of-dollars-in-bitcoin-using-only-phone-numbers/)。并且最近有爆料说有8亿android设备上有[恶意软件读取短信](http://thehackernews.com/2016/11/hacking-android-smartphone.html)。

* 用语音电话作为第二步验证也应该被禁用。黑客会轻易在你手机不在线时，通过猜测你可能从来不改的4位数字密码尝试登入并进入你的语音信箱。

* 如果一个员工要求远程重置他的密码，如果可以请他亲自到公司来。如果条件不允许（或者时间紧张），验证他们的个人信息：不要相信你自己可以识别员工的声音。永远不要给邮件密码。

### 内部人员从组织窃取信息

* 准备一个勾选表单，给离职／解雇的员工用。列出所有需要取消授权/挂起的服务（还有Whatsapp组。我们在的时候，不通过WhatsApp发送门密码）。

* 检查Google Docs日志看是否有解雇员工下载敏感信息。

* 多数终端安全产品可以被配置成阻止用配备（如USB，蓝牙，手机）拷贝数据出笔记本。

* 如果结果的员工曾有管理员密码，推荐更换敏感系统的密码。

* 当雇佣一个新员工时，向他们的前同事打听他们的人品问题，并询问他们离职的原因。请注意至少在以色列要求员工提供犯罪记录是违法的。

### VPN
* 寻找可以安装办公VPN的集成应商相对容易一些（不要自己安装）。

* 将VPN部署在办公室，以及给办公室的网络使用静态IP地址，可以让你对服务器的管理访问进行限制。例如，你可以将它设置成只允许从办公室访问，或从家中连接办公室的VPN，而不用对整个互联网公开22端口（SSH）。

* 基于云的VPN（例如安装在ec2上）还具有几个优点。首先，办公室和云之间的所有通信都是加密的（尤其是当你访问数据存储，如不带SSL的elastic search时）。对于远程工作人员来说，网络性能也要好得多。此外，它在一定程度上能够减少对物理安全性的需要，因为那里并没有网络设备（办公室仅仅是某个咖啡店而已）。而它的缺点是，每当你断开办公室网络连接，你需要重新连接到VPN。

* VPN连接也应当启用两步验证。

### 防病毒软件/防火墙

* 安装端点安全产品是很简单的。请确保产品支持所有笔记本电脑的操作系统。配置自动更新，发送邮件提醒（可能有点吵），阻止所有传入连接。最后一点对于在本地运行服务器的开发这很重要。

* 在员工就位之前安装防病毒软件更好，因为安装防病毒软件这件事会让很多开发者不高兴。

* 大多数产品都有导入／导出功能，这使得他们较容易安装。

* 还有一些在防病毒软件之上的额外保护的产品叫做EDR（Cyberreason，BlackCobalt）但他们通常很贵。

### 用合适的散列（哈希）函数转化你用户的密码

如果你支付得起，使用一个[第三方登陆验证服务](#customer-users-management)来保存密码，管理密码，恢复密码，两步验证甚至更多。一些供应商提供按月活跃用户收费的策略可以满足你的预算。

然而，如果你决定开发你自己的登陆验证服务，遵从[OWASP登陆验证指南](https://www.owasp.org/index.php/Authentication_Cheat_Sheet)。

* 如果你的数据库遭到入侵并被公开，更差的事是你的用户密码也包含在内并且可以轻易破解 - 人们喜欢用同样的密码。[这是真的](http://mashable.com/2017/02/28/passwords-reuse-study-keeper-security)。因此，永远都使用*专为密码存储而设计*的散列函数来保存用户密码： bcrypt，PBKDF2或带一个参数的scrypt，[其需要花1秒钟运算](http://security.stackexchange.com/a/3993/69959)。不要使用MD5，SHA1或其他*不是专为密码而设计*的哈希方法。这种方式存储的密码通常只需要几秒就能破解。


### 物理安全

* 将笔记本配置成你离开座位后（最多）5分钟就休眠，并需要一个密码才能再次打开。要求你的员工在离开座位时手动锁住他们的笔记本，比如用[hot corners在Mac上](https://support.apple.com/kb/PH18796)，或者在Windows上用win + L。

* 不要让陌生人够得到电脑（尤其如果电脑有USB口）。物理访问是获取系统，产品和客户的最快方式。

* 提醒员工在离开时锁好门窗，并启动警报器。

* 在工作时间，给前门添加一个密码，以防止办公室盗窃。要求员工走向没有其他员工陪同的陌生人。

* 锁好你的服务器房间（或者你的网络设备的房间）

### 防止云服务器受到威胁

* 查看云防火墙配置，以确保没有尴尬的错误。

* 建立一个名为[security@mycompany.com](mailto:security@mycompany.com)的邮件组并在你的网站加一页用来报告安全问题到这个邮箱。安全专家可能倾向发送加密邮件，那么你可以[生成一个OpenPGP键值对](https://gpgtools.org/)，在网站上公开你的公钥然后保存私钥到你的密码管理器里。 
* 为了收到严重的已知隐患的通知，所有人都知道（除了你）建立一个Zapier账户，并通过几下点击订阅关于隐患的RSS feed到Pagerduty。这是一个RSS feed样例和一个Zapier过滤器配置样例

* [https://nvd.nist.gov/download/nvd-rss.xml](https://nvd.nist.gov/download/nvd-rss.xml)
![security rss filter](/images/image_1.png)

* 在晚期分离产品环境和生产环境是很困难的。在AWS里，安全属性是在一个账户范围内管理的，所以开发用VPC应该在同一个组织的另一个账户里建立。通常有三个账户。一个用于合并计费，一个用于生产，另一个用于其他（开发和后台办公室系统，其中后台办公室系统通过网络ACL配置为仅与您的办公室通信）。

* 最近Amazon宣布了[AWS Organisations](https://aws.amazon.com/organizations/)它可以让这件事更进一步 - 让应用策略到所有账号更容易，并且同时帮你记账。

* 分离产品环境和生产环境的缺点，是某些情况下你想要复制数据从产品环境到生产环境（或者反过来），这样需要建立VPC通道和一些自定义的ACL规则。这不是火箭科学，但还是需要留心。

## 第三阶段：大众市场或企业客户

### 认证和合规

* 一旦你的销售开始向大客户销售，他们将报告与安全相关的合规性要求和认证。第一件事 - 不要惊慌。接下来，找到一个能够处理会议，文档并且懂技术的员工。

* 试着去了解哪些部分可以得到豁免，并限制认证范围。这里有几个例子：

    * 即使只有两个员工，而你为他们单独开设另一个Amazon帐户并移动几个服务，这是值得的。这样可以限定证书只被这个账户和这两个员工使用。

    * 着手考虑将生产服务（为客户提供服务）从后台办公室服务（为员工服务）独立出来到不同的账户下。通常生产用的账户将受到更严格的监管。

    * 除此之外，你还需要执行渗透测试。在此测试期间，你邀请外部PT供应商尝试并规避你的安全体系，利用漏洞和错误配置。

    * 在某些情况下，你将提供Pen-Tester API密钥来模拟你的某个客户被黑客入侵的情况，并且黑客使用其API密钥传播到你的组织。这被称为灰色PT（grey PT）。

    * 在其他情况下，你还将允许PT检查您的代码库。价格取决于服务的复杂性，黑客经验和代码量。


* 有一个称为补偿控制的重要概念。它是你在无法贯彻执行某个关键点时可以（谨慎）使用的王牌。例如，slack机器人在发现违反策略的情况时向管理者发送消息，是没有执行该策略的补偿控制。在小型组织中，通常对罕见情况发出警报，而不是执行它们。

* 认证的很大一部分是关于公司各部分的流程和过程文档。对于小型创业公司，创建一个google文档，说明何时使用git，何时使用google文档，最后一个离开办公室时锁哪些门。当作新员工第一天阅读材料来写，并保持更新。这样，它是有用的，将有资格的获得许多认证。你可能需要注释一些句子引用req 1.2.3，以便更容易查找。

* 关注合规/认证成本本身，总成本（渗透测试，工时，以及你可能需要一些自由职业者的帮助，以按时完成你的销售周期）。

### 带上你的开发人员 - 他们是它的一个很大部分

* 开发者会感觉是针对个人（甚至可能会生气），当你拿走他们的权限。他们会觉得，相比其他保持管理员权限的开发者，他们不再被信任。有些人可能会觉得，幕后黑手太自大，将有报应。其他人可能会觉得他们束手束脚，越陷越深，他们开始为“公司”工作。

* 你不能让每个人都参与决策，但你可以努力倾听不羞于表达的声音。开发者通常不会“呜咽”，他们只是不明白是做给谁看。因此，必须继续指出哪些部分对于认证至关重要，哪些部分只是一路走来的遗留问题。把安全要求明确到具体客户名字上。

* 把自动化所需的时间也考虑上。自动化必须用于常见任务，运行时给予更高权限。例如，添加新客户或升级到新版本。没有自动化，每个人都需要管理员权限，通过适当的自动化（例如Jenkins任务），所有员工都可以自己执行该操作。对程序的更改显然需要同行审查（pull request）。

* 提醒团队领导和管理员不要使用他们的管理员权限，并像日常任务一样使用自动化。管理员权限不应该用于使别人嫉妒，而是像外科手术一样用于自动化不包括的长尾任务。这是一个领导的例子和礼貌的问题。

* 定义一个流程，为特定组件特定员工在特定时间内提供管理员权限。在某些情况下，开发人员需要两天的管理员权限以便加快开发新组件或自动执行重复性任务。定义一个具有日志记录跟踪的流程，你可以向审计员提供。这样的话开发人员不用每天跑10趟管理员那里，那样会给整个团队很多挫折感。

* 一些（小）公司定义所有开发人员都是管理员。你的审核员可能会接受，并在其报告中添加对此的评论。

* 通过平衡安全性和用户体验来减少摩擦。你最不希望看到的是是开发者停止关心，开始相信规则不适用于他们。寻找[安全疲劳](https://www.nist.gov/news-events/news/2016/10/security-fatigue-can-cause-computer-users-feel-hopeless-and-act-recklessly)的迹象,并迅速解决它们。

### 对每个影响生产的变化使用变更管理

在这一点上，您应该已经具有自动测试，以及（至少半）自动升级和降级生产版本。下一步是确保生产系统是不可变的。意思是，[一个一旦部署就不改变的服务器实例](https://martinfowler.com/bliki/ImmutableServer.html)，只是替换为一个新的实例。

* 缺点是，如果自动化服务器关闭，或者甚至一些测试偶尔失败，整套组织就会终断。有了Murphy的帮助，你可以在紧急情况下部署一个的快速修复到生产环境。

* 接下来是你需要一种方法来覆盖这种自动化。它不必是管理员权限。它也可以是一个标签，标记着推动生产一个未经测试的工件。当开发人员使用此标记作为补偿控制时，可以向管理员/管理者发送通知。

* 对影响生产行为的数据库值或切换的任何更改都必须通过更改管理（如pull request或类似系统）。

### 身份管理和单点登录（SSO）

* 到某些时候，SaaS供应商的数量乘以员工的数量使得密码管理器难以管理，特别是当员工加入或离开组织时。密码应该只有管理员有密码，其他所有SaaS应用程序都应使用相同的身份管理服务（支持单点登录）。

* 整合这样一个平台需要一些时间。对于初学者，Google G-Suite可以对支持OAuth或SAML的所有站点做单点登录。身份即服务提供商，还支持基于浏览器的身份验证，智能两步验证规则，以减少与员工的摩擦，并通过ldap或radius与VPN / SSH集成。

* 一些供应商没有管理员权限管理服务。所以管理员仍然需要使用密码管理器。

### 物理安全

* 办公楼的安保和保险公司很可能规定警报器在下班时间内必须为启用状态。建议设置为在23:00自动启用，因此即便某员工忘记了，你也不用担心。

* 如果办公室的入口未被安全摄像机监控，你可以购买一个互联网摄像头，连接手机app，可以通过手机监控谁最后离开了办公室并忘记锁门/启用警报器。 所以你可以监控谁是最后一个离开办公室，忘记锁定门/激活闹钟。如果真的被盗，你可以看到他们的脸。

* 此时，您将使用基于芯片的门系统来替换您的密码锁大门。

* 这样做，你就不需要每次员工离开公司就更换密码。清洁工可能不会得到一个芯片，因为他们人可能会更换的比较频繁，所以你应该有人在清洁工离开之后锁门。磁性门卡（带磁条和摄像头）通常比较贵，并且对于新员工和候选人来说，更像是“类似企业”。然而，与门芯片系统相比，复制或破解它更加困难。

## 第四阶段：签到大客户，或快速增长

### 客户用户管理

有许多身份即服务供应商提供登录和客户的密码管理服务。如果这样的供应商符合SOC2标准，那么他们可能比你在存客户密码方面做得更好。

他们还提供自助服务和api来授权和取消授权用户，执行密码策略和恢复丢失的密码。虽然大客户可能希望与自己的身份管理解决方案进行集成。

### 敏感数据泄漏

数据泄露（业务损失和赔偿）的财务影响可能导致创业公司破产。

* 作为您的安全培训的一部分，向员工解释什么是私人信息，以及在组织里是如何处理它们的。
这个可以帮到你[未来的隐私论坛发布了视觉指南](https://fpf.org/wp-content/uploads/2016/04/FPF_Visual-Guide-to-Practical-Data-DeID.pdf)。
![privacy visual guide](/images/image_2.png)

* 向你的员工解释，犯错是不会被炒鱿鱼的。请他们在发生事故时，尽快通知你，以便您可以解决问题并减小伤害。遵守这个承诺。阐明有意的内幕泄露数据与不幸的人为错误之间的区别。需要说明的是，不同的员工来自不同的文化背景和工作背景，可能会对此有误解。

* 通过修改可公开的数据，或者将个人信息从数据中去除，来减少数据泄露的潜在损害。这通常需要管理层做出商业决策，即你的组织可以不依赖于在当前普遍认为“必须”的数据，生存下去。这个想法是通过删除敏感数据或至少拒绝大多数员工访问该数据的方式，推迟对“企业”的安全软件的需求。

* 在正确的地方使用正确的工具以防止数据泄露：

    * 通过在远程虚拟桌面工作而不是本地桌面，将数据离开本地。

    * 使用浏览器隔离技术将恶意软件移离笔记本电脑。它可以让你感觉在本地正常浏览网站，但事实上你看到的是从远程机器传来的图片，你通过它在做浏览。

    * 使用手机和笔记本电脑上的[数据防泄漏工具](https://www.google.com/search?q=Gartner+Magic+Quadrant+for+Enterprise+Data+Loss+Prevention)监控和防止数据泄露。这些需要部署在所有组织资产上，并对特定数据类型进行配置和监控。

    * 使用[移动设备管理](https://www.google.com/search?q=gartner+enterprise+mobility)监控或管理笔记本电脑和移动应用程序授权配置和操作系统设置（屏幕锁定/加密/VPN设置等）。Google G-Suite具有内置的基本MDM功能。

    * 保护身份验证和授权过程留下的所有数据。审计相关交易，以备法庭调查和数据监控。

    * 对于数据存储读/写操作（当你不需要索引）使用应用级加密，对数据存储使用磁盘及网络级加密。

### 防止你的对外互联网服务的被黑

* 根据[OWASP前十项目](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project)执行安全代码训练。

* 使用WAF和DDoS缓解服务。

* 运行外部漏洞扫描（在您的网络之外）。这应该能保护你躲过初级破解者对容易目标的搜寻。

* 运行内部漏洞扫描（在防火墙内）。这应该可以保护你：如果有黑客已经攻陷一台服务器的情况下，继续朝系统核心靠近。这通常需要代理或ssh访问，并且能够透过防火墙扫描。

* 使用渗透测试和漏洞奖励计划。指你付钱给真正的黑客来尝试查找特定的漏洞。在此测试期间，您允许外部PT供应商尝试并规避您的安全，并利用漏洞和错误的配置。

    * 在某些情况下，你将提供Pen-Tester API密钥来模拟你的某个客户被黑客入侵的情况，并且黑客使用其API密钥传播到你的组织。这被称为灰色PT（grey PT）。

    * 在其他情况下，你还将允许PT检查您的代码库。价格取决于服务的复杂性，黑客经验和代码量。

    * 赏金计划允许你接触有特殊才能的黑客。

* 定期升级你的第三方依赖库。或者甚至更好，使用自动创建pull request的机器人来升级第三方库版本。

* 扫描源代码漏洞。一些供应商使用静态和动态代码分析你的代码。其他供应商扫描常用的开源软件（请参阅SourceClear，BlackDuck，CheckMarx）。

### 数据备份

确保组织的关键数据有备份（即使这意味着需要时间从备份还原）：

* 确保您的备份是自动，持续，并覆盖所需的数据集，以避免丢失数据。

* 确保备份是在不同的云帐户，以避免人为错误或恶意删除数据。

* 确保备份位于[不同地区的不同数据中心](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html)，以防天灾导致的数据丢失。

* 有些甚至将数据复制到不同的云提供商。例如，Google Cloud可以[持续备份数据到Amazon S3上](https://cloud.google.com/storage/transfer/)。

* 并不是所有的数据对于企业生存同等重要。如果数据量和备份成本过高，请仅从关键数据开始。

* 确保恢复过程有详细的记录和测试。你不想发现您尝试从数据丢失中恢复时，发现以为有用的备份其实没法用。

* 几乎任何认证或大客户都会要求您提供年度备份/恢复实践的副本。

### 为在数据泄漏/黑客事件发生后的第二天上午做准备

* 启用任何可能的云服务的日志，即使它花费更多。将所有应用程序和服务器基础结构的日志集中保存。日志保存至少1年。

* 与您的总法律顾问（律师事务所）和会计师事务所合作，并制定事件应对计划。这些是需要做的调查，修复和控制所造成的损害的行动清单。这还包括与客户，最终用户和当局的沟通。大型法律和会计师事务所拥有人脉和经验，可以帮助制定这样一个计划。

## 第五阶段：“老妈，快看！我上报纸了！”

当您有明确的业务需求（巨大的业务成功）和可靠的安全预算时，开始寻找可以适应你的组织的安全主管（或安全VP或CISO）。这是可能需要几个月的过程。原因是要求在第一阶段需要高技术技能，并要求可以从CEO/CTO分担一些职责，这需要一些特征，比如参与销售周期和签署官方公司文件。当然，安全执行官必须符合贵组织的文化。在这个视频中可以找到这样的人的实例：[https://www.infoq.com/presentations/security-etsy](https://www.infoq.com/presentations/security-etsy)。

### 决定预算 - 构建威胁模型

威胁模型是你可以用来决定一个对安全措施的投资是否合理的经验法则。 [摩萨德还是不是](https://www.schneier.com/blog/archives/2015/08/mickens_on_secu.html)是一个基本的威胁模型，我们考虑两种攻击者：政府和其他人。

如果你被摩萨德攻击，放弃。没有钱会保护你 - 摩萨德可以替换你的新笔记本电脑[修改硬件路由](https://www.schneier.com/blog/archives/2015/03/cisco_shipping_.html)，毫无防备地进入你的办公室系统，[购买远程越狱黑客工具](https://www.zerodium.com/program.html)，甚至敲诈您的一名员工。任何停止这种威胁的投资都是浪费钱。

然而，如果你不是受到摩萨德的攻击，你实际上可以通过合理的投资保护自己。决定何时将投资从非摩萨德转为摩萨德的好的基准是考虑一个可能的，难以阻止的非法攻击。比如贿赂有特权的员工。换句话说，如果黑客攻击你的密码（即暴力强制你的密码）的成本高于贿赂一个有特权的员工的成本，那么投资更多的资源就是浪费。

### 决定预算 - 各种考虑

* 请记住，当您的公司发展壮大时，你的被攻击面以及被攻击动机也越来越大。随着时间的推移，你的安全预算将不得不相应增长。这笔预算向你的投资者显示你认真对待安全。

* 看一下完整的风险分析，并尝试先关闭大漏洞。这些是最可能的或最具破坏性的（或两者）。将所有的努力集中在应对单一的攻击方向上，攻击你的人通常会放弃攻击下一个漏洞。

* 一些要求来自客户和合规性，并不一定是你的风险。例如，客户担心Amazon会复制其业务数据，会要求AWS内端到端加密流量。虽然AWS内部人员可能会窃取您的数据，或者复杂的恶意软件会破坏虚拟机隔离，但这可能并不是你最担心的 - 但它是客户最担心的。
* 
### 风险管理

新安全经理将采取的首要步骤之一就是评估不同的风险和表现的可能性。

大体上，你可以查看DBIR报告提供的相关统计信息：

![DBIR report industry stats](/images/image_3.png)

有关基于DBIR报告的更详细的列表，请参阅[CIS控制有效的网络防御](https://www.cisecurity.org/critical-controls/)文档的附录B和C。

下一步是对潜在的业务损害作出有根据的猜测。 这里是一个例子：

<table>
  <tr>
    <td>攻击</td>
    <td>攻击方向/攻击者</td>
    <td>预计今年的攻击次数</td>
    <td>攻击伤害（包括已经缓解的部分）</td>
    <td>今年的总伤害</td>
  </tr>
  <tr>
    <td>欺诈</td>
    <td>CC欺诈
友善的欺诈
市场欺诈</td>
    <td>高</td>
    <td>低</td>
    <td>高</td>
  </tr>
  <tr>
    <td>停机</td>
    <td>天气
DDoS</td>
    <td>中</td>
    <td>中</td>
    <td>中</td>
  </tr>
  <tr>
    <td>物理性盗窃</td>
    <td>办公室被盗
车被盗
家被盗
内部人犯错</td>
    <td>中</td>
    <td>低</td>
    <td>低</td>
  </tr>
  <tr>
    <td>IP盗窃/泄漏</td>
    <td>笔记本电脑恶意软件
手机恶意软件
服务器漏洞
供应商遭到黑客入侵</td>
    <td>低</td>
    <td>高</td>
    <td>中</td>
  </tr>
  <tr>
    <td>（客户）数据盗窃/泄漏</td>
    <td>笔记本电脑恶意软件
手机恶意软件
服务器漏洞
供应商遭到黑客入侵
数据中心泄漏</td>
    <td>中</td>
    <td>高</td>
    <td>高</td>
  </tr>
  <tr>
    <td>业务/人力资源/内部文件盗窃/泄漏</td>
    <td>笔记本电脑恶意软件
手机恶意软件
供应商遭到黑客入侵</td>
    <td>中</td>
    <td>中</td>
    <td>中</td>
  </tr>
  <tr>
    <td>数据损坏或绑票</td>
    <td>服务器漏洞
身份盗窃
笔记本电脑恶意软件</td>
    <td>中</td>
    <td>中</td>
    <td>中</td>
  </tr>
  <tr>
    <td>资金流失（Bitcoin，ec2实例）</td>
    <td>身份盗窃
服务器漏洞</td>
    <td>中</td>
    <td>中</td>
    <td>中</td>
  </tr>
  <tr>
    <td>客户闯入你的服务</td>
    <td>服务器漏洞
身份盗窃</td>
    <td>中</td>
    <td>高</td>
    <td>高</td>
  </tr>
</table>
  </tr>
  <tr>
    <td>Physical Theft</td>
    <td>Office Thief
Car Thief
Home Thief
Insider Misuse</td>
    <td>Medium</td>
    <td>Low</td>
    <td>Low</td>
  </tr>
  <tr>
    <td>IP Theft/Leak</td>
    <td>Laptop Malware
Mobile Malware
Server Vulnerabilities
Vendor Hacked</td>
    <td>Low</td>
    <td>High</td>
    <td>Medium</td>
  </tr>
  <tr>
    <td>(Customer) Data Theft/Leak</td>
    <td>Laptop Malware
Mobile Malware
Server Vulnerabilities
Vendor Hacked
Datastore Leak</td>
    <td>Medium</td>
    <td>High</td>
    <td>High</td>
  </tr>
  <tr>
    <td>Business/HR/Internal Documents Theft/Leak</td>
    <td>Laptop Malware
Mobile
Vendor Hacked</td>
    <td>Medium</td>
    <td>Medium</td>
    <td>Medium</td>
  </tr>
  <tr>
    <td>Data Destructed or Held Ransom</td>
    <td>Server Vulnerabilities
Credentials Theft
Laptop Malware</td>
    <td>Medium</td>
    <td>Medium</td>
    <td>Medium</td>
  </tr>
  <tr>
    <td>Money Loss (Bitcoin, ec2 instances)</td>
    <td>Credentials Theft
Server Vulnerabilities</td>
    <td>Medium</td>
    <td>Medium</td>
    <td>Medium</td>
  </tr>
  <tr>
    <td>Customers hacked  through your service</td>
    <td>Server Vulnerabilities
Credentials Theft</td>
    <td>Medium</td>
    <td>High</td>
    <td>High</td>
  </tr>
</table>


The next phase details the prevention and exposure reduction techniques for each threat. This table is the basis for the work plan:

<table>
  <tr>
    <td>Prevention</td>
    <td>Exposure Reduction</td>
    <td>Attack Vectors/Actors</td>
  </tr>
  <tr>
    <td>Automatic Fraud Prevention</td>
    <td>DIY Heuristic + Manual Review</td>
    <td>Marketplace Fraud
Friendly Fraud
CC Fraud</td>
  </tr>
  <tr>
    <td>Multi-Region (Active Active)</td>
    <td>Failover Region Practice</td>
    <td>Weather</td>
  </tr>
  <tr>
    <td>DDoS protection</td>
    <td>Talk with AWS account manager
404/403 Alerts</td>
    <td>DDoS</td>
  </tr>
  <tr>
    <td>Alarm
Door chip
Separate laptop from 2FA (mobile phone)
Lock</td>
    <td>Move all servers and VPN to the cloud
Disk Encryption
Never leave laptop in car
Pin code/Password
Remote Wipe (company phones)</td>
    <td>Office Theft
Car Theft
Home Theft</td>
  </tr>
  <tr>
    <td>Privileged Access Management
DLP
</td>
    <td>Treat employees nicely
Access Logs
MDM
Off-boarding checklist
Privacy Training
New hire reference check
NDAs</td>
    <td>Employee Misuse
Freelance Misuse
Vendor Misuse</td>
  </tr>
  <tr>
    <td>Move IP to enterprise data vault
Endpoint Protection
DLP</td>
    <td>Least Privilege
Access Logs
Training
Encrypted Data</td>
    <td>Malware
</td>
  </tr>
  <tr>
    <td>OS/Docker automatic upgrades
Libraries Upgrade
External Vulnerability Scans
Penetration Testing
Security Bug Bounty</td>
    <td>Vulnerabilities RSS feeds
Failed Login alerts

Backup in another cloud account/region

Network Isolation (Security Groups/Subnets/ VPN/ Cloud Account)

Internal Vulnerability Scans</td>
    <td>Server Vulnerabilities</td>
  </tr>
  <tr>
    <td>2FA
Secure credentials on laptops
Secure credentials on servers</td>
    <td>Replace Admin passwords annually
</td>
    <td>Credentials Theft</td>
  </tr>
  <tr>
    <td>Protect SQL/NoSQL with username/Password

Require VPN 2FA to access them

App Level Encryption</td>
    <td>De-identification/Redaction/Deletion of unused data
Don't create local copies

Training

Access Logs</td>
    <td>Datastore Leak</td>
  </tr>
</table>


# Contributing to this repository

We welcome Pull Requests from Engineers that are working at a startup, which is also the target audience of this document. Try to keep it short and to the point. There is also some tension between keeping it practical, and keeping it vendor neutral. We're open for suggestions.

Thanks for Shahar Keidar, Avishai Ish-Shalom, Yogev Levi Shaked, Elad Shulman and Eliran Ben-Zikri for reviewing, commenting and helping out with writing the first version of this blog post.

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
