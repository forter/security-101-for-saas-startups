## 第一阶段：在客厅工作（或工作和休息在一起）

### 共享管理员密码

* 任何产品至少都会有一个用户：管理员。当你的小型初创企业有大约4人时，你至少可以把缺省的管理员密码换成一个复杂的然后分享给密码管理器并负责共享给别人。

* 共享的目的，是避免出现当只有一个雇员有对系统的权限，而其他雇员需要的情况。

* 理想的情况是每个人在每个服务上有自己的账号。一个折中的方法是创建一个'admin'(特殊情况下使用)，一个'developer'(作为日常工作用)，一个'service'(给程序使用)。这样做的意义是当你的一位开发者(developer)离开的时候你不需要替换你的服务(service)密码。

* 解释给你的雇员听，他们需要最后记住两个密码：笔记本的密码和密码管理器的密码。

* 解释给你的雇员听，不要使用他们的家庭或个人密码。否则密码很容易被公开或者已经公开。参见 [https://haveibeenpwned.com](https://haveibeenpwned.com)

* 解释如何选择密码管理器的密码。这里有一个[简短的视频(作者Sophos)](https://nakedsecurity.sophos.com/2014/10/01/how-to-pick-a-proper-password)可以帮你解释。
![如果选择合适的密码](/images/image_0.png)

### 钓鱼邮件，色情和bt是伪装的魔鬼

* 雇员很可能同时用他们的工作笔记本在家作为个人电脑使用。这很正常。但是，从第一天起，解释给你的雇员，不要用于bt下载，或者色情或其他有问题的网站。请他们买一个二手笔记本用于那些目的。

* 如果你被黑了，很可能是从一位雇员点击一封钓鱼邮件开始的。作为你的初创企业有趣活动之一： [钓鱼测试](https://www.google.com/search?q=Phishing+Quiz).

* 停止使用邮件附件。习惯于打开邮件附件的雇员总会不小心安装恶意软件。可以用Google Drive来分享文档，或者你在一个受监管的环境可以[付费使用Box](https://www.box.com/security/it-admin-controls)。

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
* 第二个域名是SaaS服务本身需要的，例如rest api。参见www.google.com之于www.gmail.com之于maps.googleapis.com。这个域名需要额外关照，和公司域名不同，他很可能需要架设在AWS Route53上，并由他们的服务工程师团队管理。

* 第三个域名用来作为内部使用和后台。这个域名需要明显于其他两个不同，并且容易写。有些公司使用公司域名的二级域名。但是，这也意味着它不能由需要为小型内部服务频繁更新的后台服务开发人员管理。二级域名还会让人混淆 - 到底哪个是内部使用，哪个是外部可见。还有一个附带的好处是如果你匿名注册这个域名。大多数情况余名解析服务也是内部的（私有Route53域名）。

* [大批量邮件发送](http://resources.mailgun.com/email-reputation.html)服务应该针对目标市场，交际性质邮件，公司邮件分别维护域名或者二级域名。这可以隔绝每种邮件类型的名声并保证时间敏感的交易性质和公司邮件不会延迟或标记为垃圾邮件。当你使用独立的营销用邮件域名时，确保他不是[雪靴垃圾邮件](https://www.spamhaus.org/faq/section/Glossary#233)并保证使用web转发到你的公司或服务网站，好让你的客户找到你。

### 在所有地方使用SSL/TLS/HTTPS！

在任何可以的地方使用SSL。在你的网站，API，后台服务，如果不是太麻烦，甚至内部服务之间也应该使用。

可以通过AWS ACM, 或Let's Encrypt ACME更简单的完成这件事情。

监控你的访问节点的公开证书的过期日期，避免其过期。

牢记SSL加密网络流量，但不做认证。也不是两步认证(2FA)的替代品。


### 选择SaaS供应商

* 一旦选择基础架构供应商，就很难再切换了。未来，你可能需要减少供应商对你的组织的数据的访问。因此，在选择云端基础架构供应商时，尽量选择大的供应商（Amazon, Google, Microsoft），或至少拥有SOC2 Type2证书的供应商（针对基础架构供应商而言），拥有PCI的支付供应商，或其他有相关领域资质的供应商。

* 这并不意味他们的服务就是好的。而是接下来你不需要替换他们尽管他们的服务是好的。

* 缺省AWS用户选择俄勒冈（us-west-2）。如果你知道你的目标市场在哪里，你应该让你的数据中心靠近你的目标市场。

* There is also regulatory implications in which country the data center resides (Data Residency). For European customers, this could be a deal breaker, and later moving to another region might be cost prohibitive.

### API key

If your company exposes APIs (as a service), make sure each one of your customers have their own API key, Otherwise your service could go down, when one of the customer's QA's has a bug in their testing script.

### Working with Git

Working with git and pull-requests is the de-facto standard way of performing change management. Part of compliance requirements you would need to show that your startup has proper change management controls and tests. Better start now.

Using git would allow you to add outsource/freelance developers for a limited time, by giving and then revoking commit permissions.

## Phase 2: Signing your first customer / Round A

### Be a little paranoid

* Turn on 2FA for every service that you use. This is especially critical for your development team as those are the services that will take your product offline if they're compromised. Google accounts, Dropbox, Github, Microsoft, etc - all of them!

* Startups that target enterprise customers or that work in a regulated environment usually enable 2FA from day one.

* A well established and easy to use 2FA implementation is [TOTP 2FA implimentation](https://en.wikipedia.org/wiki/Time-based_One-time_Password_Algorithm). Employees can install [Google Authenticator](https://en.wikipedia.org/wiki/Google_Authenticator) on their mobile phone and it would produce a one-time 6 digit code that needs to be typed in addition to the password 

* A slightly more usable approach are push notifications. Many SaaS vendors support an app that instead of generating codes, sends you a push notification. That is more convenient than copying 6 digits each time you need to log-in. The downside is that you would probably need different apps for each service, and that it won't work without an internet connection, or when the push notification vendor has downtime.

* Mobile phone 2FA problems start when an employee lost/forgot/replaces their mobile phone, or is stuck without battery, and then they are locked out of the system. Some employees don't like hardening their phone (encryption and screenlock to protect the 2FA app), and feel that the company needs to buy the phone for the 2FA app to run on. That's why some organizations use yubikey instead (a small usb plug that can sense human finger touch). Like a Mobile App Push notification, yubikey protects against malware and hackers that keylog your password. The downside is that unlike their mobile phones, employees are more likely to lose the yubikey together with their laptop. So if the stolen laptop falls into the hands of a professional that can extract the passwords from the laptop then they could also login to any service with the yubikey. Another problem is that the yubikey is a USB device, and you would need to make the distinction between USB storage devices (not allowed) and the yubikey (allowed). 
* Using SMS as a 2nd factor is discouraged and should be disabled. An experienced hacker can convince your mobile network customer support to [move your line to his](http://www.forbes.com/sites/laurashin/2016/12/20/hackers-have-stolen-millions-of-dollars-in-bitcoin-using-only-phone-numbers/) possession. Also recently it was discovered that 800M android devices
 had [a malware that reads SMSs](http://thehackernews.com/2016/11/hacking-android-smartphone.html).

* Using voice phone calls as a 2nd factor should also be disabled. Hackers will simply try to log in when your phone is offline and hack into your voice mailbox by guessing your 4 digit code, that you probably never changed.

* If an employee asks for a password reset remotely, ask them to come into the office in person if possible. If this is not feasible (or time-sensitive), verify their identify: do not trust that you can recognize your employee's voice. Never email passwords.

### Insider stealing information from the organisation

* Prepare a checkout form for leaving/terminated employees. Make a list with all of the services that requires de-provisioning/suspending (remember the Whatsapp group too, and while we're at it don't send the door password over Whatsapp).

* Check Google Docs logs (or similar) if a terminated employee has downloaded sensitive information.

* Most Endpoint Security Products can also be configured to prevent the usage of devices (such as USB, Bluetooth, Mobiles) for copying data out of the laptops.

* In case the terminated employee had access to admin passwords, it is recommended to replace passwords to sensitive systems.

* When hiring a new employee ask their former colleagues about their personality type, and the way they left their previous company. Please note that at least in Israel it's illegal to ask an employee to present a criminal record sheet.

### VPN
* 寻找可以安装办公VPN的集成应商相对容易一些（不要自己安装）。

* 将VPN部署在办公室，以及给办公室的网络使用静态IP地址，可以让你对服务器的管理访问进行限制。例如，你可以将它设置成只允许从办公室访问，或从家中连接办公室的VPN，而不用对整个互联网公开22端口（SSH）。

* 基于云的VPN（例如安装在ec2上）还具有几个优点。首先，办公室和云之间的所有通信都是加密的（尤其是当你访问数据存储，如不带SSL的elastic search时）。对于远程工作人员来说，网络性能也要好得多。此外，它在一定程度上能够减少对物理安全性的需要，因为那里并没有网络设备（办公室仅仅是某个咖啡店而已）。而它的缺点是，每当你断开办公室网络连接，你需要重新连接到VPN。

* VPN连接也应当启用两步验证。

### Antivirus/Firewall

* It's very easy to install an Endpoint Security Product. Make sure the product supports the operating system of all of your laptops. Configure automatic updates, send an email alerts (could be noisy), and block all incoming connections. The last one is important for developers running servers locally.

* It is better to install the antivirus before the employee arrives, as there are many developers that installing an antivirus turns them down.

* Most products have an export/import functionality, which makes it easier to set up.

* There are extra protection products on top of an antivirus called EDR (Cyberreason, BlackCobalt) but these are usually costly.  

### Hash your customer's passwords with a proper password hashing function


If you can afford it, use a [third party authentication service](#customer-users-management) to handle password storage, password management, password recovery, two factor auth and more. Some vendors offer Monthly Active Users pricing which can fit your budget.

However, if you decide to develop your own authentication implementation, follow the [OWASP authentication guidelines](https://www.owasp.org/index.php/Authentication_Cheat_Sheet) . 

* If your database was breached and published it's much worse when your customers' passwords are included and easily cracked - folks reuse passwords. [It's true](http://mashable.com/2017/02/28/passwords-reuse-study-keeper-security). Therefore, always use hashing function *specifically designed for password storage* to store customers passwords in your database: bcrypt, PBKDF2 or scrypt with a work factor that takes [about 1 second for the password hash](http://security.stackexchange.com/a/3993/69959). Do not use MD5, SHA1 or other hashes that are *not specifically designed for passwords*. Passwords stored like this are cracked in seconds usually.


### Physical Security

* Configure laptops to sleep after (at most) 5 minutes you are away from your desk, and require a password to re-open it. Ask employees to lock their laptops manually when they leave their desks, for example using [hot corners on macOS](https://support.apple.com/kb/PH18796), or by pressing logo key + L on Windows.

* Never let a stranger within arms reach of a computer (especially if it has a USB port). Physical access is the fastest way to getting your system and product and customers compromised.

* Remind employees to lock all the doors and windows before they go home, and to enable the alarm.

* Add a code to the front door during office hours, to deter office thefts. Ask employees to approach strangers in the office if they are not with another employee.

* Lock your server room (or the room with your network equipement)

### Preventing your cloud servers from being compromised

* Review the cloud firewall configuration to make sure there are no embarrassing mistakes.

* Open an email group and name it [security@mycompany.com](mailto:security@mycompany.com) and add a page on your website to report security incidents to this email. Security researches may prefer sending an encrypted email, so you should [generate an OpenPGP key pair](https://gpgtools.org/), publish your public key on the website and save the private key in your password manager.

* In order to get alerts when there are serious known vulnerabilities, that everyone knows about (except you) open a Zapier account and with a few click connect vulnerability RSS feed to Pagerduty. Here is the RSS feed and a sample Zapier filter configuration

* [https://nvd.nist.gov/download/nvd-rss.xml](https://nvd.nist.gov/download/nvd-rss.xml)
![security rss filter](https://github.com/forter/security-101-for-saas-startups/raw/abs-image-links-for-embedding/images/image_1.png)

* It is very difficult at a later stage to separate the production network from the development network. In AWS, security is most easily managed on an account level, so a development VPC should be on a separate account in the same organisation. Usually there are three accounts. One for Consolidated Billing, one for production, and another one for everything else (development and back office that are configured via network ACLs to communicate only with your office).

* Recently Amazon announced [AWS Organisations](https://aws.amazon.com/organizations/) that takes it one step further, by making it easier to apply policies on all of the different accounts and takes care of billing too.

* The downside of separating production from development is that in some cases you would want to copy data from production to development (or vice versa) which would require VPC peering and custom ACL rules. It's not rocket science but requires attention.

## Phase 3: Mass Market or Enterprise Customers

### Certifications and Compliance

* Once your sales starts selling to large customers, they would report back on compliance requirements and certifications related to security. First thing - don't panic. Next thing, find an employee that can handle meetings and documentations and is technical enough.

* Try to understand what sections you can get waivers, and limit the certification scope. Here are a few examples:

    * Even if you need to open another Amazon account and move a few services that only two employees have access to, that could be worth your effort. It can limit the certification only to that account and two employees.

    * Consider separating production services (that serve customers) from back office services (that serve employees) into different accounts. Usually the production account would be more heavily regulated.

    * Among other things, you would need to perform Penetration Testing. During this test you are allowing an external PT vendor to try and circumvent your security and take advantage of vulnerabilities and misconfiguration.

    * In some cases you would provide the Pen-Tester API keys to simulate a situation that one of your customers got hacked, and the hacker propagates into your organisation using their secret api keys. This is called grey PT.

    * In other cases you would also allow the PT to review your codebase. The price depends on the complexity of the service, the hacker experience and the lines-of-codes.

* There is an important concept called compensating controls. This is an ace card that you could use (sparingly) when you cannot enforce a certain bullet point. For example, a slack-bot that sends a message to a manager when there is a violation of a policy, is a compensating control for this policy not being enforced. In small organisations it usually makes a lot of sense to alert on rare cases, rather than enforce them.

* A big part of certifications is about processes and process documentation of various parts of the company. For small startups, open a google doc that explains when you use git, and when google docs, and which doors you lock when you are the last one to leave the office. Write it as a new employee first-day reading material and keep it up to date. This way it is both useful and would be qualified for many certifications. You might need to annotate some sentences with references to req 1.2.3, so it is easier to look it up.

* Keep an eye on the compliance/certification costs itself, and total costs (of penetration tests, man-hours, and you might need some freelance help to get it done on time for your sales cycle to complete).

### Bring your developers onboard - they are a big part of it

* Developers take it very personally (and might even get angry) when you take permissions away from them. They would feel that they are no longer being trusted, compared to other developers that get to keep the admin permissions. They could feel that whoever is the driving force behind the certification is having an ego-trip at their expense. Others might feel that they are being handcuffed, bogged-down, and that they started working for "a corporate".

* You cannot get everyone involved in the decision making, but you can make an effort to include representatives for different opinions that are not shy to speak up. Developers usually do not "whine", they just don't get who needs all that stuff. Therefore it is crucial to keep pointing out which parts are crucial for the certification, and which are just backlog items that are being added into the certification effort along the way. Specify concrete customer names mapped to security requirements.

* Take into account the time required for automation. Automation must be used for common tasks that until recently required elevated privileges. For example, adding a new customer, or upgrading to a new version. Without automation everyone needs admin privileges, with proper automation (for example a Jenkins task), all employees can perform that operation by themselves. Changes to the procedure would obviously require peer review (pull request).

* Remind the team leaders and administrators not to use their admin privileges, and use automation for day-to-day tasks like anybody else. Admin privileges should not be used to make others jealous, but rather for surgical actions for long tail tasks that automation doesn't cover. It's a matter of leading by example and courtesy.

* Define a process for providing admin privileges for a specific component for a specific employee for a limited time. In some cases a developer needs admin privileges for two days to speed up development of a new component or automate a repetitive task. Define a process that has a logging trail, which you can present to your auditor. This is needed so developers would not need to go to the admin ten times a day, since it would create a lot of frustration for all parties involved.

* Some (small) companies define that all developers are admins. Your auditor might accept that and add a comment about that in their report.

### Use change management for every production-affecting change

At this point you should already have automated testing, and (at least semi-) automatic of upgrading and downgrading production versions. The next step is to make sure the production system is immutable. Meaning, [a server that is once deployed, is never modified](https://martinfowler.com/bliki/ImmutableServer.html), merely replaced with a new updated instance.

* The downside is that if the automation server is down, or even a few tests fail sporadically, the organisation grinds to a halt. With a little help from Murphy that would happen exactly when you need to deploy an urgent quick-fix to production.

* What follows is that you need a way to override this automation. It doesn't have to be admin privileges. It could also be a tag that means pushing to production an untested artifact. You can send a notification to the managers/admins when a developer uses this tag as a compensating control.

* Any change of database values or toggles that affects production behavior must go through change management (like a pull request, or similar system).

### Identity Management and SSO

* At a certain point the number of SaaS vendors times the number of employees makes password managers difficult to manage, especially when employees join or leave the organisation. Password is only for admins, all of the other SaaS applications should use the same identity management service (that supports Single Sign On).

* Integrating such a platform takes some time. For starters, Google G-Suite can perform SSO to all sites that support OAuth or SAML. Identity as a Service providers, supports also browser based authentications, smart 2FA rules to reduce friction with employees, and integration with VPN/SSH via ldap or radius.

* Some vendors do not have an Admin privilege management service. So admins would still need to use the password manager.


### Physical Security

* The Office Building Security and the insurance company probably require for the alarm to be active during office off-hours. It is recommended to activate it automatically at 23:00, so you won't need to enable it manually if one of the employees forgot.

* If the entrances to the office aren't monitored by security cameras, you can buy a simple internet camera, that connects to a mobile app. So you can monitor who was the last to leave the office and forgot to lock the door/activate the alarm. And if it's a real burglar you can see their face.

* At this point, you would replace your front door pin-code with a chip based door system.

* The rationale is that you don't need to replace the code each time an employee leaves the company. Take into account that cleaning service would probably won't get a chip since they may switch employees in some days. So you should have someone to lock the door after they leave. Magnetic door cards (with a magnetic stripe and a mug-shot) are usually more expensive and smell more "corporate-like" for new employees and candidates. However it is more difficult to duplicate or hack it compare to the door chip systems.

## Phase 4: Signing a large customer, or rapid market growth

### Customer user's management

There are a number of Identity as a Service vendors that supply login and customer's password management services. If such a vendor is SOC2 Compliant they probably do a better job than you saving the customer's password in your database.

They also provide self service and apis to provision and de-provision users, enforce password policies, and recover lost passwords. Although, large customers might want integration with their own Identity management solution.

### Sensitive Data Leaks

The financial impact of a data leak (business loss, and compensation) could bring a startup to bankruptcy.

* As part of your security training explain to employees what consists of private information, and how do you handle it in your organization.
The [Future of Privacy Forum published a visual guide](https://fpf.org/wp-content/uploads/2016/04/FPF_Visual-Guide-to-Practical-Data-DeID.pdf) that can help you get started.
![privacy visual guide](https://github.com/forter/security-101-for-saas-startups/raw/abs-image-links-for-embedding/images/image_2.png)

* Explain to your employees you are not going to fire anyone for making a mistake. Beg them to notify you ASAP when a mishap happened so you could fix the problem and limit the damage. Stand behind this promise. Explain the difference between an intentional insider leaking data and an unfortunate human error. This needs to be talked about since different employees come from different cultural and work backgrounds and may react in the wrong way.

* Reduce the potential damage of a data leak by redacting or de-identifying the data. This usually requires management to make a business decision that your organization can survive without data that is considered a "must have" today. The idea is to postpone the need for security software that smells “corporate”, by removing sensitive data or at least denying access to most employees for that data.

* Prevent data breaches by using the right tool at the right places:

    * Moving the data away from the laptop by working on a remote virtual desktop instead of a local desktop.

    * Moving the malware away from the laptop by using browser isolation technologies. These give you the feeling of browsing locally on your regular browser, but in fact all you see are pixels sent from a remote machine doing the browsing.

    * Monitoring and preventing leakage of data using [Data Leak Prevention](https://www.google.com/search?q=Gartner+Magic+Quadrant+for+Enterprise+Data+Loss+Prevention) agents on mobile phones and laptops. These require deployment on all organization assets and configuration and monitoring for specific data types.

    * Monitor or Manage the laptop and mobile application provisioning and operating system settings (screenlock/encryption/VPN setting/etc…) using  [Mobile Device Management](https://www.google.com/search?q=gartner+enterprise+mobility+management) agents. Google G-Suite has a built-in basic MDM capabilities.

    * Protect all data stores with Authentication and Authorization. Audit relevant transactions for forensic investigations and monitoring of data.

    * Use app level encryption for data store read/write operations (where you don't need indexing), or disk and network level encryption for data stores.

### Prevent hacking of your internet facing services

* Perform Secure Code Training based on the [OWASP top 10](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project).

* Use a WAF and DDoS mitigation service.

* Run external vulnerability scans (outside of your network). This should protect you against "Kiddy Scripts" looking for easy targets.

* Run internal vulnerabilities scan (within the firewalls). This should protect you against a hacker that gained foothold on one server, and is trying to make a lateral movement to the heart of the system. This requires usually an agent or ssh access, and ability to scan without any firewalls.

* Use Penetration Tests and Bug Bounty Programs. This is where you pay a real hacker to try and find specific vulnerabilities. During this test you are allowing an external PT vendor to try and circumvent your security and take advantage of vulnerabilities and misconfiguration.

    * In some cases you would provide the Pen-Tester API keys to simulate a situation that one of your customers got hacked, and the hacker propagates into your organisation using their secret api keys. This is called grey PT.

    * In other cases you would also allow the PT to review your codebase. The price depends on the complexity of the service, the hacker experience and the lines-of-codes.

    * Bounty Programs allows you to reach hackers with specific skills.

*  Upgrade your library dependencies regularly. Or even better, use a bot that automatically creates pull requests to upgrade library versions.

* Scan for source code vulnerabilities. Some vendors use static and dynamic code analysis of your code. Other vendors scan commonly used open source software (see SourceClear, BlackDuck, CheckMarx).

### Data backup

Make sure the organisation's critical data is backed-up (even if it means it would take time to restore it from backup):

* Make sure your backup is automatic and continuous and covers the required data sets, to avoid gaps of missing data.

* Make sure the backup is in a different cloud account, to avoid a human error or malicious deletion of data

* Make sure the backup is in a [different data centre in a different region](http://docs.aws.amazon.com/AmazonS3/latest/dev/crr.html), to avoid data-loss in case of a natural disaster.

* Some even copy their data into a different cloud provider. For example, Google Cloud has a service that can [continuously backup data stored on Amazon S3](https://cloud.google.com/storage/transfer/).

* Not all data is equally important for the business survival. If the amount of data and backup costs is too high, start with only the critical data.

* Ensure that the restore procedure is both well documented and tested. You don't want to discover that what you thought were useful backups aren't usable when trying to recover from data loss.

* Almost any certification or big customer would ask for a copy of your annual backup/restore practice.



### Prepare for the morning after the data breach/hacking incident

* Enable logs for any possible cloud service, even if it costs a little more. Centralise logs all applications and server infrastructure. Save the logs for at least 1 year period.

* Work with your General Counsel (law office) and your Accounting firm, and prepare an incident response plan. These are the list of actions that needs to be done to investigate, fix and control the damage done. That also includes communicating with the customers, the end users, and the authorities. Big law and accounting firms have a network of connections and experience that can help with devising such a plan.

## Phase 5: "Look ma!, I'm in the newspaper"

When you have a clear business need (great business success) and a respectable security budget, start looking for a Director of Security (or VP Security or CISO) that can fit into your organization. This is a process that can take many months. The reason is the requirement for high technical skills needed in the first stages, and taking responsibility off the CEO/CTO that require other traits, such as participating in the sales cycle, and signing official company papers. And of course the security officer must fit into your organisation's culture. A live example of such person can be found in this video:[https://www.infoq.com/presentations/security-etsy](https://www.infoq.com/presentations/security-etsy).

### Deciding on a budget - Build a Threat Model

A threat model is the rule of thumb you can use to decide if an investment in some security countermeasure is justified. [Mossad or Not Mossad](https://www.schneier.com/blog/archives/2015/08/mickens_on_secu.html) is a basic threat model in which we consider two types of attackers: State Actor and everyone else.

If you are attacked by the Mossad, give up. No amount of money will protect you - The Mossad can replace your new laptop [with modified hardware en-route](https://www.schneier.com/blog/archives/2015/03/cisco_shipping_.html), break into your office unnoticed, [purchase remote jailbreak hacking tools](https://www.zerodium.com/program.html), or even extort one of your employees. Any investment into stopping this threat is a waste of money.

If however you are attacked by not-Mossad you can actually protect yourself effectively with a reasonable investment. A good benchmark for deciding when your investment has transitioned from Not-Mossad to Mossad is to consider a possible, hard to stop, highly illegal attack - e.g. bribing an employee with privileged access. In other words, if the cost of hacking your passwords (i.e. brute forcing your passwords) is higher than the cost of bribing an employee with access, than there is no sense in investing more resources to protect it.

### Deciding on  budget - various considerations

* Remember that as your company grows, your attack surface and also the motivation for attacking you grows too. Over time your security budget will have to grow accordingly. This budget shows your investors that you take security seriously.

* Look at the complete risk analysis and try to close the big holes first. These are the most probable, or most damaging (or a combination of both). Focusing all your efforts on a single attack vector, would merely require your attacker to move to the next hole.

* Some requirements come from customers and compliance and are not necessarily at the top of your risk. For example, customers afraid of amazon copying their business data may require end-to-end encrypted traffic inside AWS. While it is possible that an AWS insider would steal your data, or a sophisticated malware breaks through the virtual machine isolation, this may not be at the top of your list - however it is at the top of your customer's list.

### Risk Management

One of the first steps the new security manager will do, is to assess the different risks, and the possibility of manifestation.

For a high level starting point you can look at the relative statistics provided by the DBIR Report:

![DBIR report industry stats](https://github.com/forter/security-101-for-saas-startups/raw/abs-image-links-for-embedding/images/image_3.png)

For a more detailed list that is based on the DBIR report, look at Appendix B and C of the [CIS CONTROLS FOR EFFECTIVE CYBER DEFENSE](https://www.cisecurity.org/critical-controls/) document.

The next step is to make an educated guess of the potential business damage. Here is an example:

<table>
  <tr>
    <td>Attack</td>
    <td>Attack Vectors/Actors</td>
    <td>Expected number of attacks this year</td>
    <td>Attack damage (w, existing mitigations)</td>
    <td>Total damage this year</td>
  </tr>
  <tr>
    <td>Fraud</td>
    <td>CC Fraud
Friendly Fraud
Marketplace Fraud</td>
    <td>High</td>
    <td>Low</td>
    <td>High</td>
  </tr>
  <tr>
    <td>Downtime</td>
    <td>Weather
DDoS</td>
    <td>Medium</td>
    <td>Medium</td>
    <td>Medium</td>
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
