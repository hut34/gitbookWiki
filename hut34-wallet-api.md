# Hut34 wallet API

## Enable API Access in your account

Prior to using API calls, you need to enable API access in your account.

First, Sign in using your Google account credentials at:

> [https://wallet.hut34.io/](https://wallet.hut34.io/)

![](.gitbook/assets/image%20%2825%29.png)

Next, click on your profile on the top right of your screen and click on API settings.

![](.gitbook/assets/image%20%2818%29.png)

On the next page, click on "Enable API". It's done! You have successfully enables API access in order to use them.

![](.gitbook/assets/image%20%2816%29.png)

{% hint style="info" %}

**Wallet as a service API v.0.0.1**

* API based security applies to all URLs /api/v1/
* Regular OAuth based security applies to all other URLs
* we recommend using other providers to query balances and view transaction history.

## Base URL

All endpoints are served at:

```text
https://walletbeta.hut34.io/api/v1
```

## Authentication

{% hint style="info" %}
**Note:** The API tag on an address does not refer to API access, rather that the address was created using the API.
{% endhint %}

To enable API access, first log in to your wallet, and select ‘API access’ from the top right hand corner of the screen. Record your API key, and ensure all requests contain an ‘Authorization’ request header as follows:

```text
Authorization: Hut34 [APIKEY]
```

For example:

```text
Authorization: Hut34 CKooV3KaDPg6K70H06aF9IgQi7zFCSkO
```

{% hint style="info" %}
**Note:** Authorization header needs to be included in every API calls.
{% endhint %}

## Endpoints   <a id="endpoints"></a>

{% api-method method="get" host="https://wallet.hut34.io/api/v1" path="/addresses" %}
{% api-method-summary %}
/addresses \(GET\)
{% endapi-method-summary %}

{% api-method-description %}
Returns the list of addresses for this user that can be managed via the API i.e. password protected addresses.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
"Hut34 \[API\_KEY\]"
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
  {
    "created": "2018-05-15T15:34:10.938+10:00",
    "updated": "2018-05-15T15:34:10.938+10:00",
    "address": "0x1a7ede45aac5ea993f5d3a5c1c966764d1313740"
  },
  {
    "created": "2018-05-14T11:35:04.142+10:00",
    "updated": "2018-05-14T11:35:04.142+10:00",
    "address": "0xf7b024a32cE0183616ee62bBA00786a71e987390"
  } 
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://wallet.hut34.io/api/v1" path="/addresses" %}
{% api-method-summary %}
/addresses \(POST\)
{% endapi-method-summary %}

{% api-method-description %}
Allows the user to create a new address with the chosen password.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
"Hut34 \[API\_KEY\]"
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="password" type="string" required=true %}
"p4ssword"
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
// RETURNS A NEWLY CREATED ADDRESS DETAILS
// NOTE: this creates a new address with the password you have chosen

{
  "created": "2018-05-15T15:34:10.938+10:00",
  "updated": "2018-05-15T15:34:10.938+10:00",
  "address": "0x1a7ede45aac5ea993f5d3a5c1c966764d1313740"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://wallet.hut34.io/api/v1" path="/addresses/{source address}/send/eth" %}
{% api-method-summary %}
/addresses/{source address}/send/eth
{% endapi-method-summary %}

{% api-method-description %}
Allows the user to send ETH to another address.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
"Hut34 \[API\_KEY\]"
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="password" type="string" required=true %}
"p4ssword"
{% endapi-method-parameter %}

{% api-method-parameter name="to" type="string" required=true %}
"0xADDRESS"
{% endapi-method-parameter %}

