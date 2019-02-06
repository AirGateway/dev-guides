---
title: "Dev Guide"
weight: 1
---

AirGateway NDC Gateway Developer Guide
====================

This is a developer guide intended to provide insights on a technical integration with AirGateway's **NDC JSON API** aggregation service.

Our platform is designed to facilitate the interaction with the new distribution model brought by [NDC (New Distribution Capability)](http://www.iata.org/whatwedo/airline-distribution/ndc/) established by IATA and adopted by a growing number of the most relevant airlines in the World.

Our **NDC Aggregation Platform** facilitates the interaction with multiple NDC providers in a one-to-one architecture. This makes much easier to interact with distributed airline NDC APIs and therefore facilitates transitioning into this model.

Our **NDC Aggregation Platform** works as a real-time routing machine delivering and collecting concurrently shopping offers from multiple NDC providers (airlines) and deliver an asynchronous real-time aggregation isolating consumers from cases they won't need to consider such as message wrapping (SOAP, REST...), Authentication issues, API architectural issues, and ancillaries normalization.

Also transitioning among different NDC versions/implementations will be a  much easier process to handle relying on our **NDC Aggregation Platform**.

References and Links
-----------
To use our **NDC JSON API** you must sign up in our agencies portal:

* [Agencies Portal](https://agency.airgateway.net/)

We use a self-documented API Framework that produces always-up to date Swagger Documentation. This live-documentation can be found here.

* [NDC JSON API reference v1.0](https://api.airgateway.net/v1/swagger-ui/)
* [NDC JSON API reference v1.1](https://api.airgateway.net/v1.1/swagger-ui/)

You can find more examples of use in Postman:

* [NDC JSON API Postman Documentation](https://docs.airgateway.net/)

For futher questions/comments or just quickly getting in touch with our technical team you are welcome to use our Gitter Support Chat.

* https://gitter.im/AirGateway/Lobby