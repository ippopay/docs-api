---
description: >-
  The Ippopay Payments plugin allows you to accept credit card, UPI, Netbanking
  and debit card payments via Ippopay payment gateway.
---

# Angular JS

## angular-ippopay

IppoPay Payment Gateway for your Online Business.

### Install

with npm

NPM Package Link : [https://www.npmjs.com/package/angular-ippopay](https://www.npmjs.com/package/angular-ippopay)



```bash
npm install --save angular-ippopay
```

### Usage

IppoPay Payment Gateway uses sensible defaults, so only minimal configuration via props is necessary.

#### Basic configuration

How to do configuration in your Angular Project?

#### Step 1

Add the below script in angular-cli.json or angular.json.

```jsx
  "scripts": [
    "./node_modules/angular-ippopay/index.js"
  ]
```

#### Step 2

In your Typescript file. follow the instructions.

To initialize the IppoPay Payment.

```jsx
//To Declare the Ippopay Payment

declare var Ippopay: any;

// For Success and Error Handlers. You can get the Payment status in the below function, it may be success or error. 

const ippopayHandler = ( function (e) {
  if(e.data.status == 'success'){
        console.log(e.data)
    }
    if(e.data.status == 'failure'){
        console.log(e.data)
    }
});
window.addEventListener('message', ippopayHandler);

//To Initialize the Ippopay Payment

constructor(){
    Ippopay.init();
}
```

To Open the Ippopay Payment Popup. Get the Order ID (ORDER\_ID) from Step 3.

```jsx
Ippopay.open('ORDER_ID','PUBLIC_KEY');
```

To Close the Ippopay Payment Popup

```jsx
Ippopay.close();
```

#### Step 3

Create order from Server side using below API and get the Order id. [Click here](https://docs.ippopay.com/server-side-integrations/rest-api#create-order) to know how to create a order.

#### Step 4

When you click place order button our popup will be loaded so you can use below test card credentials to complete the order.

```jsx
  Card Number 4111 1111 1111 1111
  Expiry 05/20
  CVV 123

  Card Number 4242 4242 4242 4242
  Expiry 05/23
  CVV 123
```

#### Success and Error Handlers

React IppoPay gives you the handlers for Payment status and details.

After Payment done, the below line sends the Payment details and status to ippopayHandler function.

```jsx
window.addEventListener('message', this.ippopayHandler);
```

You can get the Payment status in the below function, it may be success or error.

```jsx
  const ippopayHandler = ( function (e) {
  if(e.data.status == 'success'){
        console.log(e.data)
    }
    if(e.data.status == 'failure'){
        console.log(e.data)
    }
});
```

#### Sample Integration - App.component.ts

```jsx
import { Component, OnInit } from '@angular/core';
import "@angular/compiler";
declare var Ippopay: any;
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent implements OnInit {
  constructor() {
    console.log('Called Constructor');
    Ippopay.init();
  }
  ngOnInit() {
    console.log('Called ngOnInit method');
    const ippopayHandler = ( function (e) {
      if(e.data.status == 'success'){
            console.log(e.data)
        }
        if(e.data.status == 'failure'){
            console.log(e.data)
        }
    });
    window.addEventListener('message', ippopayHandler);
    Ippopay.open('ORDER_ID','PUBLIC_KEY');
  }  
}
```

### Author

This component is written by [IppoPay](https://github.com/ippopay).

### License

IppoPay 2020 © All Rights Reserved. [IppoPay](https://www.ippopay.com)
