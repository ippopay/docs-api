---
description: >-
  The Ippopay Payments plugin allows you to accept credit card, UPI, Netbanking
  and debit card payments via Ippopay payment gateway.
---

# Javascript Integration

## Configuration

Initialize your object by passing your order id and public key:

> Get Order Id from Create order api from next step

```javascript
<script type="text/javascript" src="https://js.ippopay.com/scripts/ippopay.v1.js"></script>
<script type="text/javascript">
var order_id;
var options = {
    "order_id" : order_id, //Get order_id params value from Create Order from next step
    "public_key" : "pk_live_xxxxxxxxx"
}
var ipay = new Ippopay(options);
```

You can get your Public and Secret key from the api [dashboard](https://app.ippopay.com/settings/api).

## Create Order

Create order from Server side using below API and get the Order id. [Click here](https://docs.ippopay.com/server-side-integrations/rest-api#create-order) to know how to create a order.

## Open the payment view

Use the below code to open the payment view for the customers to pay.

```javascript
ipay.open();
```

## Close the payment view

Use the below code to close the payment view.

```javascript
ipay.close();
```

## Response Handlers

For Success and Error handlers use the below handler function for payment response

```javascript
ippopayHandler(response, function (e) {
    if(e.data.status == 'success'){
        console.log(e.data)
    }
    if(e.data.status == 'failure'){
        console.log(e.data)
    }
});

```
