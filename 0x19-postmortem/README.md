0x19. Postmortem

TASK 0.
Duration: 2 hours (12:00 PM - 2:00 PM EST) Impact:A segment of users, constituting around 20%, experienced difficulty accessing the checkout page on our e-commerce platform, leading to missed opportunities for potential sales.

Timeline:
12:00 PM - The problem was initially identified when our monitoring system alerted us to an increase in 500 errors occurring on the checkout page.
12:05 PM - The engineering team received notification of the issue and promptly initiated an investigation.
12:10 PM - Preliminary findings indicated a potential connection to the website's database. The team delved into the database logs and executed queries to pinpoint and understand the root cause.
12:20 PM - Subsequent investigations uncovered that the problem was, in fact, linked to the integration of the payment gateway. The team then scrutinized payment gateway logs and code.
12:40 PM - A bug in the payment gateway code, causing the checkout page to crash under specific conditions, was identified by the team.
1:00 PM - The incident escalated to senior engineers and involved collaboration with the payment gateway provider.
1:30 PM - Working closely with the payment gateway provider, the team developed and implemented a solution to rectify the issue.
2:00 PM - The problem was successfully resolved, and users regained access to the checkout page.

The primary cause was attributed to the new configuration applied to git data. Following the initiation of the rollout, this configuration led to a decline in the performance of fundamental git operations (such as pull and push requests). As a consequence of the internal framework, other services also experienced degradation, eventually resulting in a significant outage where 8 out of 10 services became unavailable.

Attempts to roll back the changes proved unsuccessful due to constraints within the framework. A gradual failover mechanism was triggered, causing the system to transition to the backup. This resulted in the restoration of write operations, leading to a shift from a major outage to a state of degraded performance for the majority of services. Subsequent efforts were dedicated to restoring databases and recovering data for pull and push requests received during the outage.

To address and mitigate future risks, internal processes are undergoing thorough review and adjustment. This proactive measure aims to ensure the safe deployment of any future changes. Additionally, a comprehensive investigation into the framework across services is underway to minimize the likelihood of multiple service failures.


TASK 1
We are constantly stormed by a quantity of information, it’s tough to get people to read you.

Make your post-mortem attractive by adding humour, a pretty diagram or anything that would catch your audience attention.

Please, remember that these blogs must be written in English to further your technical ability in a variety of settings.
