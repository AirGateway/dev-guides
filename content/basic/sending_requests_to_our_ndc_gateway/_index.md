---
title: "Sending requests"
weight: 2
pre: "2 . "
---

## Sending requests to our NDC Gateway

We use **HTTP/1.1** as communication protocol to accept requests to the gateway. All NDC requests are sent using the **POST** HTTP method.

The public endpoint to our **NDC Gateway** remains immutable for all NDC requests and it is:

* **Version 1**: http://proxy.airgateway.net/ndc/v1/
* **Version 1.1**: http://proxy.airgateway.net/ndc/v1.1/

We require some mandatory basic HTTP headers intended for message formatting:

* **Content-Type**: application/json
* **Accept**: application/json

It's very relevant to distinguish between two types of requests to send to the **NDC Gateway**. Attending to the architecture, we have two types of requests with significant differences between them:

* **MPR** (Multiple provider requests)
* **SPR** (Single provider requests)
