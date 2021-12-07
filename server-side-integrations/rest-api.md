---
description: >-
  The Ippopay Payments plugin allows you to accept credit card, UPI, Netbanking
  and debit card payments via Ippopay payment gateway.
---

# REST API

{% swagger baseUrl="https://public_key:secret_key@api.ippopay.com" path="/v1/order/create" method="post" summary="Create Order" %}
{% swagger-description %}
Use this api to create your order on Ippopay to use it for initiating transaction. You can get your keys from the api dashboard.
{% endswagger-description %}

{% swagger-parameter in="body" name="notify_url" type="string" %}
Your webhook url
{% endswagger-parameter %}

{% swagger-parameter in="body" name="amount" type="number" %}
The Order amount to be charged in format ##.##
{% endswagger-parameter %}

{% swagger-parameter in="body" name="currency" type="string" %}
The currency to be charged, Defaults to INR.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="payment_modes" type="string" %}
Payment modes to be enabled for this order, Defaults to Credit, Debit Cards, Netbanking and UPI.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="customer" type="object" %}
Information of the customer, if not provided will be prompted on payment page.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
        "success": true,
        "message": "Order created",
        "data": {
            "order": {
            "merchant": {
                "name": "Demo Merchant",
                "id": "TaodSgGa"
            },
            "customer": {
                "phone": {
                "country_code": "91",
                "national_number": "1234567"
                },
                "name": "Test",
                "email": "test@gmail.com"
            },
            "currency": "INR",
            "paymentModes": "cc,db,nb,upi",
            "status": "created",
            "amount": 100.00,
            "order_id": "order_G@nzg3qBq"           
            }
        }
    }

```
{% endswagger-response %}
{% endswagger %}

```javascript
{
        "amount": 100.00,
        "currency": "INR",
        "payment_modes": "cc,dc,nb,upi",
        "notify_url":"YOUR WEBHOOK URL",
        "customer": {
                "name": "Test",
                "email": "test@gmail.com",
                "phone": {
                        "country_code": "91" ,
                        "national_number": "1234567"
                    }
                }
    }
```



{% swagger baseUrl="https://public_key:secret_key@api.ippopay.com" path="/v1/order/ORDER_ID" method="get" summary="Get Order Details" %}
{% swagger-description %}
Use this API to get your order details.
{% endswagger-description %}

{% swagger-response status="200" description="" %}
```
{
        "success": true,
        "message": "Order Details",
        "data": {
            "order": {
            "merchant": {
                "name": "Demo Merchant",
                "id": "TaodSgGa"
            },
            "customer": {
                "phone": {
                "country_code": "91",
                "national_number": "1234567"
                },
                "name": "Test",
                "email": "test@gmail.com"
            },
            "currency": "INR",
            "paymentModes": "cc,db,nb,upi",
            "status": "created",
            "amount": 100.00,
            "order_id": "order_G@nzg3qBq", 
            "payment_url": "https://pay.ippopay.com/order/G@nzg3qBq",
           
            }
        }
    }

```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://public_key:secret_key@api.ippopay.com" path="/v1/order/ORDER_ID/transaction" method="get" summary="Get Transaction Details for Order" %}
{% swagger-description %}
Use this API to get your transaction details for the successful order.
{% endswagger-description %}

{% swagger-response status="200" description="" %}
```
{
    "success":true,
    "message":"Transaction details",
    "data":{
        "transaction":{
            "trans_id":"trans_t2Jca2dVIF",
            "merchant":{
                "name":"Test",
                "id":"MERCHANT_ID"
            },
            "customer":{
                "phone":{
                    "country_code":"+91",
                    "national_number":"9876543210"
                },
                "name":"Test",
                "email":"test@gmail.com"
            },
            "cost":{
                "paid":1,
                "settled":0.98
            },
            "commission":{
                "percentage":1.75,
                "value":0.02,
                "tax":0,
                "total":0.02,
            },
            "tax":{
                "value":0,
                "calculation":"percent"
            },
            "notes":"",
            "is_manual_record":false,
            "manual_recorded_date":"2020-12-08T17:33:11.405Z",
            "is_intl_payment":false,
            "refund_status":"not_requested",
            "status":"success",
            "failure_reason":"",
            "product":"order",
            "settlement_date":"2020-12-10T18:30:00.000Z",
            "gateway":{
                "payment_mode":{
                    "pay_mode":"Debit Card",
                    "pay_mode_id":"dc",
                    "pay_group":"card",
                    "bank_name":"HDFC Bank",
                    "card_number":"405988XXXXXX6908",
                    "card_scheme":"VISA"
                }
            },
            "updatedAt":"2020-12-09T06:59:23.488Z",
            "createdAt":"2020-12-09T06:59:23.488Z",
            "settlement_id":"settl_oVHAVByLh"
        }
    }
}

```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://public_key:secret_key@api.ippopay.com" path="/v1/order/refund/YOUR_ORDER_ID" method="post" summary="Refund Request" %}
{% swagger-description %}
Use this API to refund for your order on Ippopay.
{% endswagger-description %}

{% swagger-parameter in="body" name="refund_amt" type="number" %}
Pass this parameter to do a partial refund. 
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "success": true,
    "message": "Your refund request accepted"
}

```
{% endswagger-response %}
{% endswagger %}

