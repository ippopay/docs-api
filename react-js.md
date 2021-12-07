---
description: >-
  The Ippopay Payments plugin allows you to accept credit card, UPI, Netbanking
  and debit card payments via Ippopay payment gateway in your React JS.
---

# React JS

## react-ippopay

IppoPay Payment Gateway for your Online Business.

### Install

with npm

NPM Package Link : [https://www.npmjs.com/package/react-ippopay](https://www.npmjs.com/package/react-ippopay)

```bash
npm install --save react-ippopay
```

### Usage

IppoPay Payment Gateway uses sensible defaults, so only minimal configuration via props is necessary.

#### Basic configuration

How to do configuration in your React Project?

#### Step 1

Initialize the Ippopay Payment like below.

```jsx
import {Ippopay} from 'react-ippopay';

class App extends Component {
  state = {
    ippopayOpen: false,
    order_id:'YOUR_ORDER_ID',
    public_key:'YOUR_PUBLIC_KEY'
  };
  ippopayHandler(e){
    if(e.data.status == 'success'){
        console.log(e.data)
    }
    if(e.data.status == 'failure'){
        console.log(e.data)
    }
  }
  componentDidUpdate(){
    window.addEventListener('message', this.ippopayHandler);
  }
  ippopayOpen(){
    this.setState({ippopayOpen: true});
  }
  render() {
    return (
      <div>
        <span onClick={e => this.ippopayOpen(e)}>IppoPay</span>
        <Ippopay ippopayOpen={this.state.ippopayOpen} ippopayClose={true} order_id={this.state.order_id} public_key={this.state.public_key}
          />
      </div> 
    );
  }
}
```

#### Step 2

Create order from Server side using below API and get the Order id. [Click here](https://docs.ippopay.com/server-side-integrations/rest-api#create-order) to know how to create a order.

#### Step 3

When you click place order button our popup will be loaded so you can use below test card credentials to complete the order.

```jsx
  Card Number 4111 1111 1111 1111
  Expiry 05/20
  CVV 123

  Card Number 4242 4242 4242 4242
  Expiry 05/23
  CVV 123
```

#### Props

React IppoPay default props to provide a dynamic experience to open a payment widget and allow user to make a payment via Credit/Debit Card.

* `ippopayOpen` - Boolean - toggles the popup open state (see above example)
* `ippopayClose` - Boolean - Enables the popup close option state (see above example)
* `order_id` - String - sets the Order ID as order\_id state&#x20;
* `public_key` - String - sets your Public Key as public\_key state (Check your API Settings in IppoPay Merchant Panel to know the Public Key)

#### Success and Error Handlers

React IppoPay gives you the handlers for Payment status and details.

After Payment done, the below line sends the Payment details and status to ippopayHandler function.

```jsx
window.addEventListener('message', this.ippopayHandler);
```

You can get the Payment status in the below function, it may be success or error.

```jsx
  ippopayHandler(e){
    if(e.data.status == 'success'){
        console.log(e.data)
    }
    if(e.data.status == 'failure'){
        console.log(e.data)
    }
  }
```

### Author

This component is written by [IppoPay](https://github.com/ippopay).

### License

IppoPay 2020 © All Rights Reserved. [IppoPay](https://www.ippopay.com)
