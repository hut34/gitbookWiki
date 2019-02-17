# hutRelay API

{% api-method method="post" host="https://relay.hut34.io" path="/registerDevice" %}
{% api-method-summary %}
Register a device
{% endapi-method-summary %}

{% api-method-description %}
API allows the user to register a device from the front-end.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="uid" type="string" required=false %}
google account uid given when logging in the relay
{% endapi-method-parameter %}

{% api-method-parameter name="serviceAccount" type="string" required=false %}
serviceAccount created by the device. needs to be an object
{% endapi-method-parameter %}

{% api-method-parameter name="invocation" type="string" required=false %}
invocation of the device without the @
{% endapi-method-parameter %}

{% api-method-parameter name="metatags" type="string" required=false %}
metatags of the device separated by commas
{% endapi-method-parameter %}

{% api-method-parameter name="idToken" type="string" required=false %}
idToken given when logging in to check in the backend if it is the user or not 
{% endapi-method-parameter %}

{% api-method-parameter name="botname" type="string" required=false %}
Name of the device
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returns the dialogFlowAPI that I have created for that bot. Need to be used when talking to another bot \(and necessary when generating and filling order in the backend\)
{% endapi-method-response-example-description %}

```
alert("You have successfully registered your device. The Fallback Intent of your bot is: https://relay.hut34.io/api/v1/talktothehut/" + result);
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
returns "invocation already exists" if the invocation already exists. Does not return anything if a problem occurs.
{% endapi-method-response-example-description %}

```
else if (result === "Invocation already exists") {
                  alert("Invocation already exists. Please try again.");
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://relay.hut34.io" path="/updateDevice" %}
{% api-method-summary %}
Update a device 
{% endapi-method-summary %}

{% api-method-description %}
Usually on the front end, most of the variables are already available by fetching it from firestore. only botname and metatags can be changed for now. Post the data in the backend and backend only returns state \(success or nothing\).
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="botname" type="string" required=false %}
changeable 
{% endapi-method-parameter %}

{% api-method-parameter name="serviceAccount" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="invocation" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="metatags" type="string" required=false %}
changeable
{% endapi-method-parameter %}

{% api-method-parameter name="idToken" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="uid" type="string" required=false %}
user ID when logging in with google 
{% endapi-method-parameter %}

{% api-method-parameter name="refID" type="string" required=false %}
referenceID of the device on firestore
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returns success
{% endapi-method-response-example-description %}

```
if(status === "success") {
                  alert("Your device has been updated successfully.");
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
              else {
                  alert("A problem has occured. Please try again.");
              }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://relay.hut34.io" path="/devices/sendENTRP" %}
{% api-method-summary %}
send ENTRP to the device 
{% endapi-method-summary %}

{% api-method-description %}
Funds the account in the backend by sending the info needed. Can only be funded ENTRP once. All data are fetched from firestore when displaying their bots/devices. Only for devices on Relay.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="ethAddress" type="string" required=false %}
The ethAddress of the device found from firestore using the invocation.
{% endapi-method-parameter %}

{% api-method-parameter name="uid" type="string" required=false %}
user ID from google sign in 
{% endapi-method-parameter %}

{% api-method-parameter name="refID" type="string" required=false %}
referenceID of the device from firestore
{% endapi-method-parameter %}

{% api-method-parameter name="invocation" type="string" required=false %}
device's invocation
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
returns "true" \(string\) when the device has already been funded. Returns the transaction hash if it is successful.
{% endapi-method-response-example-description %}

```
  if(result === "true") {
      alert("Your device has already been funded once.");
  }
  else {
      alert("tx hash:" + result);
  }
                      
                      
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://relay.hut34.io" path="/devices/sendETH" %}
{% api-method-summary %}
Send some dust ETH to a device
{% endapi-method-summary %}

{% api-method-description %}
Can only be done once. Same concept as the API above but with ETH for the device to fillOrder and approve ENTRP. Only for devices on relay.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="uid" type="string" required=false %}
userID from google sign in
{% endapi-method-parameter %}

{% api-method-parameter name="ethAddress" type="string" required=false %}
ethAddress from firestore of the device
{% endapi-method-parameter %}

{% api-method-parameter name="invocation" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="refID" type="string" required=false %}
referenceID from firestore
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
                  if(result === "true") {
                      alert("Your device has already been funded once.");

                  }
                  else {

                      alert("Follow your transaction at "+ result);
                  }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}





