---
title: Chat Window Documentation

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

search: true
---

# Introduction

KMBotUI is a custom chat-window for websites. This chat-window is intended to be used with a automated conversation agents (chatbots). It supports a large variety of rich message formats.

<aside class="notice">
Note: This plug-in can only be used alongside with Kick My Bot products.
</aside>

<i>Here is an example of what can be done on the chat-window with this plugin :</i>

 <div class="row">
  <div class="column">
    <img src="../images/example-Welcome.png"></img>
  </div>
  <div class="column">
    <img src="../images/example-CHAT.png"></img>  
  </div>
  <div class="column">
    <img src="../images/example-FAQ.png"></img>
  </div>
</div> 

<br/>

# Base Setup

## loadScript

```javascript
function loadScript(src, callback) {
  var s,
      r,
      t;
  r = false;
  s = document.createElement('script');
  s.type = 'text/javascript';
  s.src = src;
  s.onload = s.onreadystatechange = function() {
    if ( !r && (!this.readyState || this.readyState == 'complete') )
    {
      r = true;
      callback();
    }
  };
  t = document.getElementsByTagName('script')[0];
  t.parentNode.insertBefore(s, t);
}

loadScript("https://kick-my-bot.s3-eu-west-1.amazonaws.com/KMBotUI_V2/kmbotui.js.gz", function () {  
  var config = {
    serverUrl: <Insert your chatbot server URL here />
  };
  KMBotUI.init(config);
});

```
In your HTML web page, simply add and call the loadScript function written on the right:

This function will load the latest version of the chatbot, without disrupting the loading of the page it is put in. After that, call the loadScript function (see code on the right), and set the callback function as follow. The `config` variable will be where your options are set.

This is the recommended way to implement the script onto your webpage.

<aside class="warning">
Note that two options need to be defined in order for the bot to work properly. Those two options are explained below.
</aside>

<br/>
<br/>

## serverUrl
<u>Type:</u> `String`

```javascript
{
  ...
  serverUrl: "https://my-bot-url.kickmybot.com/",
  ...
}
```

This option corresponds to the chatbot server URL. It is required for the chatbot to work as it will define its behavior.
<aside class="warning">
Required
</aside>


<br/>
<br/>

## projectName
<u>Type:</u> `String`

```javascript
{
  ...
  projectName: "My_Bot_Project",
  ...
}
```

This option corresponds to the name of the project on the back office, which the questions in the FAQ section will be synchronized with. Usually provided by Kick My Bot.
<aside class="warning">
Highly Recommended
</aside>

# Style

## primaryColor
<u>Type:</u> `String`

```javascript
{
  ...
  primaryColor: "#24a6f3",
  ...
}
```

This option sets the main color of the chat window (headers, bot message, bot bubble). The color must be in hexadecimal. 
<aside class="notice">
<b><u>Default:</u></b> `#1abc9c`
</aside>
<br/>


## secondaryColor
<u>Type:</u> `String`

```javascript
{
  ...
  secondaryColor: "#5931bf",
  ...
}
```

This option sets the secondary color of the chat window (quick replies (CTA), buttons). The color must be in hexadecimal. 
<aside class="notice">
<b><u>Default:</u></b> `same as primaryColor`
</aside>
<br/>


## isWhite
<u>Type:</u> `Boolean`

```javascript
{
  ...
  isWhite: true,
  ...
}
```

This option, if set to `true`, will make the close button on the top right of the welcome page white. It will be black if set to `false`. 
<aside class="notice">
<b><u>Default:</u></b> `true`
</aside>
<br/>


## headerBackground
<u>Type:</u> `String`

```javascript
{
  ...
  headerBackground: "https://my-background-url.kickmybot.com/header.png",
  ...
}
```
This option is the URL of the background image you want to put on the header of the welcome page. The standard size is <b>400x250</b>. If no value is set, a <i>primaryColor</i> colored background will be displayed.
<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>


<img style="display: block; margin:auto" src="../images/example-header.png"></img>
<br/>


## height
<u>Type:</u> `Integer`

```javascript
{
  ...
  width: 400,
  ...
}
```

This option sets the width of the main window in pixels.
<aside class="notice">
<b><u>Default:</u></b> `400`
</aside>
<br/>



