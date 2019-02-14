# Front-End HutX Portal API

{% api-method method="post" host="https://portal.hut34.io" path="/orderHash" %}
{% api-method-summary %}
orderHash and Signature
{% endapi-method-summary %}

{% api-method-description %}
Post all variables needed to make a valid 0x object and backend is creating an orderHash and signing it. Returns the valid makerAssetData and takerAssetData, signature and orderHash.  
  
EVERY VARIABLE IS A STRING.  
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="makerUID" type="string" required=false %}
userID from google sign in
{% endapi-method-parameter %}

{% api-method-parameter name="takerAssetAmount" type="string" required=false %}
Anything as it is NOTCOIN
{% endapi-method-parameter %}

{% api-method-parameter name="takerAssetData" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="takerFee" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="salt" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="senderAddress" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="takerAddress" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="exchangeAddress" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="expirationTimeSeconds" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="feeRecipientAddress" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="makerAddress" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="makerAssetAmount" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="makerAssetData" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="makerFee" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
When receiving the response,  I delete the field makerUID and add the orderHash, makerAssetData, takerAssetDdata and signature. here's a hutX Request sent to firestore, including a valid 0x object.
{% endapi-method-response-example-description %}

```javascript
{  
   "orderHash":"0x7b0e8dd18b2600823f838b7c65a0b52fbb1e9165e7b09e4dee8fc0b651e26ffb",
   "dataRequest":"Where can I sell ENTRP ?",
   "makerUID":"RpzFNZmTKpO0Aogi2Bvk9ucKbCP2",
   "orderDetails":{  
      "exchangeAddress":"0x4f833a24e1f95d70f028921e27040ca56e09ab0b",
      "expirationTimeSeconds":"1549554416", // timestamp when the order will be cancelled by itself
      "feeRecipientAddress":"0x89db81c2dc4adaf10a93705b69289d479d576635",
      "makerAddress":"0xd8c820a5011fb0b63947d1719d1b8b5651a9d626",
      "makerAssetAmount":"990000000000000000",
      "makerAssetData":"0xf47261b00000000000000000000000005bc7e5f0ab8b2e10d2d0a3f21739fce62459aef3",
      "makerFee":"0",
      "salt":"1546962416341", // random number, I am using the timestamp in milliseconds, but can use anything random 
      "senderAddress":"0x0000000000000000000000000000000000000000",
      "takerAddress":"0x0000000000000000000000000000000000000000",
      "takerAssetAmount":"1000000000000000000",
      "takerAssetData":"0xf47261b00000000000000000000000000027449bf0887ca3e431d263ffdefb244d95b555",
      "takerFee":"0",
      "orderHash":"0x7b0e8dd18b2600823f838b7c65a0b52fbb1e9165e7b09e4dee8fc0b651e26ffb",
      "signature":"0x1c55c438b1f825fadaa1640a1cb893a45969badb5919d96dfb5ebaf5ecd0f50f6a14058e915b98e402a5a2a6f65bee0d267bcc384bad168fed9abbdc66783ce29703"
   },
   "referenceID":"XndZpdVBCK1WhEfH9c7h"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://portal.hut34.io" path="/createAddress" %}
{% api-method-summary %}
Create an Ethereum Address
{% endapi-method-summary %}

{% api-method-description %}
Creates an address that is linked to the google account. Used to generate order and filling order. In the backend, I  use Hut34 wallet API, but I doubt that it will affect the front-end.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="uid" type="string" required=false %}
user ID from google sign in
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returns the address created.
{% endapi-method-response-example-description %}

```
result = "0x........"
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://portal.hut34.io" path="/deleteRequest" %}
{% api-method-summary %}
Delete Request
{% endapi-method-summary %}

{% api-method-description %}
As a maker, you can delete your request \(delete it from our firestore\) only if the request hasn't been answered yet.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="uid" type="string" required=false %}
userID from google sign in 
{% endapi-method-parameter %}

{% api-method-parameter name="refID" type="string" required=false %}
referenceID of the hutX Request
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
returns success or nothing
{% endapi-method-response-example-description %}

```
result = true when the request has been deleted successfully.
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://portal.hut34.io" path="/users/sendETH" %}
{% api-method-summary %}
Send dust ETH to the account 
{% endapi-method-summary %}

{% api-method-description %}
Funds the account once only to post several requests and getting approved. For portal users only. In the backend, it sends ETH to the address and approves ENTRP. fully automated.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="uid" type="string" required=false %}
userID from google sign in 
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

                if(results === "true" ) {
                    alert("Your account has already been funded once.");
                }

                else {
                    alert("Track the transaction Hash at " + results);
                }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://portal.hut34.io" path="/users/sendENTRP" %}
{% api-method-summary %}
Send 5 ENTRP to ethAddress
{% endapi-method-summary %}

{% api-method-description %}
Fund the address once in ENTRP to generate and fill Order. For portal users only.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="uid" type="string" required=false %}
userID from google sign in 
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

                if(results === "true") {
                    alert("Your account has already been funded once");
                }

                else {
                    alert("Track the transaction Hash at " + results);
                }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

