---
title: "Agents"
weight: 3
pre: "3 . "
---

Finally, each agency can have many agents working there. We use this entity you trace the whole selling process to every user involved. When a user logs into your system, you'll have to send his/her key (token) credential so we can know who's performing the action and what consumer he/she belongs to (check Authentication in Gettin Started chapter).

----
[Agents](https://hub.airgateway.net/api/static/swagger-ui/#!/Agents/post_agents) have some specific information about the user, but these are the most relevant:

- Username
- Email
- Agency id
- Password

If you ever want your users to login in our Bookingpad app directly, you'll have to share with them their username, agency name and password. You can check more information about [Bookingpad authentication in the open source project](https://github.com/AirGateway/bookingpad-app).

> All these steps can be done via our own hub application which you'll have access to