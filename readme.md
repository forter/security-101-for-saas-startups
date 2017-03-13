# Security 101 for SaaS startups

## 真希望我的第一个老板告诉我这些

如果你在一家初创企业工作，并一直在思考应该在何时开始研究安全注意事项和合规性？哪些技术债务应该推迟到以后，哪些系统应该马上强化？主要考虑因素是什么？

技术债务越堆越高，并且多数情况下比起现在偿还拖到以后会更容易。比如，如果你不是用用户名密码的方式使用ElasticSearch，你应该再三检查你的防火墙设置。等到B轮融资之后，你的初创企业很可能有了足够的人力物力来正确的保障ElasticSearch集群。

初创企业文化使得它更难“以后”再改。让我们举一个简单的例子：习惯于不做代码审查而直接提交的开发者，会抱怨说同行评审会拖慢整个开发，并让他们觉得这“太企业”。

那么早期应该做哪些安全方面的考虑？

* 产品中的哪些安全特性是客户愿意买单的？

* What are the security expectations  in your industry (Medical, Finance, Enterprise)?

* What are the target market (country) regulations (Data Privacy, Data Residency)? Europeans are known to have tougher regulations. Different US States have different regulations.

* Which tools and policies would not hurt your team's morale.

* How long would it take you to prepare a security risk plan (see example at the bottom of this document)?

    * What is the impact of Intellectual Property theft, business plans theft, bitcoin/ec2 theft, losing all your data ? How would it affect your sales, customers, investors?

    * How can you protect against a data breach?

    * How can you reduce the exposure after a data breach?

We grouped together the expected security recommendations by the different phases a start-up goes through. The more money and data the startup handles, the bigger the investment in security:

[continue reading](https://github.com/forter/security-101-for-saas-startups/blob/master/security.md)
