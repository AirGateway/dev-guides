---
title: "Multi-provider requests"
weight: 3
pre: "3 . "
---

This requests are basically restricted to one single NDC method call (**AirShopping**) since it's the only NDC method that makes sense to be concurrently requested to multiple NDC providers.

To execute a MPR you only need send a valid standard NDC **AirShopping** request including an HTTP header like this:
> **AG-Providers:** *
This is interpreted by the **NDC Gateway** like a send to all available NDC providers for the consumer.

Alternatively, you can define a list of providers using a list of comma-separated standard [IATA airline designators](https://en.wikipedia.org/wiki/List_of_airline_codes).
> **AG-Providers:** BA, AA, LH

**MPR Responses**

Multi-Provider responses

MPRs behave asynchronously when used this HTTP headers:
> **Connection:** keep-alive


MPR response formats:

Our MPR responses (only applies to AirShopping seraches) has two modes: **Streaming** or **Standard HTTP**.

To enabled streaming mode (strongly recommended for GUI Applications) it's required to send the following HTTP header:

 - **AG-Connection**: keep-alive

And optionally, for the streaming mode a timeout in the server-side can be set upon request of the client to set a maximum request lifetime.

 - **Ag-Request-Timeout:** X (where x is an integer number in seconds)

Using this header will let you get all the results received in the first X seconds. For example, if airline 1 returns results in 5 seconds and airline 2 returns results in 10 seconds, if we setup timeout to 6 seconds we'll receive all results from airline 1 but no results from airline 2.


**Important note**

> Please, keep in mind streaming mode responses use a non-standard JSON notation wrapping called [JSON Streaming](https://en.wikipedia.org/wiki/JSON_streaming) used to streamline a collection of valid JSON objects instead of a resulting JSON-valid notation.