## width
<u>Type:</u> `Integer`

```javascript
{
  ...
  height: 700,
  ...
}
```

This option sets the height of the main window in pixels.
<aside class="notice">
<b><u>Default:</u></b> `700`
</aside>
<br/>


## bubbleColor
<u>Type:</u> `String`

```javascript
{
  ...
  bubbleColor: "#dedede",
  ...
}
```

This option sets the speech bubble color. This option is only considered if welcomeMessage is set.
<aside class="notice">
<b><u>Default:</u></b> `#8f8f8f`
</aside>
<br/>


# UI

## title
<u>Type:</u> `String`

```javascript
{
  ...
  title: "#dedede",
  ...
}
```

This option sets the text that will be displayed in the chat window header. 
<aside class="notice">
<b><u>Default:</u></b> `Kick My Bot`
</aside>
<br/>


## version
<u>Type:</u> `String`

```javascript
{
  ...
  version: "#dedede",
  ...
}
```

This option sets the chatbot UI version.
<aside class="notice">
<b><u>Default:</u></b> `last version available`
</aside>
<br/>


## botIcon
<u>Type:</u> `String`

```javascript
{
  ...
  botIcon: "https://my-bot-icon-url.kickmybot.com/icon.png",
  ...
}
```

This option sets the main chatbot's image path. You can specify a remote or local image.
<aside class="notice">
<b><u>Default:</u></b> `(displays the Kick My Bot mascot).`
</aside>
<br/>


## welcomeMessage
<u>Type:</u> `String`

```javascript
{
  ...
  welcomeMessage: "Hello, I'm BOT. How may I help you ? 🙂",
  ...
}
```

This option sets the text that will be displayed after some time in the speech bubble when the chat window is closed. Do no set if you don't want this additional feature.
<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>
<br/>


## welcomeLinks
<u>Type:</u> `Array`

```javascript
{
  ...
  welcomeLinks: [
    ...
    {
      type: "facebook",
      url: "https://www.facebook.com/MyFacebookGroup"
    },
    {
      icon: "https://my-custom-website-icon.com/icon.png",
      url: "https://www.my-website.com/"
    },
    ...
  ],
  ...
}
```

This option sets the list of links you want to display on the welcome page. Links are objects with a `type` key and a `url` key (for the link to your desired website).
If you want to use a custom icon, you can replace the `type` key with an `icon` and give your custom icon URL as a value.

Allowed values for the `type` key : <br/>
`facebook`
- `linkedin`
- `twitter`
- `instagram`
- `snapchat`
- `youtube`
- `pinterest`
- `reddit`
- `whatsapp`
- `steam`

<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>
<img style="display: block; margin:auto" src="../images/example-welcome-links.png"></img>
<br/>


## welcomePageText
<u>Type:</u> `String`

```javascript
{
  ...
  welcomePageText: "Hello, <br/> I'm displayed on the <b>Welcome page</b>. <br/>Click on &quot;Start&quot; to start !",
  ...
}
```

This option sets the introducing message you want to display on the welcome page. HTML is supported.
<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>
<img style="display: block; margin:auto" src="../images/example-welcome-page-text.png"></img>

<br/>

## welcomeTimer
<u>Type:</u> `Integer`

```javascript
{
  ...
  welcomeTimer: 10* 1000, // 10 seconds
  ...
}
```

This option sets the time period (in ms) during which the speech bubble (welcome message) is displayed.
<aside class="notice">
<b><u>Default:</u></b> `5000`
</aside>
<br/>


## welcomeDelay
<u>Type:</u> `Integer`

```javascript
{
  ...
  welcomeDelay: 12000, // 12 seconds
  ...
}
```

This option sets the delay (in ms) before displaying the speech bubble (welcome message).
<aside class="notice">
<b><u>Default:</u></b> `10000`
</aside>
<br/>

## redirectionUrl
<u>Type:</u> `String`

```javascript
{
  ...
  redirectionUrl: "http://www.facebook.com/MyBotPage",
  ...
}
```

This option sets the URL of a Facebook Messenger chatbot. This option will display a messenger icon in the chatbox's header.
<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>
<br/>

## displayWelcomePage
<u>Type:</u> `Boolean`

