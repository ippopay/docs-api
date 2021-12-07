# Transfers

{% swagger baseUrl="https://public_key:secret_key@api.ippopay.com" path="/v1/payout/transfer/request" method="post" summary="Transfer Request" %}
{% swagger-description %}
Use this api to initiate a transfer to your added beneficiary. You can get your keys from the payout api dashboard.
{% endswagger-description %}

{% swagger-parameter in="body" name="amount" type="number" %}
10.00
{% endswagger-parameter %}

{% swagger-parameter in="body" name="trans_ref" type="string" %}
Unique Transfer Reference id for the Transfer.

\


Accepts only alpha numeric.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="beneficiary_ref" type="string" %}
Reference id of the created beneficiary.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="remarks" type="string" %}
Transaction remarks.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="pay_mode" type="string" %}
Payment modes to be used for this transaction, Defaults to NEFT.

\


Available modes: "NEFT", "IMPS", "RTGS"

\


IMPS: Transactions value up to INR 200000

\


RTGS: Transaction value above INR 200000
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "success": true,
    "message": "Payout Accepted",
    "data": {
        "transfer": {
            "commission": {
                "value": 4,
                "total": 4
            },
            "status": "accepted",
            "merchant_id": "TaodSgGa",
            "trans_id": "trans_VRm7frCeE",
            "trans_ref": "test24",
            "beneficiary": {
                "account": {
                    "number": "50100035304529",
                    "ifsc": "HDFC0000674"
                }
                "beneficiary_id": "bene_0sWxgFdY@",
                "beneficiary_ref": "jaikumarr"
            },
            "pay_mode": "IMPS",
            "amount": 1,
            "total_deduction": 5,
            "product_type": "payout",
            "trans_type": "DEBIT",
            "init_source": "api",
            "remarks": "Testing",
            "updatedAt": "2021-05-11T14:59:07.594Z",
            "createdAt": "2021-05-11T14:59:07.594Z"
            
        }
    }
}
```
{% endswagger-response %}
{% endswagger %}

```javascript
 {
	"amount":10.00,
	"trans_ref":"xxxxx",
	"pay_mode":"NEFT",
	"remarks":"Testing",
	"beneficiary_ref":"xxxxx"
}
```

{% swagger baseUrl="https://public_key:secret_key@api.ippopay.com" path="/v1/payout/transfer/detail?trans_ref=xxxx" method="get" summary="Transfer Details" %}
{% swagger-description %}
Use this api to get the status of  a transfer. You can get your keys from the payout api dashboard.
{% endswagger-description %}

{% swagger-parameter in="query" name="trans_ref" type="string" %}
Unique transfer id used to initiate the transaction.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "success": true,
    "message": "Payout Accepted",
    "data": {
        "transfer": {
            "commission": {
                "value": 4,
                "total": 4
            },
            "status": "accepted",
            "merchant_id": "TaodSgGa",
            "trans_id": "trans_VRm7frCeE",
            "trans_ref": "test24",
            "beneficiary": {
                "account": {
                    "number": "50100035304529",
                    "ifsc": "HDFC0000674"
                }
                "beneficiary_id": "bene_0sWxgFdY@",
                "beneficiary_ref": "jaikumarr"
            },
            "pay_mode": "IMPS",
            "amount": 1,
            "total_deduction": 5,
            "product_type": "payout",
            "trans_type": "DEBIT",
            "init_source": "api",
            "remarks": "Testing",
            "updatedAt": "2021-05-11T14:59:07.594Z",
            "createdAt": "2021-05-11T14:59:07.594Z"
            
        }
    }
}
```
{% endswagger-response %}
{% endswagger %}
