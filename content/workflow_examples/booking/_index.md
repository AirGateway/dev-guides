---
title: "Booking"
weight: 1
pre: "1 . "
---

This is the basic workflow you need to run to buy tickets from any airline.

----

**Regular Booking**

![Regular booking](../../images/bookingregular.png)

1. AirShopping
2. OfferPrice
3. OrderCreate (without Form of Payment)
4. OrderRetrieve
5. AirDocIssue

----

**Booking Workflow with Autoticketing**
![Booking with Autoticketing](../../images/bookingauto.png)

1. AirShopping
2. OfferPrice
3. OrderCreate (with Form of Payment)

----

**Booking with Seats**
![Booking with Seats](../../images/bookingseats.png)

1. AirShopping
2. OfferPrice
3. SeatAvailability
4. OrderCreate (with Form of Payment)

----

*AirShopping*
You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/AirDocIssue_Post) and [an example](https://docs.airgateway.net/?version=latest#2e6c3925-7fc9-4675-a633-4e218762e98d) on how to use this method.

This method receives a "search" with the flights info you want to search (origin, destination, dates...) and you'll receive a list of offers of each of the airlines you send the request to (you can indicate this via headers as [explained here](https://dev-guides.airgateway.net/getting_started/sending_requests_to_our_ndc_api/)).

----

*OfferPrice*
You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/OfferPrice_Post) and [an example](https://docs.airgateway.net/?version=latest#e6a12080-535a-4083-81d3-ece0841aeffd) on how to use this method.

This method receives the id of an offer you want to see detailed (you'll get a list of offer ids in AirShopping) and will return the information the airline gives us for that given offer. Please have in mind that details can be different from an airline to another (some airlines send really exhaustive disclosures while others only send some raw texts, for example). Some airlines don't even implement this method so we'll return the information we have for that offer from AirShopping.

----

***OrderCreate***
You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/OrderCreate_Post) and [an example](https://docs.airgateway.net/?version=latest#57433cd3-b160-4a35-8e7a-a465c8d5b96e) on how to use this method.

This method receives the information about the offer you want to buy and information essential to create the order (passengers info).

You can send payment information here too, but it's not recommended for most of the airlines and usecases. If you send payment information, some airlines will try to auto-issue the tickets immediately, which can lead to errors sometimes (if you have infants in your order, for example, you'll have to wait for confirmation from the airline first).

Sometimes it's needed to add the form of payment because airline doesn't allow order reservation for that offer. For example with Iberia you need to pay when you want to buy tickets for a flight departing today. In vueling paying when creating the order is the default option.

----

***OrderRetrieve***
You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/OrderRetrieve_Post) of this method.

This method receives the ID of the order you want to retrieve and returns all the information attached to that order.

You'll need to call this method if you want to check the status before you go ahead with AirDocIssue, for example.

You'll receive all order details, everything we receive from the airline and some information we store in our databases like disclosures received in the OfferPrice or remarks and comments your agents can add.

----

***AirDocIssue***
You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/AirDocIssue_Post) of this method.

This method will receive the payment method details and the order id you want to pay and get the tickets.

You'll receive all order details, including tickets information, everything we receive from the airline and some information we store in our databases like disclosures received in the OfferPrice or remarks and comments your agents can add.

----

***SeatAvailability***
[This method](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/SeatAvailability_Post) allows you to request available seats in a given offer. When it's done before you book the order (pre-booking) you'll have to add the payment method (and pay) in OrderCreate to succeed (for example with Iberia).

Sometimes even airlines which accept this method will return an error with some offers (not all flights and fares accept seat selection).