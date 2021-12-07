# Account

{% swagger baseUrl="https://public_key:secret_key@api.ippopay.com" path="/v1/payout/account/balance" method="get" summary="Get Balance" %}
{% swagger-description %}
Use this api to fetch available balance on your account. You can get your keys from the payout  dashboard.
{% endswagger-description %}

{% swagger-response status="200" description="" %}
```
{
    "success": true,
    "message": "Account Details",
    "data": {
        "account": {
            "available_balance": "47.50"
        }
    }
}
```
{% endswagger-response %}
{% endswagger %}
