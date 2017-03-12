# Security 101 for SaaS startups

## Things I wish my first boss had told me

So you are working at a startup, and you have been wondering at what point should you start looking into security considerations and compliance? Which technical debt should be postponed for a later stage, and which systems should be hardened this instant? What are the main considerations?

Technical debt gets piled up, and in many cases it is easier to pay later rather than now. For example, if you are using ElasticSearch without username/passwords, you should double check your firewall settings. After round-B your startup would probably have the manpower and budget to properly secure the ElasticSearch cluster.

Startup culture is a bit more difficult to change "later". Let's take a trivial example. Developers that are used to pushing code without code review, would complain that peer review would bog down the development, and it might even smell "too corporate" for them.

So which security considerations are relevant at an early stage?

* What security concerns were raised by customers willing to pay for your product?

* What are the security expectations  in your industry (Medical, Finance, Enterprise)?

* What are the target market (country) regulations (Data Privacy, Data Residency)? Europeans are known to have tougher regulations. Different US States have different regulations.

* Which tools and policies would not hurt your team's morale.

* How long would it take you to prepare a security risk plan (see example at the bottom of this document)?

    * What is the impact of Intellectual Property theft, business plans theft, bitcoin/ec2 theft, losing all your data ? How would it affect your sales, customers, investors?

    * How can you protect against a data breach?

    * How can you reduce the exposure after a data breach?

We grouped together the expected security recommendations by the different phases a start-up goes through. The more money and data the startup handles, the bigger the investment in security:

[continue reading](/security.md)
