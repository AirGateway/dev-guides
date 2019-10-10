---
title: Webhooks
weight: 5
pre: ' '
---
We offer some event based services like mails or slack notifications after orders are created, changes in orders or orders are canceled. We can personalize some of these services if needed, but we offer a really versatile service you can use to be notified on every event you want to track: **webhooks**.

We currently track these events:

* OrderCreated
* OrderChanged
* OrderCanceled
* OrderTicketed
* OrderStarted (Time of first flight has passed)
* OrderCompleted (Time of last flight has passed)
* ServicesAddition
* ServicesDeletion
* SeatsAddition
* SeatsDeletion
* DatesChanged

For each of these events, we can call any endpoint you want (we can use the same for all events or we can call a different one for each).

Everytime the selected events are triggered, we'll call your endpoint with a JSON body including the information you need. This is **completely configurable**, we can adapt it to your needs, using any of these fields:

* **agw_id**: Order id in our platform
* **order_id**: Order id from airline
* **pnr**
* **record_locator**
* **booking_type**: One Way, Round Trip or Multicity
* **origin**
* **destination**
* **full_path**: All legs in the order (MAD-LHR, LHR-MAD...)
* **adults_pax**: number of adults
* **children_pax**: number of children
* **infants_pax**: number of infants
* **order_status**: cancelled, on hold...
* **total_amount**
* **created_on**
* **updated_on**
* **session_id**
* **agent_email**: email from the agent that triggered the event
* **consumer_email**: email from the consumer in the order
* **psg_phone**: contact passenger phone
* **psg_email**: contact passenger email
* **consumer_iata_code**
* **consumer_country_code**
* **consumer**: consumer name
* **provider**: provider code
* **agent**: agent name
* **agency**: agency name

For example we can configure a task to call your endpoints on OrderTcketed with this information:

```
{
    "http_request": {
        "url": "https://yourservices/api/order-ticketed",
        "header": {
            "Authorization": "Basic YourPassword"
        },
        "json_body": {
            "agent": "{{agent}}",
            "agency": "{{agency}}",
            "pnr": "{{pnr}}",
            "freeText": "Order has been ticketed, this is your order ID: {{agw_id}}"
        }
    }
}
```
