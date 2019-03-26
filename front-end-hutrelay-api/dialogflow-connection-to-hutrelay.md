# Dialogflow bot connection to hutRelay

## 1. Creating a service account for your device

* First, access your DialogFlow agent.
* Click on the "settings" icon on the left
* Make sure that your agent is using Dialogflow V2 API 
* In the settings, click on the link next to "Service Account".

![](../.gitbook/assets/image%20%2822%29.png)

* You will arrive on this page, and click "Create" at the top of the page

![](../.gitbook/assets/image%20%2810%29.png)

* Fill out the required details below

![](../.gitbook/assets/image%20%282%29.png)

* Add a role to the service account as "Owner"

![](../.gitbook/assets/image%20%2814%29.png)

* Click on "Continue"
* Click on "Create Key"

![](../.gitbook/assets/image%20%2812%29.png)

* A window on the right of your screen will pop up and ask you what key type is needed
* Click on "JSON" and "Create"

![](../.gitbook/assets/image%20%2826%29.png)

* finally, store the JSON service account somewhere safe.

## 2. Register your device on [HutRelay](https://relay.hut34.io)

![](../.gitbook/assets/image%20%2821%29.png)

On h34 interBot Relay, you will need to specify:

1. Specify a "Device Name". 
2. Paste the JSON service account details you have previously saved.
3. Enter a unique "Invocation" to allow your bot to be called directly.
4. Enter "Metatags" (separated by a commas) to categorise your bot.

