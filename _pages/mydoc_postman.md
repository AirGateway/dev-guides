---
title: Postman examples
sidebar: mydoc_sidebar
permalink: postman.html
folder: pages
---

Here you can find some postman examples in a single collection with multiples cases and workflows

---

**Clone the repo**

Please, clone [this repository](https://github.com/AirGateway/postman-json-api) with the collection and two environments: BA and IB. Import files 

![Import files in Postman](../../images/postman-import.png) 

and then edit the collection to modify the variable called `AG-Authorization` with the airgateway`s api-key.

![AG-Authorization variable](../../images/postman-variables.png) 

**Fork the repo**

A different way to do this is to fork the repository in any of your organizations and then import in postman using the _Code repository_ option.

![Import files in Postman using repository](../../images/postman-import-repo.png)

---

**Collection structure**

There are many folders in the collection, each of them with a complete and concrete flow for the different scenarios, the caption for each case is simple:

- ADI: AirDocIssue
- AS: AirShopping
- OP: OfferPrice
- OC: OrderCreate
- OR: OrderRetrieve
- OCancel: OrderCancel
- OReshop: The OrderReshop flow to change the date
- SA: SeatAvailability
- SL: ServiceList

so if a folder is called _AS-OP-SL-OC-OCancel_ is because it runs through all those methods. There are some hidden methods, because they are implicit in the transaction flow, this cases are:

- AirDocIssue: in the ticket issuing flow, before the ADI we have to invoke the OrderReshopReprice in order to check if the price has changed.
- OrderCancel: in order to do the OrderCancel it is mandatory in the most of the airlines call a previous OrderReshopRefund to know the amount to be refunded.
- OrderReshop: in the flow to change the date of a flight there are 3 methods involved: OrderReshop, OrderReshopReprice and OrderChange.
- SeatAvailability and ServiceList *post order*: in the post order scenario after the SA or the SL we need to call to an OrderChange to add the services in the order.

---

**Collection content**

The current list of folders we have in this collection is this:

- AS-OP-OC-OCancel
- AS-OP-OC-ADI-OCancel
- AS-OP-SA-OC-OCancel
- AS-OP-SL-OC-OCancel
- AS-OP-OC-SA-OCancel
- AS-OP-OC-SL-OCancel
- AS-OP-OC-OReshop-OCancel

The SA and the SL can be pre and post order. It is determined by the position relative to the OC method, for example SA-OC would be a SeatAvailability in pre order scenario, while OC-SL would be a ServiceList post order.