{% api-method-parameter name="value" type="string" required=true %}
"100000000", \(note: value is in Wei, nonce is fetched automatically, gas limit is set 21,000.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
​
// returns: Submitted tx hash
{
"transactionHash": "0x6382c86eeb550cfb32eda5bb466ec99208b48a72532b01d8a53d3d2a1fe990f6"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://wallet.hut34.io/api/v1" path="/addresses/{Source address}/send/tokens" %}
{% api-method-summary %}
/addresses/{source address}/send/tokens
{% endapi-method-summary %}

{% api-method-description %}
Allows to send tokens \(other than ETH\) to other addresses.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
"Hut34 \[API\_KEY\]"
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="password" type="string" required=true %}
"p4ssword"
{% endapi-method-parameter %}

{% api-method-parameter name="to" type="string" required=true %}
"0xADDRESS"
{% endapi-method-parameter %}

{% api-method-parameter name="value" type="string" required=true %}
"10000000"
{% endapi-method-parameter %}

{% api-method-parameter name="tokenAddress" type="string" required=true %}
"0xTOKENADDRESS"
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
//Returning submitting tx hash

{
  "password": "p455w0rd",
  "to": "0xADDRESS",
  "tokenAddress": "0xTOKENADDRESS",
  "value": "100000000000000"
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Redirecting   <a id="redirecting"></a>

```text
https://wallet.hut34.io/api/v1/?redirectAddressTo={redirect address}
```

After sign in, this will perform a redirect in the browser to the given address, with the parameter "walletAddress" set to the first address in the wallet.

For example:

```text
https://wallet.hut34.io/api/v1?redirectAddressTo=https://hut34.io
```

will direct you to

```text
https://hut34.io/?walletAddress=0xf7b024a32cE0183616ee62bBA00786a71e987390
```

## Transaction

With the help of this API call, your app will be able to prepare the user to proceed to a payment through the Hut34 Wallet.

{% api-method method="get" host="https://wallet.hut34.io/api/v1" path="/?data={encodedJSON}" %}
{% api-method-summary %}
Prepare for transfer \(GET\)
{% endapi-method-summary %}

{% api-method-description %}
Using the JSON object below and after encoding it in base64, insert the text in a variable called data.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
"Hut34 \[API\_KEY\]"
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="toAddress" type="string" required=true %}
"0xADDRESS"
{% endapi-method-parameter %}

{% api-method-parameter name="amount" type="string" required=true %}
"0.0001"
{% endapi-method-parameter %}

{% api-method-parameter name="redirectOnSuccess" type="string" required=true %}
A string that contains the URL after a successful transaction
{% endapi-method-parameter %}

{% api-method-parameter name="token" type="object" required=false %}
{ "symbol": "ENTRP",  
"decimals":18,  
"address": "0x5BC7e5f0Ab8b2E10D2D0a3F21739FCe62459aeF3"}
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
If no token is mentioned in the JSON object, it will automatically prepare to transfer ETH.
{% endhint %}

### Example of transfer

```javascript
{
  "toAddress": "0x95c8c55bb34e9701a80507c83cf488d5b85166e2",
  "amount": "1",
  "redirectOnSuccess": "https://www.youtube.com/watch?v=SC4xMk98Pdc",
  "token": {
    "symbol": "ENTRP",
    "decimals": 18,
    "address": "0x5BC7e5f0Ab8b2E10D2D0a3F21739FCe62459aeF3"
  }
}
```

After encoding the above JSON object in base64, we find the following link:

```text
https://wallet.hut34.io/?data=ewogICJ0b0FkZHJlc3MiOiAiMHg5NWM4YzU1YmIzNGU5NzAxYTgwNTA3YzgzY2Y0ODhkNWI4NTE2NmUyIiwKICAiYW1vdW50IjogIjEiLAogICJyZWRpcmVjdE9uU3VjY2VzcyI6ICJodHRwczovL3d3dy55b3V0dWJlLmNvbS93YXRjaD92PVNDNHhNazk4UGRjIiwKICAidG9rZW4iOiB7CiAgICAic3ltYm9sIjogIkVOVFJQIiwKICAgICJkZWNpbWFscyI6IDE4LAogICAgImFkZHJlc3MiOiAiMHg1QkM3ZTVmMEFiOGIyRTEwRDJEMGEzRjIxNzM5RkNlNjI0NTlhZUYzIgogIH0KfQ==
```

{% hint style="info" %}
Do not forget to include the Authorization header containing your Hut34 API key.
{% endhint %}

{% api-method method="post" host="https://wallet.hut34.io/api/v1" path="/signOrderHash" %}
{% api-method-summary %}
Sign Order Hash
{% endapi-method-summary %}

{% api-method-description %}
Signs a 0x order.   
  
  
  
WARNING: Signing does not mean that the 0x order is valid. It is merely a mathematical calculation.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
"Hut34 \[API\_KEY\]"
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="walletAddress" type="string" required=true %}
"0x1E1b924fb3f6A66c34731f2Bd62b2FAdb1c07eB1"
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=true %}
"password"
{% endapi-method-parameter %}

{% api-method-parameter name="orderHash" type="string" required=true %}
"0xb299859b6025f2344d8ba704a4c63d362dbe0460076ca57d4d91968782735806"
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
"result": "0x..................."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://wallet.hut34.io/api/v1" path="/fillOrder" %}
{% api-method-summary %}
Fill 0x Order
{% endapi-method-summary %}

{% api-method-description %}
Fill the 0x order included in the body.   
  
The 0x object must be valid and signed.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Hut34 \[API\_KEY\]
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="signedOrder" type="object" required=true %}
Valid 0x order 
{% endapi-method-parameter %}

{% api-method-parameter name="walletAddress" type="string" required=true %}
The address you want to fill the order with 
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=true %}
password of your Hut34 address that you are using
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returns the transaction hash that can be tracked on etherscan.
{% endapi-method-response-example-description %}

```javascript
"result": "0x......"
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://wallet.hu34.io/api/v1" path="/setProxyAllowance" %}
{% api-method-summary %}
Set Proxy Allowance
{% endapi-method-summary %}

{% api-method-description %}
Approve the coin used for this address.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Hut34 \[API\_KEY\]
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="walletAddress" type="string" required=false %}
The address used to approve the coin
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=false %}
The password of the address
{% endapi-method-parameter %}

{% api-method-parameter name="tokenAddress" type="string" required=false %}
The address of the approved coin
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returns the transaction hash that can be tracked on etherscan.
{% endapi-method-response-example-description %}

```javascript
"result": "0x......"
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Disable API Access in your account

If you ever want to disable API calls for your account for any reason, complete the following steps:

First, Log In your Hut34 Wallet using your Google Account credentials.

![](.gitbook/assets/image%20%2825%29.png)

Next, click on your profile, on the top right corner of the page.

![](.gitbook/assets/image%20%2818%29.png)

Finally, click on "Disable API".

![](.gitbook/assets/image%20%2816%29.png)

You have now disabled API access in your wallet.

