###How to flash the lights when you get a new text

This recipe uses Burner’s Developer Connection and IFTTT to take an outgoing webhook from Burner and 
trigger an action on another service, in this case Philips Hue lights.

1) First, make sure IFTTT is connected to your Hue.  Visit https://ifttt.com/hue and click “Connect channel,”
which will ask you to log in and give Hue permission to talk to IFTTT.

2) Then, activate the Maker Channel on IFTTT.  (Maker Channel is what they call their webhooks channel.)  
Visit https://ifttt.com/maker and click “Connect channel”, which simply turns it on.

3) On that page, click on the link that says “How to trigger events”.  You should see a screen like the below.
(You’ll have your own unique secret key and url.)

![IFTTT](https://github.com/adhoclabs/developer/blob/master/examples/assets/blink-lights-1.png?raw=true)

4) In the box that the arrow is pointing to, type in whatever you want to call your event, replacing the 
placeholder text “{event}”.  For this event, we are going to use “lights”.

5) Highlight and copy the whole url, and then send it to yourself so you can paste it on your mobile phone.

6) Open Burner and go to the “Settings” page for any active Burner number.  Select “Developer Connection” 
and click the button to activate it.

7) In the box labelled “Outgoing Webhook URL”, paste the webhook URL from IFTTT.  It will look like this.
Once you hit “done” and go back, every text, voicemail, or picture you get will tell Burner to go hit this
webhook URL on IFTTT.

![IFTTT](https://github.com/adhoclabs/developer/blob/master/examples/assets/blink-lights-2.png?raw=true)

8) You’re not actually done yet - that will send the “lights” command to IFTTT, but we haven’t told them 
what to do with it.  The last step is to make a new recipe that does exactly this.  Go to Create a Recipe, 
and click “this”.

9) Look for and select “Maker” as the trigger channel. 

10) There’s only one kind of trigger to choose, “Receive a web request”.  Choose it.

11) In the Event Name field, put your event name (e.g. “lights”) and hit “create trigger”. You’ve now created 
the “if this” part of the IFTTT recipe.

![IFTTT](https://github.com/adhoclabs/developer/blob/master/examples/assets/blink-lights-3.png?raw=true)

12) Now click “that” and search for and select Hue.  As you can see there are lots of options for the action
you want to create.  Choose any one you like.  (We’re using “blink lights”.)  You’ll also get to pick
which lights you want to blink (e.g. “all lights”).

![IFTTT](https://github.com/adhoclabs/developer/blob/master/examples/assets/blink-lights-4.png?raw=true)

13) That’s it!  Your summary recipe page should look something like this.  You can edit it at any time to 
change things (e.g. which lights flash).

14) Send yourself a text and watch the lights flash!
