---
title: "Single Provider Requests"
weight: 4
pre: "4 . "
---

All non-AirShopping NDC requests are considered SPR. This means:

- FlightPrice
- SeatAvailability
- OrderCreate
- OrderRetrieve
- OrderChange
- OrderCancel
- ServiceList
- ServicePrice


To execute a SPR you need send a valid standard NDC request including an HTTP header detailing a specific provider like this:
> **AG-Providers:** BA

SPR responses don't have special any special wrapping since only one response is delivered in synchronous mode.

