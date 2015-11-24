### Outbound webhooks in the Burner Developer Connection

The purpose of outbound webhooks for the Burner Developer Connection is to allow more tech-savvy burner users build automation based on content they receive on their burner phone number. The outbound webhook allows forwarding text messages and pictures the Burner number receives - even voicemails left on the phone number to the web url user configures in Developer connection.

For some additional context check out our writeup of the feature [here](http://www.burnerapp.com/blog/2015/11/23/introducing-the-burner-developer-connection).

Burner will post a json message to the url configured in the Developer Connection settings with a POST http method.

Url can be https or http, both are supported by our system.

### Get started

Assuming you configured `https:\\mysite.com\my-powerful-burner-events` url in your Developer Connection settings, burner will make following requests:

For text messages Burner number receives:

> POST https:\\\\mysite.com\my-powerful-burner-events -d '{ "type": "inboundText", "payload": "Hello", "fromNumber": "+12222222222", "toNumber": "+13333333333" }'

For any media (e.g. pictures) the Burner number receives:

> POST https:\\\\mysite.com\my-powerful-burner-events -d '{ "type": "inboundMedia", "payload": "\<picture url\>", "fromNumber": "+12222222222", "toNumber": "+ 13333333333" }'

For voicemails:
> POST https:\\\\mysite.com\my-powerful-burner-events -d '{ "type": "voiceMail", "payload": "\<voice mail url\>", "fromNumber": "+12222222222", "toNumber": "+ 13333333333" }'

### Examples

If you don't want to host your own server to process the outgoing webhooks, there are a bunch of fun things you can do to customize your Burner's behavior without writing a single line of code.

__IFTTT__

1) Sign up or log into your account on [IFTTT](http://ifttt.com).

2) Start creating a new MAKER url by going [here](https://ifttt.com/maker) and click "How to Trigger events."

3) You will see a URL that you can edit an `{event}` for. If you wanted Burner to turn on a light, you could name this event "lights" and your url would look like `https://maker.ifttt.com/trigger/lights/with/key/{your-key}`.

4) Copy that URL and then add behaviors to it by created a new recipe [here](https://ifttt.com/myrecipes/personal/new).

5) Choose a trigger by tapping the "this" button, then search for the channel `Maker`.

6) Tap the "Receive a web request" button.

7) Write the trigger event from step 3 above. In our example, we would write "lights" here.

8) Tap on the big "that" button and search for an action. In our example we searched for the philips hue action. but there are many others you could use. Tap the service you want.

9) Choose the action you want to perform when something happens on your burner. There will most likely be a few options here. We chose "Turn on lights."

10) Follow any additional steps to setup your action, including any authentication.

11) Once the action has been created, paste the URL from step 2 into your Burner's Developer Connection, in the Outgoing webhook field.

12) Send the burner a text, and watch whatever action you created get triggered.

__Zapier__

1) Sign up or Log in to [Zapier](http://zapier.com).

2) Start [creating a new "zap"](https://zapier.com/app/editor).

3) Tap the "choose a trigger" button and find/select `Webhooks by Zapier` as your Trigger, then choose the "Catch hook" trigger.

4) Find an action. We tried Gmail.

5) Choose an action. We chose the "Send email" action for Gmail.

6) Once you have setup your Trigger and Action, tap Continue.

7) Copy and make note of the URL. This will be what you copy into Burner.

8) If you picked an Action that needs authenticate (like Gmail) enter your credentials.

9) Optionally choose a filter. For example, if you only wanted to trigger your action when a certain phone number texts you, you could enter `fromNumber.+12223334444`.

10) Enter any required information in the Match up section and tap continue.

11) Test your webhook by tapping the "test webhooks" button. This will show you a link, which you can use to paste into the Burner Developer Connection section. Send yourself a text message to test out that it's working.

12) Now that we sent a test to zapier, it knows what kind of data you can use to customize your action. Tap on any of the "Insert Fields" buttons to find data from Burner like `fromNumber`. In our example we use `fromNumber` as the subject of our email. This way, whenever the action runs, it will use whatever phone number is texting or calling us as the subject of the new email.

13) Finish up by saving. You can turn your Zap on or off from your [dashboard](https://zapier.com/app/dashboard).

These are just a few tools we use to quickly enable cool functionality on Burner with very little work, and zero code.