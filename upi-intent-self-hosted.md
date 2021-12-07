---
description: >-
  UPI Intent enables users to have a smooth experience of UPI payments on Mobile
  devices. Users can able to pay via any UPI PSP Apps on their devices.
---

# UPI Intent (Self Hosted)

This Self Hosted UPI Intent flow enabled users to have a seamless experience on UPI Intents without having to integrate our SDK.&#x20;

{% swagger baseUrl="https://public_key:secret_key@api.ippopay.com" path="/v1/order/{ORDER ID}/process" method="post" summary="GET URI for UPI Intent" %}
{% swagger-description %}
Use this API to fetch URI for the UPI Intent
{% endswagger-description %}

{% swagger-parameter in="body" name="Name" type="string" %}
Name of the customer
{% endswagger-parameter %}

{% swagger-parameter in="body" name="email" type="string" %}
Email id of the customer
{% endswagger-parameter %}

{% swagger-parameter in="body" name="phone" type="string" %}
Phone number of the customer
{% endswagger-parameter %}

{% swagger-parameter in="body" name="pay_mode_id" type="string" %}
upi-intent
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
  "success": true,
  "message": "Opening UPI Apps...",
  "data": {
    "pay_process": {
      "action": "intent",
      "redirect_data": {
        "data": {
          "upi_intent": "upi://pay?pa=ippopaypg@yesbank&pn=Ippopay&mc=7399&tr=ORDER_XXX&tn=IppopayPG&am=1439.6"
        }
      }
    }
  }
}
```
{% endswagger-response %}
{% endswagger %}
