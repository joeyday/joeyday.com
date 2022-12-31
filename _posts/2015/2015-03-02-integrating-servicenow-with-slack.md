---
id: 2652
title: 'Integrating ServiceNow with Slack'
date: '2015-03-02T00:41:59+00:00'
author: Joey
layout: post
guid: 'http://joeyday.com/?p=2652'
wps_subtitle:
    - ''
dsq_thread_id:
    - '3559868456'
categories:
    - essay
tags:
    - api
    - integration
    - rest
    - servicenow
    - slack
    - 'web services'
---

![Slack + ServiceNow](http://joeyday.com/wp-content/uploads/2015/03/slack_servicenow.png) One of our teams at work recently started using [Slack](http://www.slack.com "Slack") for all their team communication and approached me about possibly having [ServiceNow](http://www.servicenow.com "ServiceNow") shoot Incident assignment notifications into one of their Slack channels. As it turns out, integrating ServiceNow and Slack is really easy. In this article I’ll show you how to enable the necessary Slack “Incoming Webhooks” integration service as well as give you a ready-to-go ServiceNow Script Include you can use to post messages to Slack from any scripted ServiceNow Business Rule. Finally, I include some examples and ideas for how to use and re-use the Script Include in your own Business Rules.

## Getting access to the Slack API

To get started, you’ll need an endpoint URL for the Slack API to which ServiceNow can send web service calls. To get this URL, from within any Slack channel (either in the Slack app or the Slack website), simply drop down the arrow next to the channel name and select “Add a service integration”. It doesn’t matter which channel you do this in—I’ll show below how you can use this same integration endpoint to post to any channel within the same team.

[![Slack “Add a service integration…”](http://joeyday.com/wp-content/uploads/2015/03/slack-add-service-integration-1024x727.png)](http://joeyday.com/wp-content/uploads/2015/03/slack-add-service-integration.png)

On the next screen, scroll almost all the way to the bottom and click “+Add” next to “Incoming Webhooks”.

[![Slack Choose Incoming Webhooks](http://joeyday.com/wp-content/uploads/2015/03/slack-choose-incoming-webhooks-1024x758.png)](http://joeyday.com/wp-content/uploads/2015/03/slack-choose-incoming-webhooks.png)

Lastly, click “Add Incoming Webhooks Integration”.

[![Slack Incoming Webhooks setup](http://joeyday.com/wp-content/uploads/2015/03/slack-incoming-webhooks-setup-1024x649.png)](http://joeyday.com/wp-content/uploads/2015/03/slack-incoming-webhooks-setup.png)

On the next screen you should see a long web address labeled “Webhook URL”, similar to this:

```
https://hooks.slack.com/services/xxxxxxxxx/xxxxxxxxx/xxxxxxxxxxxxxxxxxxxxxxxx
```

Save this URL someplace safe. I’ll show you where to use it in a bit. Slack doesn’t require any kind of authentication to use this API, so the tokens in this URL essentially *are* your password. Keep it a secret.

## Creating the REST Message in ServiceNow

The first step in ServiceNow is to set up a REST Message. If you’re running Fuji you can actually skip this step and go straight to the Script Include, as the new RESTMessageV2 API in Fuji doesn’t require a REST Message database record. If you’re still on Eureka or want to keep the integration backwards-compatible with earlier releases for any reason, read on.

1. Navigate to **System Web Services** › **Outbound** › **REST Messages** in your ServiceNow instance.
2. Click “New” to create a new REST Message. 
    - Type “Slack” for the name.
    - Click the lock icon to unlock the Endpoint field and type “${endpoint}” there.
    - Type something useful in the Description field if you go for that sort of thing.
3. Right-click in the header and choose “Save” to submit the new record and stay where you are.
4. At the bottom of the newly-saved record, there will be a related list containing REST Message Functions, of which there should be four: “get”, “post”, “put”, and “delete”. Check the box to the left of all these but “post” and use the drop-down at the bottom to delete them. The only one we need to keep here is the “post” function.
5. Click into the “post” function. 
    - Verify the Endpoint here is also set to “${endpoint}” (it should’ve inherited this setting from the parent REST Message).
    - In the Content field, type “${payload}”.
6. Click “Update”.

That’s it, the REST Message and REST Message Function should be ready to go.

## The Script Include

To create the Script Include, follow these steps:

1. Navigate to **System Definition** › **Script Includes** in your ServiceNow instance.
2. Click “New”. 
    - Name the Script Include “SlackMessage”.
    - Give it a description if you want.
    - Copy and paste the script below.
3. Click “Submit”.

Here’s the script itself:  
\[code language=”javascript”\]var SlackMessage = Class.create();

SlackMessage.prototype = {  
 ‘initialize’: function() {  
 if (gs.getProperty(‘slack\_message.default\_icon\_url’) != ”) {  
 this.payload.icon\_url = gs.getProperty(‘slack\_message.default\_icon\_url’);  
 }  
 else if (gs.getProperty(‘slack\_message.default\_icon\_emoji’) != ”) {  
 this.payload.icon\_emoji = gs.getProperty(‘slack\_message.default\_icon\_emoji’);  
 }  
 },

 ‘send’: function (text, channel) {  
 // Set the text and channel (or fall back to defaults)  
 this.payload.text = text || this.payload.text;  
 this.payload.channel = channel || this.payload.channel;

 // Encode the payload as JSON  
 var SNJSON = JSON; // Workaround for JSLint warning about using JSON as a constructor  
 var myjson = new SNJSON();  
 var encoded\_payload = myjson.encode(this.payload);

 // Create and send the REST Message  
 var msg = new RESTMessage(‘Slack’, this.method);  
 msg.setStringParameter(‘endpoint’, this.endpoint);  
 msg.setXMLParameter(‘payload’, encoded\_payload);  
 var res = msg.execute();  
 return res;  
 },

 ‘endpoint’: gs.getProperty(‘slack\_message.default\_endpoint’),  
 ‘method’: ‘post’,  
 ‘payload’: {  
 ‘channel’: gs.getProperty(‘slack\_message.default\_channel’),  
 ‘username’: gs.getProperty(‘slack\_message.default\_username’),  
 ‘text’: ”,  
 ‘attachments’: \[\]  
 },

 ‘type’: ‘SlackMessage’  
};\[/code\]

Now, I said earlier if you’re running Fuji you could skip the step for adding the REST Message. If you did that, you’ll want to find the following block of code in the above script . . .  
\[code language=”javascript” firstline=”23″\]// Create and send the REST Message  
var msg = new RESTMessage(‘Slack’, this.method);  
msg.setStringParameter(‘endpoint’, this.endpoint);  
msg.setXMLParameter(‘payload’, encoded\_payload);  
var res = msg.execute();  
return res;\[/code\]

. . . And replace it with this:  
\[code language=”javascript” firstline=”23″\]// Create and send the REST Message  
var msg = new sn\_ws.RESTMessageV2();  
msg.setEndpoint(this.endpoint);  
msg.setHttpMethod(this.method);  
msg.setRequestBody(encoded\_payload);  
var res = msg.execute();  
return res;\[/code\]

This alternative code instantiates a new RESTMessageV2 object (instead of the older RESTMessage object) and does so without specifying any parameters. One of the neat things about the new version of the Outbound REST API is you don’t have to specify an existing REST Message, but can use the setter methods you see here to set the Endpoint and the HTTP Method, as well as directly set the Content Body of the message, all at runtime. Obviously if there’s a lot of setup (special headers and authentication and such) you may still want to go the former route of declaring the REST Message up front and calling it here, but since the Slack API doesn’t require any of that, being able to do it this way keeps things simple.

## System Properties

You may have noticed the Script Include pulls in a handful of System Properties. I like using System Properties because they allow you to change settings on the fly later without re-deploying code. You can get a list view of all System Properties by typing “sys\_properties.list” in the search box at the top of the left sidebar in ServiceNow. To create a new System Property from there, simply click the “New” button.

You’ll need to declare the following System Properties in your instance for the Script Include above to function properly:

| Name | Value |
|---|---|
| slack\_message.default\_endpoint | Here’s where you should paste that Slack Webhook URL you put in a safe place way back in the first section above. |
| slack\_message.default\_channel | Specify the channel to which you’ll post the majority of your Slack messages, with a leading hash symbol, such as “#general” or “#servicenow”. The Slack API also allows specifying a person’s username preceded by an at symbol to send direct messages instead, such as “@joeyday”. |
| slack\_message.default\_username | This is the display name of the bot that will post the messages. I set mine to “ServiceNow”, but this could be anything you like. |
| slack\_message.default\_icon\_url | Specify a URL of an image to be used as the avatar for your bot, or leave this blank if you want to use an Emoji instead (see the next property). This image can be anywhere on the web or hosted on Slack as long as you’ve shared it to the whole team and not left it private. |
| slack\_message.default\_icon\_emoji | Specify an Emoji code including surrounding colons, such as “:warning:”. Slack uses the same Emoji codes as Campfire and Github, for which there is a very handy [Emoji cheat sheet](http://www.emoji-cheat-sheet.com). This setting will be ignored if you’ve specified an image URL instead (see the previous property). |

I called these all defaults since, as I’ll show below, you can override any or all of them in your individual Business Rules. As a best practice I recommend you rename these to include a company prefix, e.g. **acme.slack\_message.default\_endpoint**. If you do, just don’t forget to modify all the gs.getProperty() calls in the Script Include to match the new names.

## Examples

Here’s how easy it is to send a message into the default channel using this Script Include. In an advanced Business Rule (with conditions specified however you like), just call the send() method on a new SlackMessage object:

\[code language=”javascript”\]var slack = new SlackMessage();  
slack.send(‘Hello World!’);\[/code\]

To send the message to a different channel or as a direct message to an individual, simply specify the channel or user in a second parameter of the send() method:

\[code language=”javascript”\]var slack = new SlackMessage();  
slack.send(‘Hello World!’, ‘#random’);\[/code\]

\[code language=”javascript”\]var slack = new SlackMessage();  
slack.send(‘Hello World!’, ‘@joeyday’);\[/code\]

You can get even more fancy using the payload member variable to override defaults and/or specify additional API options (this is very similar to the Business Rule script I actually wrote for the team I mentioned in the opening paragraph):

\[code language=”javascript”\]// Initialize a new SlackMessage  
var slack = new SlackMessage();

// Set up the payload  
slack.payload.text = ‘An Incident has been assigned to ‘ + current.assignment\_group.name + ‘:’;  
slack.payload.icon\_emoji = ‘:exclamation:’;  
slack.payload.attachments.push({  
 ‘title’: current.number.toString(),  
 ‘title\_link’: ‘https://’ + gs.getProperty(‘instance\_name’) + ‘.service-now.com/nav\_to.do?uri=incident.do?sys\_id=’ + current.sys\_id,  
 ‘text’: current.short\_description.toString()  
});

// Fire off the message  
slack.send();\[/code\]

The above will result in a Slack message looking like this:

[![Slack Message](http://joeyday.com/wp-content/uploads/2015/03/Screenshot-2015-03-01-23.24.23.png)](http://joeyday.com/wp-content/uploads/2015/03/Screenshot-2015-03-01-23.24.23.png)

Don’t miss how you can call the send() method without any parameters as long as you’ve specified useful values in the payload beforehand, and that you may need to use toString() when you set values if you’re not using string concatenation or something else that would implicitly cast the contents of a record field into a string.

There are more options I haven’t gone over here and I encourage you to read up on the Slack [Incoming Webhooks API](https://api.slack.com/incoming-webhooks) for more details. The important thing to notice is that “payload” is a JavaScript object that gets encoded as JSON and sent in as the Request Body of the REST message, so you can declare any option you want from the Incoming Webhooks API as a key/value pair in that payload object and it should work.

I should mention that you can even override the default endpoint if you need to send a message to an entirely different team:

\[code language=”javascript” autolinks=”false”\]var slack = new SlackMessage();  
slack.endpoint = ‘https://hooks.slack.com/services/xxxxxxxxx/xxxxxxxxx/xxxxxxxxxxxxxxxxxxxxxxxx’;  
slack.send(‘Hello World!’, ‘#general’);\[/code\]

Lastly, the send() method returns the server response. If you store that response you can debug by grabbing values out of it as shown below:  
\[code language=”javascript”\]// Send the message  
var slack = new SlackMessage();  
var response = slack.send(‘Hello World!’);

// Show error message if it failed  
if(response.getStatusCode() != 200) {  
 gs.addInfoMessage("response.getBody: " + response.getBody());  
 gs.addInfoMessage("response.getStatusCode: " + response.getStatusCode());  
 gs.addInfoMessage("response.getErrorMessage: " + response.getErrorMessage());  
}\[/code\]

## Ideas

What sorts of things can you do with this? The sky’s the limit really. What I was tasked with doing was simply send a message into a specific channel whenever an Incident was assigned to a specific User Group. By specifying different conditions in your Business Rule, you could send messages only if an Incident is high priority or attached to certain Configuration Items.

One idea I thought of is adding a Slack username field to the sys\_user table and then using that to push a private message whenever a user has a ticket assigned to them, something like:

\[code language=”javascript”\]if (current.assigned\_to.u\_slack\_username != ”) {  
 slack.send(‘Ticket ‘ + current.number + ‘ has been assigned to you!’, ‘@’ + current.assigned\_to.u\_slack\_username);  
}\[/code\]

If you use this Script Include for something interesting, I’d love if you’d leave a comment below or drop me a line on social media. Cheers!{% include endmark.html %}