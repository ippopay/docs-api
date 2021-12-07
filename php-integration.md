---
description: IppoPay Payment Gateway for your Online Business.
---

# PHP Integration

#### Sample Integration - PHP

```jsx
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>IppoPay</title>
    </head>
    <body>       
        <?php
        $publicKey = 'pk_live_XXXXXXX';
        $secretKey = 'sk_live_XXXXXXXXXXXXXX';
        $data = "{
            \"amount\": 2.00,
            \"currency\": \"INR\",
            \"payment_modes\": \"cc,dc,nb,upi\",
            \"return_url\": \"\",
            \"customer\": {
                \"name\": \"Test\",
                \"email\": \"test@gmail.com\",
                \"phone\": {
                    \"country_code\": \"91\" ,
                    \"national_number\": \"9876543210\"
                }
            }
        }";
        $curl = curl_init();
        curl_setopt_array($curl, array(
        CURLOPT_URL => "https://".$publicKey.":".$secretKey."@api.ippopay.com/v1/order/create",
        CURLOPT_RETURNTRANSFER => true,
        CURLOPT_ENCODING => "",
        CURLOPT_MAXREDIRS => 10,
        CURLOPT_TIMEOUT => 0,
        CURLOPT_FOLLOWLOCATION => true,
        CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
        CURLOPT_CUSTOMREQUEST => "POST",
        CURLOPT_SSL_VERIFYHOST => 0,
        CURLOPT_SSL_VERIFYPEER => 0,
        CURLOPT_POSTFIELDS => $data,
        CURLOPT_HTTPHEADER => array(
            "Content-Type: application/json"
        ),
        ));
        $response = curl_exec($curl);
        $err = curl_error($curl);
        curl_close($curl);  
        if ($err) {
            echo "cURL Error #:" . $err;
        } else {      
            $array = json_decode($response,true);
            $orderId = $array['data']['order']['order_id'];
        }

        ?>
        <script type="text/javascript" src="https://js.ippopay.com/scripts/ippopay.v1.js"></script>
        <script type="text/javascript">
            var order_id;
            var options = {
                "order_id" : "<?php echo $orderId; ?>",
                "public_key" : "<?php echo $publicKey; ?>"
            }
            var ipay = new Ippopay(options);
            ipay.open();
            ippopayHandler(response, function (e) {
                if(e.data.status == 'success'){
                    console.log(e.data);
                }
                if(e.data.status == 'failure'){
                    console.log(e.data);
                }
            });
        </script>
    </body>
</html>
```

### Author

This component is written by [IppoPay](https://github.com/ippopay).

### License

IppoPay 2020 © All Rights Reserved. [IppoPay](https://www.ippopay.com)