```javascript
{
  ...
  displayWelcomePage: true,
  ...
}
```

This option, if set to `true`, displays a welcome page when a user opens the chatbot.
<aside class="notice">
<b><u>Default:</u></b> `true`
</aside>
<br/>

## tabsConfig
<u>Type:</u> `Object`

```javascript
{
  ...
  tabsConfig: {
    CHAT: {
        title: "Hello, I'm BOT the bot"
    },
    FAQ: {
        title: "Frequently asked questions"
    }
  },
  ...
}
```

This option sets the configuration for each tab with two keys `CHAT` and `FAQ` and within those keys an `object` with a `title` key that will be the title displayed in the chat header for each tab (required). This option overrides the `title` option defined above.
<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>

These pictures show the result of the example configuration for the `CHAT` and `FAQ` tab header respectively :

<img style="display: block; margin:auto" src="../images/example-tabs-config-chat.png"></img>
<br/>

## lang
<u>Type:</u> `String`

```javascript
{
  ...
  lang: "en",
  ...
}
```

This option sets the language used for keywords.
<aside class="notice">
<b><u>Default:</u></b> `fr`
</aside>
<br/>

## hideInput
<u>Type:</u> `String`

```javascript
{
  ...
  hideInput: "false",
  ...
}
```

This option, if set to `true`, will hide the user input at the bottom of the chat window (for quickreply use only, for example).
<aside class="notice">
<b><u>Default:</u></b> `false`
</aside>
<br/>

## enableRecorder
<u>Type:</u> `Boolean`

```javascript
{
  ...
  enableRecorder: true,
  ...
}
```

This option, if set to true, will display a button in the input area ,allowing speech recording and recognition. 
<aside class="notice">
<b><u>Default:</u></b> `true`
</aside>

The picture below shows the <i>microphone</i> icon displayed in the input area when the option is set to `true` :

<img style="display: block; margin:auto" src="../images/example-recorder.png">
</img>
<br/>

## enableMobile
<u>Type:</u> `String`

```javascript
{
  ...
  enableMobile: true,
  ...
}
```

This option, if set to `true`, allows the chatbot to be displayed on mobile devices.
<aside class="notice">
<b><u>Default:</u></b> `true`
</aside>
<br/>

## registrationKey
<u>Type:</u> `String`

```javascript
{
  ...
  registration: "A_Registation_Key",
  ...
}
```

This option, if an authorized key is set, will hide the "Powered By Kick My Bot" block under the input area. You can ask for a valid key by contacting the following address : <a href="mailto:contact@kickmybot.com">contact@kickmybot.com</a>
<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>

<img style="display: block; margin:auto" src="../images/example-poweredBy.png">
<br/>

## menu
<u>Type:</u> `Array`

```javascript
{
  ...
  menu: [
    ...
    {
      type: "postback",
      title: "Relancer 🔃",
      payload: "SOME_POSTBACK"
    },
    ...
  ]
  ...
}
```

This option sets the content for the persitent menu, which following the Facebook Messenger API format (see here: https://developers.facebook.com/docs/messenger-platform/reference/messenger-profile-api/persistent-menu). Usually provided by Kick My Bot.
<aside class="notice">
<b><u>Default:</u></b> `true`
</aside>
<img style="display: block; margin:auto" src="../images/example-menu.png">
</img>
<br/>

## animation
<u>Type:</u> `Boolean`

```javascript
{
  ...
  animation: true,
  ...
}
```

This option, if set to `true`, will make the launcher icon animated (small bounce effect). Set to `false` if you want to turn this effect off. Do not hesitate to define your own CSS animation if you want to.
<aside class="notice">
<b><u>Default:</u></b> `true`
</aside>
<br/>




<!-- 
		"welcomePageText",
		"welcomeTimer",
		"welcomeDelay",
		"redirectionUrl",
		"serverUrl",
		"extraChatOptions",
		"displayWelcomePage",
		"tabsConfig",
		"lang",
		"hideInput",
		"enableRecorder",
		"enableMobile",
		"registrationKey",
		"menu",
		"projectName" -->
# Contact

For all requests/suggestions and support, do not hesitate to contact us at <a href="mailto:contact@kickmybot.com">contact@kickmybot.com</a>

<br/>
<br/>
<br/>
