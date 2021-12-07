---
description: >-
  You can manage beneficiaries with the set of API provided below. You can make
  a transfer request only against an added beneficiary.
---

# Beneficiary

{% swagger baseUrl="https://public_key:secret_key@api.ippopay.com" path="/v1/payout/beneficiary/create" method="post" summary="Create Beneficiary" %}
{% swagger-description %}
Use this api to create a beneficiary on your account to use it for initiating transfer. You can get your keys from the payout api dashboard.
{% endswagger-description %}

{% swagger-parameter in="body" name="acc_number" type="string" %}
Account number of the beneficiary
{% endswagger-parameter %}

{% swagger-parameter in="body" name="ifsc" type="string" %}
IFSC code for the account
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" type="string" %}
Account holder name
{% endswagger-parameter %}

{% swagger-parameter in="body" name="beneficiary_ref" type="string" %}
Unique Reference id for the beneficiary.

\


Accepts only alpha numeric.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "success": true,
    "message": "Beneficiary created Successfully"
}
```
{% endswagger-response %}
{% endswagger %}

```javascript
 {
	"acc_number":"50100012345678",
	"ifsc":"HDFC0000001",
	"name":"Account Holder Name",
	"beneficiary_ref":"reference_id"
}
```

{% swagger baseUrl="https://public_key:secret_key@api.ippopay.com" path="/v1/payout/beneficiary/list" method="get" summary="Beneficiary List" %}
{% swagger-description %}
Use this api to fetch list of beneficiaries on your account. You can get your keys from the payout api dashboard.
{% endswagger-description %}

{% swagger-parameter in="query" name="limit" type="number" %}
Limits the number of records to fetch
{% endswagger-parameter %}

{% swagger-parameter in="query" name="page" type="number" %}
The page number to fetch the list
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "success": true,
    "message": "Beneficiary list",
    "data": {
        "beneficiaries": [
            {
            "account": {
                    "number": "501000000012345678",
                    "ifsc": "HDFC0000001"
                }
                "name": {
                    "first": "",
                    "last": "",
                    "full": "Jaikumar R"
                }
                "status": "active",
                "merchant_id": "XXXXXX",
                "beneficiary_id": "bene_XXXX",
                "beneficiary_ref": "unique_beneficiary_ref",
                "tags": [],
                "updatedAt": "2021-05-11T14:23:05.112Z",
                "createdAt": "2021-05-11T14:23:04.668Z"
            }
        ],
        "total": 1
    }
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://public_key:secret_key@api.ippopay.com" path="/v1/payout/beneficiary/getdetails/{beneficiary_ref}" method="get" summary="Get Beneficiary Details" %}
{% swagger-description %}
Use this api to get a particular beneficiary on your account. You can get your keys from the payout api dashboard.
{% endswagger-description %}

{% swagger-parameter in="path" name="beneficiary_ref" type="string" %}
Reference id of the beneficiary
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "success": true,
    "message": "Beneficiary Detail",
    "data": {
        "beneficiary": 
            {
            "account": {
                    "number": "501000000012345678",
                    "ifsc": "HDFC0000001"
                }
                "name": {
                    "first": "",
                    "last": "",
                    "full": "Jaikumar R"
                }
                "status": "active",
                "merchant_id": "XXXXXX",
                "beneficiary_id": "bene_XXXX",
                "beneficiary_ref": "unique_beneficiary_ref",
                "tags": [],
                "updatedAt": "2021-05-11T14:23:05.112Z",
                "createdAt": "2021-05-11T14:23:04.668Z"
            }
    }
}
```
{% endswagger-response %}
{% endswagger %}
