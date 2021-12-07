---
description: >-
  The Ippopay Payments plugin allows you to accept credit card, UPI, Netbanking
  and debit card payments via Ippopay payment gateway.
---

# Node JS SDK

## Ippopay Node SDK

&#x20;[![npm](https://camo.githubusercontent.com/b5fcc3731cd6163fe2555dbdc927f454920303d080087d42ec4b170e6a2cabdb/68747470733a2f2f696d672e736869656c64732e696f2f6e706d2f762f6e6f64652d6970706f7061792e7376673f6d61784167653d323539323030303f7374796c653d666c61742d737175617265)](https://www.npmjs.com/package/node-ippopay)

Official nodejs library for [Ippopay API](https://docs.ippopay.com/node-js-sdk).

Check this link for detailed information to inteagrate Ippopay Node JS SDK: [https://docs.ippopay.com/node-js-sdk](https://docs.ippopay.com/node-js-sdk)

### Installation

```bash
npm i node-ippopay
```

### Documentation

Documentation of Ippopay's API is available at [https://docs.ippopay.com/node-js-sdk](https://docs.ippopay.com/node-js-sdk)

#### Basic Usage

Initiate the Ippopay instance with `public_key` & `secret_key`. You can get the keys from the merchant dashboard ([https://app.ippopay.com/settings/api](https://app.ippopay.com/settings/api))

```javascript
const Ippopay = require("node-ippopay");

var ippopay_instance = new Ippopay({
  public_key: 'YOUR_PUBLIC_KEY',
  secret_key: 'YOUR_SECRET_KEY',
});
```

#### Create an Order

```javascript
ippopay_instance.createOrder({
    amount: 10.00, 
    currency: 'INR',
    payment_modes: "cc,dc,nb,upi",
    customer: {
        name: "Test",
        email: "test@gmail.com",
        phone: {
            country_code: "91",
            national_number: "9876543210"
        }
    }
}, function (err, data){
   console.log(data);
});
```

#### Get Transaction Details of Order

```javascript
ippopay_instance.orderTransactionDetails({
    orderId: 'ORDER_ID'
}, function (err, data){
   console.log(data);
});
```

### Author

This component is written by [IppoPay](https://github.com/ippopay).

### License

IppoPay 2021 © All Rights Reserved. [IppoPay](https://www.ippopay.com)
