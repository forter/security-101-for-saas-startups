## Phase 1: Working in the living room (or living at work)

### Sharing Admin Passwords

* Any product has at least one user - the admin. The minimum you could do when your small startup is about 4 people, is to replace the default admin password with a complex password and share it with a password manager that supports sharing.

* The reason for sharing is to avoid a situation where only a single employee has permissions to the system, while another employee needs it.

* It is preferable to have a different user for each person for each service. A middle-ground is to create an ‘admin' (for special circumstances), developer (for day to day work) and ‘service' users (for your code). The idea is that when a developer leaves, you don't need to replace your service passwords.

* Explain to your employees that eventually they need to memorize two passwords, your laptop's and the password manager's.

* Explain to your employees not to use their "home" or “personal” password. They have most likely been exposed, or would be exposed. See [https://haveibeenpwned.com](https://haveibeenpwned.com)

* Explain how to choose the password manager's password. There's a[ short video by Sophos](https://nakedsecurity.sophos.com/2014/10/01/how-to-pick-a-proper-password) that explains it.
![how to pick a proper password](https://github.com/forter/security-101-for-saas-startups/raw/abs-image-links-for-embedding/images/image_0.png)

### Phishing emails, porn and torrents are the devil in disguise

* Employees would probably use their work laptop at home for their personal needs. That's fine. Nevertheless, from day one, explain your employees not to use it for torrents downloads or porn or any other shady website. Ask them to buy a 2nd hand laptop for that kind of stuff.

* If you got hacked it would most likely start with an employee clicking a link in a phishing email. As one of your fun startup activities play [phishing quiz](https://www.google.com/search?q=Phishing%2520Quiz).

* Stop using email attachments. Employees that are used to opening email attachments are the first ones to accidentally install a malware. Document sharing is Google Drive, or if you are in a regulatory environment then [Box that are more expensive](https://www.box.com/security/it-admin-controls).

* For other internal communication use Slack. Email is for contacting customers and vendors.

* Use your password manager to share passwords, credentials and secret notes.

* Stop using thumb drives.

* For more background information read the [DBIR Report](https://www.google.com/search?q=DBIR%2520Report).

### Encryption today is only one click away

If your laptop gets lost or stolen, you would not want the data would be compromised.

* Mac users can encrypt their drive with 1 click.
* Windows users would need the Pro version and prefer laptop hardware that supports TPM.
* Linux users would require disk reformatting.

A note about choosing laptops. If in the future, you would need to control all laptops centrally due to compliance requirements (such as MDM), it is important to know that most vendors don't have linux support. Mac, Windows Pro, Android, iPhone - yes. Linux usually partial support or non-existent.

Non-jailbroken iPhones are much more difficult to hack compared to Android. They also have screen lock and encryption enabled by default. Make sure that your managers and admins have screen lock on their phones, and encryption enabled.

### Fixing known vulnerabilities

Most operating systems (on your laptop or the cloud) have an option for automatic security upgrades. It's a one liner configuration in most cases. This could reduce the attack surface about 10 times.

### Buy at least 2 or 3 domain names

You would need at least one domain for your website, one for your API, and one for internal use.

* The first domain is usually the company's official name or brand. It used for outbound marketing (the website) and for employee emails. Both would probably be managed by an external service provider. Protect this email domain with SPF and DKIM. It's not that complicated and reduces phishing attempts in which hackers imposter your managers or admins. Many security incidents start with an employee opening a phishing email so this is important.

* The second domain is required for the service itself (for example the rest api endpoint). This domain requires extra care, and unlike the company domain it would probably be hosted in AWS route 53 and managed by the engineering. There are two main reasons for this domain. First the company's domain is protected by SPF which makes it more difficult to send automated emails from AWS SES without it ending up in a spam folder. The other reason is that automated outgoing emails could be marked as spam by the receiver. This is bad enough without it affecting all of your employee's emails (ending up in spam boxes too).

* A third domain is needed for internal use and back office. This domain would probably be registered anonymously, so it would be a little more difficult to find.

### Use SSL where possible

Use SSL anywhere possible. In your website, your API, your back office servers, and if it's not too difficult even between internal services.

For easier automation look at AWS ACM, or Let's Encrypt ACME.

Monitor your endpoint's public certificate expiration date, to detect prevent certificate expiration.

Remember that SSL encrypts network traffic, but does not supply authentication. SSL is also not a replacement for 2FA.

### Hash your customer's passwords with a proper password hashing function

This might seem to technical and for your developers eyes mostly but you need to be prepared for that data breach and this is low effort - high reward! If your database was breahed and published it's much worse when your customers' passwords are included and easily cracked - folks reuse passwords. [It's true](http://mashable.com/2017/02/28/passwords-reuse-study-keeper-security).

* Use a well known hashing algorithm to store customers passwords in your database: bcrypt, PBKDF2 or scrypt with a work factor that takes [about 1 second for the password hash](http://security.stackexchange.com/a/3993/69959).

* Do not use MD5, SHA1 or other hashes that are *not specifically designed for passwords*. Passwords stored like this are cracked in seconds usually.

* [Follow the OWASP guidance](https://www.owasp.org/index.php/Password_Storage_Cheat_Sheet) and demand your developers hash passwords using one of the above.

### Picking a SaaS vendor

* Once committed to an infrastructure vendor, it is difficult to switch them. In the future you would need to screen vendors that have access to your organisation's data. Therefore, for cloud infrastructure try choosing one of the big vendors (Amazon, Google, Microsoft), or at least a vendor with a SOC2 Type2 certification (for infrastructure vendors), PCI for payment vendors, or any other relevant certification or compliance for that industry.

* This doesn't mean their service is good. It means down the road you won't need to replace them even if their service is good.

* By default AWS users choose Oregon (us-west-2). If you know where your target market is, you should start with a datacenter closer to the target market.

* There is also regulatory implications in which country the data center resides (Data Residency). For European customers, this could be a deal breaker, and later moving to another region might be cost prohibitive.

### API key

If your company exposes APIs (as a service), make sure each one of your customers have their own API key, Otherwise your service could go down, when one of the customer's QA's has a bug in their testing script.

### Working with Git

Working with git and pull-requests is the de-facto standard way of performing change management. Part of compliance requirements you would need to show that your startup has proper change management controls and tests. Better start now.

Using git would allow you to add outsource/freelance developers for a limited time, by giving and then revoking commit permissions.

## Phase 2: Signing your first customer / Round A

### Be a little paranoid

* Every service you use requires a 2nd authentication factor (2FA). Usually it's a mobile app that receives a push notification on each login, where the user is required to tap once on the phone. In other cases the user would have to type in a 6 digit code.

* Startups that target enterprise customers or that work in a regulated environment usually enable 2FA from day one.

* Mobile phone 2FA problems start when an employee lost/forgot/replaces his mobile phone, or is stuck without battery, and then he is locked out of the system. That's why some organizations use yubikey instead (a small usb plug that can sense human finger touch). Like a Mobile App Push notification, yubikey protects against malware and hackers that keylog your password. The downside is that unlike their mobile phones, employees are more likely to loose the yubikey together with their laptop. So if the stolen laptop falls into the hands of a professional that can extract the passwords from the laptop then they could also login to any service with the yubikey. For most organisations this is not a likely attack and thus the yubikey is becoming very popular.

* Using SMS as a 2nd factor is discouraged and should be disabled. An experienced hacker can convince your mobile network customer support to [move your line to his](http://www.forbes.com/sites/laurashin/2016/12/20/hackers-have-stolen-millions-of-dollars-in-bitcoin-using-only-phone-numbers/) possession. Also recently it was discovered that 800M android devices
 had [a malware that reads SMSs](http://thehackernews.com/2016/11/hacking-android-smartphone.html).

* Using voice phone calls as a 2nd factor should also be disabled. Hackers will simply try to login when your phone is offline and hack into your voice mailbox by guessing your 4 digit code, that you probably never changed.

### Insider stealing information from the organisation

* Prepare a checkout form for leaving/terminated employees. Make a list with all of the services that requires de-provisioning/suspending (remember the Whatsapp group too, and while we're at it don't send the door password over Whatsapp).

* Check Google Docs logs (or similar) if a terminated employee has downloaded sensitive information.

* Most Endpoint Security Products can also be configured to prevent the usage of devices (such as USB, Bluetooth, Mobiles) for copying data out of the laptops.

* In case the terminated employee had access to admin passwords, it is recommended to replace passwords to sensitive systems.

* When hiring a new employee ask his former colleagues about his personality type, and the way he left their previous company. Please note that at least in Israel it's illegal to ask an employee to present a criminal record sheet.

### VPN

* It is relatively easy to find integration vendors that can install an office VPN (don't do it yourself).

* A combination of a VPN deployed in the office and a static ip address for the office internet, allows to restrict management access to servers. For example, instead of opening port 22 (SSH) to the entire internet, you allow only access from the office, or from home when connected to the office's VPN.

* Alternatively a cloud based VPN (installed on ec2 for example) has a few more advantages. First all of the communication between the office and the cloud is encrypted (especially important if you are accessing data stores such as elastic search without SSL). The network performance is much better for remote workers that are physically located far from the office. Also it relaxes the need for physical security somewhat since there is no network equipment there (the office is just another coffee shop). The downside is that each time you get disconnected from the office network you need to reconnect to the VPN.

* VPN connection should have 2nd factor enabled too.

### Antivirus/Firewall

* It's very easy to install an Endpoint Security Product. Make sure the product supports the operating system of all of your laptops. Configure automatic updates, send an email alerts (could be noisy), and block all incoming connections. The last one is important for developers running servers locally.

* It is better to install the antivirus before the employee arrives, as there are many developers that installing an anti-virus turns them down.

* Most products have an export/import functionality, which makes it easier to setup.

* There are extra protection products on top of an antivirus called EDR (Cyberreason, BlackCobalt) but these are usually costly.  

### Physical security

* Remind employees to lock all the doors and windows before they go home, and to enable the alarm.

* Add a code to the front door during office hours, to deter office thefts. Ask employees to approach strangers in the office if they are not with another employee.

### Preventing your cloud servers from being compromised

* Review the cloud firewall configuration to make sure there are no embarrassing mistakes.

* Open an email group and name it [security@mycompany.com](mailto:security@mycompany.com) and add a page on your website to report security incidents to this email.

* In order to get alerts when there are serious known vulnerabilities, that everyone knows about (except you) open a Zapier account and with a few click connect vulnerability RSS feed to Pagerduty. Here is the RSS feed and a sample Zapier filter configuration

* [https://nvd.nist.gov/download/nvd-rss.xml](https://nvd.nist.gov/download/nvd-rss.xml)
![security rss filter](https://github.com/forter/security-101-for-saas-startups/raw/abs-image-links-for-embedding/images/image_1.png)

* It is very difficult at a later stage to separate the production network from the development network. In AWS security is most easily managed on an account level, so a development VPC should be on a separate account in the same organisation. Usually there are three accounts. One for Consolidated Billing, one for production and another one for everything else (development and back office that are configured via network ACLs to communicate only with your office).

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

* Developers take it very personally (and might even get angry) when you take permissions away from them. They would feel that they are no longer being trusted, compared to other developers that get to keep the admin permissions. They could feel that whoever is the driving force behind the certification is having an ego-trip on their expense. Others might feel that they are being handcuffed, bogged-down, and that they started working for "a corporate".

* You cannot get everyone involved in the decision making, but you can make an effort to include representatives for different opinions that are not shy to speak up. Developers usually do not "whine", they just don't get who needs all that stuff. Therefore it is crucial to keep pointing out which parts are crucial for the certification, and which are just backlog items that are being added into the certification effort along the way. Specify concrete customer names mapped to security requirements.

* Take into account the time required for automation. Automation must be used for common tasks that until recently required elevated privileges. For example, adding a new customer, or upgrading to a new version. Without automation everyone needs admin privileges, with proper automation (for example a Jenkins task), all employees can perform that operation by themselves. Changes to the procedure would obviously require peer review (pull request).

* Remind the team leaders and administrators not to use their admin privileges, and use automation for day-to-day tasks like anybody else. Admin privileges should not be used to make others jealous, but rather for surgical actions for long tail tasks that automation doesn't cover. It's a matter of leading by example and curtesy.

* Define a process for providing admin privileges for a specific component for a specific employee for a limited time. In some cases a developer needs admin privileges for two days to speed up development of a new component or automate a repetitive task. Define a process that has a logging trail, which you can present to your auditor. This is needed so developers would not need to go to the admin ten times a day, since it would create a lot of frustration for all parties involved.

* Some (small) companies define that all developers are admins. Your auditor might accept that and add a comment about that in his report.

### Use change management for every production-affecting change

* At this point you should already have automated testing, and (at least semi-) automatic of upgrading and downgrading production versions. The next step is to make sure the production system is immutable. Meaning, [a server that is once deployed, is never modified](https://martinfowler.com/bliki/ImmutableServer.html), merely replaced with a new updated instance. Any change of code, database, toggles must go through change management (like a pull request, or similar system).

* The downside is that if the automation server is down, or even a few tests fail sporadically, the organisation grinds to a halt. With a little help from murphy that would happen exactly when you need to deploy an urgent quick-fix to production.

* What follows is that you need a way to override this automation. It doesn't have to be admin privileges. It could also be a tag that means pushing to production an untested artifact. You can send a notification to the managers/admins when a developer uses this tag as a compensating control.

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

They also provide self service and apis to provision and de-provision users. Although, large customers might want integration with their own Identity management solution.

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

When you have a clear business need (great business success) and a respectable security budget, start looking for a Director of Security (or VP Security or CISO) that can fit into your organization. This is a process that can take many months. The reason is the requirement for high technical skills needed in the first stages, and taking responsibility off the CEO/CTO that require other traits, such as participating in the sales cycle, and signing official company papers. And of course the security officer, must fit into your organisation's culture. A live example of such person can be found in this video:[https://www.infoq.com/presentations/security-etsy](https://www.infoq.com/presentations/security-etsy).

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
