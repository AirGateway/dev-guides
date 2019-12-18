---
title: "Authentication"
title: Authentication
weight: 1
pre: "1 . "
pre: '1 . '
---

To be able to access our platform you will have to get the proper credentials at our [Agencies Portal](https://agency.airgateway.net/). After registration, you would be able to apply for an Authentication key [here](https://dev.airgateway.net/apis/).

----
All requests sent to the **NDC Aggregation Platform**  are required to be consumer-authenticated with a two HTTP headers pair:

- **Authorization**: {Authorization-key} (obtained from our Dev Portal)
- **AG-Consumer**:  {Consumer-ID}  (a three chars. code)
----------

Note regarding Authentication:

> We will provide further details on how NDC Participant authentication
> (IATA number, Agency ID in NDC messages Party block) must be provided
> since this could be related to final production stage.
