---
title: "Servicing"
weight: 2
pre: "2 . "
---

In some orders, you might be interested in adding new services like seats, ancillaries or even change your orders. These are the basic workflows you can use for that.

----

**Booking Cancelation**

![Booking Cancelation](../../images/bookingcancelation.png)

1. OrderRetrieve
2. OrderReshopRefund
3. OrderCancel

----

**Add Services to Booking**

![Add Services to Booking](../../images/bookingaddservices.png)

1. OrderRetrieve
2. ServiceList
3. OrderChange

----


**Add Seats to Booking**

![Add Seats to Booking](../../images/bookingaddseats.png)

1. OrderRetrieve
2. SeatAvailability
3. OrderChange

----

**Change Booking Dates**

![Change Booking Dates](../../images/bookingdateschange.png)

1. OrderRetrieve
2. OrderReshop
3. OrderReshopReprice
4. OrderChange

----

***OrderRetrieve***
You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/OrderRetrieve_Post) of this method.

This method receives the ID of the order you want to retrieve and returns all the information attached to that order.

You'll need to call this method if you want to check the status before you go ahead with AirDocIssue, for example.

You'll receive all order details, everything we receive from the airline and some information we store in our databases like disclosures received in the OfferPrice or remarks and comments your agents can add.

----

***OrderReshop***
You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/OrderReshop_Post) of this method.

This method receives the ID of the order you want to retrieve some more info like "when" do you want to flight instead.

The response will include all the offers that match that new search, it's a kind of new *AirShopping*.

----

***OrderReshopReprice***
You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/OrderReshopReprice_Post) of this method.

It's more or less like OrderPrice in Reshop. You'll receive details about an offer to change your current order.

----

***OrderChange***

You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/OrderChange_Post) of this method.

This method is called to "save changes" after a change (like OrderReshop, adding seats or services). You'll need to send different information depending on the action you're performing (you'll need to send the ReshopOffferID if you're changing dates but you'll have to send Services if you're adding services, for example), as long as other general data like form of payment and so on.

You'll receive a response with the Order details like after OrderCreate.

----


***SeatAvailability***
[This method](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/SeatAvailability_Post) allows you to request available seats in a given offer. When it's done before you book the order (pre-booking) you'll have to add the payment method (and pay) in OrderCreate to succeed (for example with Iberia).

Sometimes even airlines which accept this method will return an error with some offers (not all flights and fares accept seat selection).

----

***ServiceList***
You can see [the docs](https://api.airgateway.net/v1.1/swagger-ui/#!/NDC_Methods/ServiceList_Post) of this method.

This service receives information about the passengers so the airlines can know what Services are available depending on the type of passenger (age) and returns a list of services with description, prices, taxes...