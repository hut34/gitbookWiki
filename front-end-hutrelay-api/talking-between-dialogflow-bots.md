# Talking between Dialogflow bots

In order enable bot-bot interaction, you will need to fund your device. 

After registering your device on [hutRelay](https://relay.hut34.io), log in and click on "My Devices" at the top of the page.

![](../.gitbook/assets/image%20%2811%29.png)

In the "My Devices" page, you will see all the bots that you have registered. 

![](../.gitbook/assets/image%20%286%29.png)

Click first on "FUND DUST ETH" and wait until completed. An option to track the transaction will be given to you. Copy and paste the transaction hash to etherscan to track Tx progress. 

Once complete, now click on "FUND ENTRP", which will send you 5 ENTRP.

## 1. Bots with no webhook 

This section is recommended for Dialogflow bots with no webhooks. 

Before starting, you will need to:

* [Register](https://docs.hut34.io/wiki/front-end-hutrelay-api/dialogflow-connection-to-hutrelay) your device on [hutRelay](https://relay.hut34.io)
* [Fund ](talking-between-dialogflow-bots.md)your device with ETH and ENTRP
* Have no webhooks on Dialogflow

To get started, click on "My Devices" on [hutRelay](https://relay.hut34.io). You will see that your device will have a DialogFlow API created by the hut.

Copy that API and insert it in that link:

```text
https://relay.hut34.io/api/v1/talktothehut/{dialogflowAPI}
```

Now, go to your dialogflow bot and click on fullfillment. Paste the link above in the webhook section.

![](../.gitbook/assets/image%20%287%29.png)

Save and click on intents. In "Default Intent Fallback", delete all the responses and enable webhook call for this intent at the bottom of the page. 

![](../.gitbook/assets/image%20%284%29.png)

Now, every question that your dialogflow cant' answer will be relayed to the hut and answered by another DialogFlow bot connected to the hut.

Specific bots can answer your query by using direct invocation, e.g:

```text
@tourdefrance who is Lance Armstrong ?
@cryptoPrice what is the price of ETH ?
```

