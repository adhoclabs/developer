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

__NOTE__: IFTTT will give you a URL that starts with __https__. Change it to __http__ before triggering the event.

12) Send the burner a text, and watch whatever action you created get triggered.

__Zapier__

1) Sign up or Log in to [Zapier](http://zapier.com).

2) Start creating a new Zap by clicking the "Make a Zap" button at the top of your Dashboard.

3) In the box under "Choose a Trigger App", type "webhook" and select "Webhooks by Zapier" as your Trigger.

4) You should see and input box and then two options under "Select Webhooks by Zapier Trigger" - "Retrieve Poll" and "Catch Hook". Select "Catch Hook" and then click the "Save + Continue" button.

5) The next screen you should see is "Set up Webhooks by Zapier Hook." This is optional, and allows you to only look at specific information sent in by Burner. For example, if you only cared about the incoming phone numbers, you'd input "fromNumber". When you're finished, press the "Continue" button. 

6) You should now see "Test Webhooks by Zapier" at the top of this screen and a URL at the bottom (The URL will look like this: https://zapier.com/hooks/catch/1173170/2pm6it/). Input that URL into the "Outgoing Webhook URL" field in the Burner Developer Connection section.

7) Click "Send test request".

8) In Zapier, click "Ok, I did this".

__Note:__ Zapier will say "Looking for the hook, this might take a sec...", and it may take several minutes to recognize the test request.

9) Click the "Continue" button.

10) Under "Choose an Action App", start typing in the name of the app you'd like to connect (for this example, we'll choose Gmail).

11) Under "Select Gmail Action", select "Send Email" (or whatever app and action you are using) and click the "Save + Continue" button.

12) Click the "Connect a New Account" button if your app requires authentication, go through the authentication process, and then click the "Save + Continue" button.

13) In our Gmail example, I will choose an Address to send email to, a Subject line, and enter something in the Body.

14) In all the fields, you should see an icon with a plus sign. If you click this, it will show you options to insert data sent over from Burner. I will choose the Type, From Number, and Payload options to show if it's a text or phone call, who it came from, and what it contains.

15) Click the "Continue" button.

16) Click the "Create + Continue" button to test it, or click the "Skip Test & Continue" button.

17) Under "Ready to turn on your Zap?" click the toggle button to turn on your Zap.

These are just a few tools we use to quickly enable cool functionality on Burner with very little work, and zero code.