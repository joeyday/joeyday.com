---
id: 2747
title: 'Integrating ServiceNow with HipChat'
date: '2015-05-18T23:18:51+00:00'
author: Joey
layout: post
guid: 'http://joeyday.com/?p=2747'
wps_subtitle:
    - ''
dsq_thread_id:
    - '3775786953'
categories:
    - essay
tags:
    - api
    - hipchat
    - integration
    - rest
    - servicenow
    - 'web services'
---

My tutorial on integrating \[ServiceNow\] with \[Slack\] turned out to be one of my most popular articles ever. Justin Meader recently asked me on Twitter how easy it would be to integrate Service­Now with \[HipChat\] instead.

> [@joeyday](https://twitter.com/joeyday) Hey Joey, I found your article on integrating Slack with Service­Now, and it's very helpful.
> 
> — Justin Meader (@justinmeader) [May 13, 2015](https://twitter.com/justinmeader/status/598566238835597312)

 <script async="" charset="utf-8" src="//platform.twitter.com/widgets.js"></script>

> [@joeyday](https://twitter.com/joeyday) We're a HipChat shop, and I was wondering how difficult it would be to adapt the include script for HipChat? I'm not a coder sadly.
> 
> — Justin Meader (@justinmeader) [May 13, 2015](https://twitter.com/justinmeader/status/598566367793684480)

 <script async="" charset="utf-8" src="//platform.twitter.com/widgets.js"></script>

So, I gave it a whirl. In this article I’ll show you how you can post Service­Now notifications right into HipChat using their API. Just like in the previous tutorial, I’ll give you a ready-made Service­Now Script Include and instructions and examples for how you can call that Script Include from any scripted Business Rule.

## Getting access to the HipChat API

To get started, you’ll need an endpoint URL for the HipChat API to which Service­Now can send web service calls. To get this URL, go to HipChat’s [Integrations](https://www.hipchat.com/integrations "HipChat Integrations") page:

[![HipChat Integrations Page](/wp-content/uploads/2015/05/hipchat-1-1024x720.png)](/wp-content/uploads/2015/05/hipchat-1.png)

Scroll to the bottom and click “Set Up An Integration”:

[![HipChat Set Up An Integration](/wp-content/uploads/2015/05/hipchat-2-1024x616.png)](/wp-content/uploads/2015/05/hipchat-2.png)

If you’re not already logged you may be asked to do so, then click the “Create” button under “Build Your Own!”:

[![HipChat Build Your Own Integration](/wp-content/uploads/2015/05/hipchat-3-1024x637.png)](/wp-content/uploads/2015/05/hipchat-3.png)

On the next screen, choose the room you want to use and the name of the bot as you’d like it to appear whenever it posts, then click “Create”:

[![HipChat Choose the Room and Name Your Integration Bot](/wp-content/uploads/2015/05/hipchat-4-1024x635.png)](/wp-content/uploads/2015/05/hipchat-4.png)

On the next screen, you should see a URL like the below:

```
https://api.hipchat.com/v2/room/xxxxxxx/notification?auth_token=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

Save this URL someplace safe. I’ll show you where to use it in a bit. HipChat doesn’t require any kind of authentication to use this API, so the token in this URL essentially *is* your password. Keep it a secret.

## Creating the REST Message in ServiceNow

The first step in Service­Now is to set up a REST Message. If you’re running Fuji you can actually skip this step and go straight to the Script Include, as the new RESTMessageV2 API in Fuji doesn’t require a REST Message database record. If you’re still on Eureka or want to keep the integration backwards-compatible with earlier releases for any reason, read on.

1. Navigate to **System Web Services** › **Outbound** › **REST Messages** in your Service­Now instance.
2. Click “New” to create a new REST Message. 
    - Type “HipChat” for the name.
    - Click the lock icon to unlock the Endpoint field and type “${endpoint}” there.
    - Type something useful in the Description field if you go for that sort of thing.
3. Right-click in the header and choose “Save” to submit the new record and stay where you are.
4. At the bottom of the newly-saved record, there will be a related list containing REST Message Functions, of which there should be four: “get”, “post”, “put”, and “delete”. Check the box to the left of all these but “post” and use the drop-down at the bottom to delete them. The only one we need to keep here is the “post” function.
5. Click into the “post” function. 
    - Verify the Endpoint here is also set to “${endpoint}” (it should’ve inherited this setting from the parent REST Message).
    - Insert an HTTP Header row Name “Content-Type” and Value “application/json”.
    - In the Content field, type “${payload}”.
6. Click “Update”.

That’s it, the REST Message and REST Message Function should be ready to go.

## The Script Include

To create the Script Include, follow these steps:

1. Navigate to **System Definition** › **Script Includes** in your Service­Now instance.
2. Click “New”. 
    - Name the Script Include “HipChatNotification”.
    - Give it a description if you want.
    - Copy and paste the script below.
3. Click “Submit”.

Here’s the script itself:  
\[code language=”javascript”\]var HipChatNotification = Class.create();

HipChatNotification.prototype = {  
 ‘initialize’: function() {},

 ‘send’: function (message, endpoint) {  
 // Set the text and channel (or fall back to defaults)  
 this.payload.message = message || this.payload.message;  
 this.endpoint = endpoint || this.endpoint;

 // Encode the payload as JSON  
 var SNJSON = JSON; // Workaround for JSLint warning about using JSON as a constructor  
 var myjson = new SNJSON();  
 var encoded\_payload = myjson.encode(this.payload);

 // Create and send the REST Message  
 var msg = new RESTMessage(‘HipChat’, this.method);  
 msg.setStringParameter(‘endpoint’, this.endpoint);  
 msg.setXMLParameter(‘payload’, encoded\_payload);  
 var res = msg.execute();  
 return res;  
 },

 ‘endpoint’ : gs.getProperty(‘hipchat\_notification.default\_endpoint’),  
 ‘method’ : ‘post’,  
 ‘payload’ : {  
 ‘color’ : gs.getProperty(‘hipchat\_notification.default\_color’),  
 ‘message’ : ”,  
 ‘message\_format’ : ‘html’,  
 ‘notify’ : false  
 },

 ‘type’: ‘HipChatNotification’  
};\[/code\]

Now, I said earlier if you’re running Fuji you could skip the step for adding the REST Message. If you did that, you’ll want to find the following block of code in the above script . . .  
\[code language=”javascript”\]// Create and send the REST Message  
var msg = new RESTMessage(‘HipChat’, this.method);  
msg.setStringParameter(‘endpoint’, this.endpoint);  
msg.setXMLParameter(‘payload’, encoded\_payload);  
var res = msg.execute();  
return res;\[/code\]

. . . And replace it with this:  
\[code language=”javascript”\]// Create and send the REST Message  
var msg = new sn\_ws.RESTMessageV2();  
msg.setEndpoint(this.endpoint);  
msg.setHttpMethod(this.method);  
msg.setRequestHeader(‘Content-Type’, ‘application/json’);  
msg.setRequestBody(encoded\_payload);  
var res = msg.execute();  
return res;\[/code\]

This alternative code instantiates a new RESTMessageV2 object (instead of the older RESTMessage object) and does so without specifying any parameters. One of the neat things about the new version of the Outbound REST API is you don’t have to specify an existing REST Message, but can use the setter methods you see here to set the Endpoint and the HTTP Method, as well as directly set the Content Body of the message, all at runtime. Obviously if there’s a lot of setup (special headers and authentication and such) you may still want to go the former route of declaring the REST Message up front and calling it here, but since using the HipChat API doesn’t require a lot of complicated setup, being able to do it this way keeps things simple.

## System Properties

You may have noticed the Script Include pulls in a couple of System Properties. I like using System Properties because they allow you to change settings on the fly later without re-deploying code. You can get a list view of all System Properties by typing “sys\_properties.list” in the search box at the top of the left sidebar in Service­Now. To create a new System Property from there, simply click the “New” button.

You’ll need to declare the following System Properties in your instance for the Script Include above to function properly:

| Name | Value |
|---|---|
| hipchat\_notification.default\_endpoint | Here’s where you should paste that URL you put in a safe place way back in the first section above. |
| hipchat\_notification.default\_color | Specify the color you’d like all HipChat notifications to be by default. You can choose from yellow, green, red, purple, gray, or random. |

I called these both defaults since, as I’ll show below, you can override either or both of them in your individual Business Rules. As a best practice I recommend you rename these to include a company prefix, e.g. **acme.hipchat\_notification.default\_endpoint**. If you do, just don’t forget to modify each of the gs.getProperty() calls in the Script Include to match the new names.

## Examples

Here’s how easy it is to send a notification to the default endpoint using this Script Include. In an advanced Business Rule (with conditions specified however you like), just call the send() method on a new HipChatNotification object:

\[code language=”javascript”\]var hipchat = new HipChatNotification();  
hipchat.send(‘Hello World!’);\[/code\]

To send the notification someplace other than the default room, simply create another integration for that room and specify the alternate endpoint URL as a second parameter of the send() method:

\[code language=”javascript”\]var hipchat = new HipChatNotification();  
hipchat.send(‘Hello World!’, ‘https://api.hipchat.com/v2/room/xxxxxxx/notification?auth\_token=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx’);\[/code\]

Note that the message itself can include HTML. Here’s a more realistic example how you might notify a room when an Incident has been assigned to a particular assignment group:

\[code language=”javascript”\]// Initialize a new HipChatNotification  
var hipchat = new HipChatNotification();

// Set up the payload  
hipchat.payload.message = ‘An Incident has been assigned to ‘ + current.assignment\_group.name + ‘: &lt;a href="https://’ + gs.getProperty(‘instance\_name’) + ‘.service-now.com/nav\_to.do?uri=incident.do?sys\_id=’ + current.sys\_id + ‘"&gt;’ + current.number + ‘&lt;/a&gt; ‘ + current.short\_description;  
hipchat.payload.color = ‘red’;

// Fire off the message  
var response = hipchat.send();\[/code\]

The above will result in a Slack notification looking like this:

[![HipChat Notification](/wp-content/uploads/2015/05/hipchat-notification-1024x99.png)](/wp-content/uploads/2015/05/hipchat-notification.png)

Don’t miss how you can call the send() method without any parameters as long as you’ve specified useful values for the payload beforehand, and be aware you may need to use toString() when you set values if you’re not using string concatenation or something else that would implicitly cast the contents of a record field into a string.

Lastly, note that the send() method returns the server response. If you store that response you can debug by grabbing values out of it as shown below:  
\[code language=”javascript”\]// Send the notification  
var hipchat = new HipChatNotification();  
var response = hipchat.send(‘Hello World!’);

// Show error message if it failed  
if(response.getStatusCode() != 200) {  
 gs.addInfoMessage("response.getBody: " + response.getBody());  
 gs.addInfoMessage("response.getStatusCode: " + response.getStatusCode());  
 gs.addInfoMessage("response.getErrorMessage: " + response.getErrorMessage());  
}\[/code\]

## Conclusion

So, what can you use this for? The sky’s the limit really. You can set up a Business Rule to fire on any condition you want and send any HTML message into any HipChat room. Use it as above to notify any given team when they have a new assignment. Use it to notify management when there’s a P1 incident. If you find a creative use for this Script Include, I’d love if you’d leave a comment below or drop me a line on social media. Cheers!\[endmark\]