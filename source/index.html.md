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
Note: This plug-in can only be used alongside with KMB Labs products.
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


# CASE 1: Linked configuration

```javascript

  var config = {
    projectKey: your_project_key
  };

```
In most cases, your window's configuration will be handled by the KMB Labs team. <br/>
They will provide you with a `projectKey` that can be used to display your chat window with a setting built for your website. You can set it inside the `config` object.
<br/> It is however possbile for you to set up a custom configuration. Refer to <b>CASE 2</b> for more details.
<br/>
<br/>

# CASE 2: Custom configuration

If you want to have a custom configuration, you can change it directly inside the config object. <br/>
The options available for customization are explained in the different sections below.

# Required

## serverUrl
<u>Type:</u> `String`

```javascript
{
  ...
  serverUrl: "https://my-bot-url.kmblabs.com/",
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

This option corresponds to the name of the project on the back office, which the questions in the FAQ section will be synchronized with. Usually provided by KMB Labs.
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

## windowBackgroundColor
<u>Type:</u> `String`

```javascript
{
  ...
  windowBackgroundColor: "#f1f1f1",
  ...
}
```

This option sets the background color of the message list and the welcome page of the chat window in windowed mode only. The color must be in hexadecimal. 
<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>
<br/>

## windowBackgroundImage
<u>Type:</u> `String`

```javascript
{
  ...
  windowBackgroundImage: "https://the-url-to-your-image.image/image.png",
  ...
}
```

This option sets the background image of the message list and the welcome page of the chat window in windowed mode only. 
<aside class="notice">
<b><u>Default:</u></b> `default star image`
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
  headerBackground: "https://my-background-url.kmblabs.com/header.png",
  ...
}
```
This option is the URL of the background image you want to put on the header of the welcome page. The standard size is <b>400x250</b>. If no value is set, a <i>primaryColor</i> colored background will be displayed.
<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>


<img style="display: block; margin:auto" src="../images/example-header.png"></img>
<br/>


## width
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



## height
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

## analytics
<u>Type:</u> `Object`

```javascript
{
  ...
  analytics: {
      quickreplies: function(title) {
         console.log(title);
    },
      items: function(title) {
         console.log(title);
    }
    },
  ...
}
```

This option can contain two keys : `quickreplies` and `items`. These two keys are user-defined functions that run when the user clicks on a quickreply or an item in a carousel (cards). The functions take the title of the selected element as a parameter. The analytics can be used to perform analytics actions.
<aside class="notice">
<b><u>Default:</u></b> `null`
</aside>
<br/>

## lightMode (BETA)
<u>Type:</u> `boolean`

```javascript
{
  ...
  lightMode: true,
  ...
}
```

This option, if sets to `true`, activates the light mode in fullscreen mode, which sets text font to black, and adds a black background to each message.<aside class="notice">
<b><u>Default:</u></b> `false`
</aside>

<img style="display: block; margin:auto" src="../images/example-lightMode.png"></img>
<br/>
<br/>
<br/>

# UI

## title
<u>Type:</u> `String`

```javascript
{
  ...
  title: "Hello, I'm BOT the bot",
  ...
}
```

This option sets the text that will be displayed in the chat window header. 
<aside class="notice">
<b><u>Default:</u></b> `KMB Labs`
</aside>
<br/>


## version
<u>Type:</u> `String`

```javascript
{
  ...
  version: "V4_a",
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
  botIcon: "https://my-bot-icon-url.kmblabs.com/icon.png",
  ...
}
```

This option sets the main chatbot's image path. You can specify a remote or local image.
<aside class="notice">
<b><u>Default:</u></b> `(displays the KMB Labs mascot)`
</aside>
<br/>

## bubbleIcon
<u>Type:</u> `String`

```javascript
{
  ...
  bubbleIcon: "https://my-bubble-icon-url.kmblabs.com/icon.png",
  ...
}
```

This option sets the image to appears in the chat bubble when the window is closed. You can specify a remote or local image.

<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>

<img style="display: block; margin:auto" src="../images/example-bubbleIcon.png"></img>
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
      url: "https://www.facebook.com/MyFacebookGroup",
      displayInHeader: true
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

This option sets the list of links you want to display on the welcome page and at the top left in fullscreen mode. Links are objects with a `type` key and a `url` key (for the link to your desired website).
If you want to use a custom icon, you can replace the `type` key with an `icon` and give your custom icon URL as a value.
<br/>You can optionally add a `displayInHeader` key with a boolean value. If set to `true`, the icon will also appear in the header in windowed mode.

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
<br/>
<br/>
6 links is the maximum for an optimal responsive behavior.


<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>
<img style="display: block; margin:auto" src="../images/example-welcome-links.png"></img>
<br/>


## welcomeConfig
<u>Type:</u> `Object`

```javascript
{
  ...
  welcomeConfig: {
    welcomeTitle: "Hello, <br/> I'm displayed on the <b>Welcome page</b> and the <b>FullScreen intro message</b>.",
    welcomeSubtitle: "Click on &quot;Start&quot; to start !"
  }, 
  ...
}
```

This option is an object that sets the introducing message you want to display on the welcome page. On the windowed version, the `welcomeTitle` and the `welcomeSubtitle` will be displayed. If no `welcomeSubtitle` is set, a default message will be displayed ('Cliquez sur le bouton "Démarrer" pour commencer à discuter avec moi !') On the full screen version, only the `welcomeTitle` will be displayed as an introductive message to the conversation. HTML is supported.
<aside class="notice">
<b><u>Default:</u></b> `{
    welcomeTitle: "Hello",
    welcomeSubtitle: ""
  }`
</aside>

These pictures show respectively the result of the configuration example on the windowed welcome page and on the full screen introductive message.

<img style="display: block; margin:auto" src="../images/example-welcome-page-text.png"></img>
<br/>
<img style="display: block; margin:auto" src="../images/docs-fullscreen-welcome.png"></img>

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

This option, if an authorized key is set, will hide the "Powered By KMB Labs" block under the input area. You can ask for a valid key by contacting the following address : <a href="mailto:contact@kickmybot.com">contact@kickmybot.com</a>
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

This option sets the content for the persitent menu, which following the Facebook Messenger API format (see here: https://developers.facebook.com/docs/messenger-platform/reference/messenger-profile-api/persistent-menu). Usually provided by KMB Labs.
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

## welcomeWithCv
<u>Type:</u> `Boolean`

```javascript
{
  ...
  welcomeWithCv: true,
  ...
}
```

This option, if set to `true`, will make it available to send a CV through the welcome page. It can be used by dragging and dropping your file inside the dropzone.
<aside class="notice">
<b><u>Default:</u></b> `false`
</aside>

## forceWelcomeWithCv
<u>Type:</u> `Boolean`

```javascript
{
  ...
  forceWelcomeWithCv: true,
  ...
}
```

This option, if set to `true`, will only put the dropzone inside the welcome page, and remove the "Start" button. The only way to start the conversation would be to drag and drop a CV inside the dropzone of the welcome page.
<aside class="notice">
<b><u>Default:</u></b> `false`
</aside>

# Full Screen

```javascript
{
  ...
  fullScreen: {
    enableFullScreen: true,
    forceFullScreen: false,
    background: {
      main: {
        outside:"#000",
        middle:"#113862",
        inside:"#4498ff"
      },
      waves: {
        top: "#53b4fb",
        bottom: "#3c6477"
      }
    }
  },
  ...
}
```
In order to set the configuration for the full screen mode, a `fullScreen` key must be added

<u>Type:</u> `Object`

Here is the result of the example full screen configuration : 

<img style="display: block; margin:auto" src="../images/example-fullscreen.png"></img>
<br/>

## enableFullScreen
<u>Type:</u> `Boolean`

```javascript
{
    ...
  fullScreen: {
    ...
    enableFullScreen: true,
    ...
  }
}
```

This option, if set to true, will enable full screen mode and all of its options for your chatbot. Full screen can only be enabled with a valid `registrationKey` (provided by KMB Labs)
<aside class="notice">
<b><u>Default:</u></b> `true`
</aside>

## forceFullScreen
<u>Type:</u> `Boolean`

```javascript
{
    ...
  fullScreen: {
    ...
    forceFullScreen: false,
    ...
  }
}
```

This option, if set to true, will disable windowed mode for the chatbot, and it will only be available in full screen mode.
<aside class="notice">
<b><u>Default:</u></b> `false`
</aside>

## webpageMode
<u>Type:</u> `Boolean`

```javascript
{
    ...
  fullScreen: {
    ...
    webpageMode: true,
    ...
  }
}
```

This option, if set to true, will set the chatbot in webpage mode, meaning that full screen mode will be active all the time, and the conversation will immediately starts.
<aside class="notice">
<b><u>Default:</u></b> `false`
</aside>

## staticWaves
<u>Type:</u> `Boolean`

```javascript
{
    ...
  fullScreen: {
    ...
    staticWaves: true,
    ...
  }
}
```

This option, if set to true, will disable the animation of the waves in full screen mode.
<aside class="notice">
<b><u>Default:</u></b> `false`
</aside>

## buttonBackgroundColor
<u>Type:</u> `String`

```javascript
{
    ...
  fullScreen: {
    ...
		buttonBackgroundColor: "#24a6f3",
    ...
  }
}
```

This option sets the background color of the buttons in full screen mode.
<aside class="notice">
<b><u>Default:</u></b> `#1abc9c`
</aside>

## background
<u>Type:</u> `Object`

```javascript
{
    ...
  fullScreen: {
    ...
    background: {
      main: {
        outside:"#000",
        middle:"#113862",
        inside:"#4498ff"
      },
      waves: {
        top: "#53b4fb",
        bottom: "#3c6477"
      }
    }
    ...
  }
  ...
}
```

`background` is an object that sets the color parameters or the full screen background. Two objects are defined inside to set the colors :
<br/>
<br/>
- `main` is an object with 3 keys `inside`, `middle` and `outside` that will set the colors of the background, which is a 3-color radial gradient. `inside` sets the inner-circle color. `middle` sets the middle circle color, which is the most dominant color. `outside` sets the outside-circle color, on the borders.
<br/>
<br/>
- `waves` is an object with 2 keys `top` and `bottom` that will set the colors of the bottom waves, are a 2-color linear gradient from top to bottom. `top` / `bottom` sets the color of the top/bottom gradient.
<aside class="notice">
<b><u>Default:</u></b> `{
				main: {
					outside: "#2c5b93",
					middle: "#113862",
					inside: "#0f4c81"
				},
				waves: {
					top: "#53b4fb",
					bottom: "#3c6477"
				}
			}`
</aside>

These pictures show the result of the example configuration for the `background` :

<img style="display: block; margin:auto" src="../images/docs-fullscreen.png"></img>

<br/>

# Page Customization

```javascript
{
  ...
  pageCustomization: [
    ...
    {
      matchPath:"commercial",
      idGetter: "commercial/offer/(.*?)/infos",
      bubbleText:"<b>Welcome !</b><br/> I see you are
      interested by our commercial offer. What
      do you want to do ?",
      bubbleButtonColor:"#0f4c81",
      bubbleDelay: 1000,
      bubbleTimer: 20000,
      fastQR: [
        {
          type: "postback_bubble",
          title:"I want to apply",
          payload:"HOW_TO_APPLY_POSTBACK"
        },
        {
          type: "postback_bubble",
          title:"I want more information",
          payload:"FAQ_${id}_POSTBACK"
        }
      ]
    },
    ...
  ],
  ...
}
```
In order to customize the window depending on the page it is on, a `pageCustomization` key can be added.

<u>Type:</u> `Array of Objects`

Here is the result of the example pageCustomization configuration on a fictive page www.kmblabs.com/commercial/offer/541/infos : 

<img style="display: block; margin:auto" src="../images/example-pageCustomization.png"></img>
<br/>

## matchPath
<u>Type:</u> `String`

```javascript
{
    ...
  pageCustomization: {
    ...
    matchPath: "commercial",
    ...
  }
}
```

This option corresponds to the page in which the customization is applied. The value can be a substring or a regex that matches the URL of the page.
<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>

## idGetter
<u>Type:</u> `String`

```javascript
{
    ...
  pageCustomization: {
    ...
    idGetter: "commercial/offer/(.*?)/infos",
    ...
  }
}
```

This option is a regex to retrieve an ID inside the URL in order to set a custom postback for the chatbot's answer.
<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>

## bubbleText
<u>Type:</u> `String`

```javascript
{
    ...
  pageCustomization: {
    ...
    bubbleText: "<b>Welcome on kmblabs.com !
    What are you looking for ?</b>",
    ...
  }
}
```

This option sets the text displayed inside the speech bubble.
<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>

## bubbleButtonColor
<u>Type:</u> `String`

```javascript
{
    ...
  pageCustomization: {
    ...
    bubbleButtonColor: "#0f4c81",
    ...
  }
}
```

This option sets the color of the speech bubble buttons (for fast QRs).
<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>

## bubbleDelay
<u>Type:</u> `String`

```javascript
{
    ...
  pageCustomization: {
    ...
    bubbleDelay: 1000,
    ...
  }
}
```

This option sets the time after which the speech bubble will appear.
<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>

## bubbleTimer
<u>Type:</u> `String`

```javascript
{
    ...
  pageCustomization: {
    ...
    bubbleTimer: 20000,
    ...
  }
}
```

This option sets the time after which the speech bubble will disappear.
<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>


## fastQR
<u>Type:</u> `Array`

```javascript
{
    ...
  pageCustomization: {
    ...
    fastQR: [
      ...
      {
        type: "postback_bubble",
        title:"I want to apply",
        payload:"HOW_TO_APPLY_POSTBACK"
      },
      ...
    ]
    ...
  }
  ...
}
```

`fastQR` is an array that allows to customize the buttons under the speech bubble. It has 3 keys :
<br/>
<br/>
- `type` is a string that sets the type of the button. Typically, it is set as `postback_bubble` and it will send a message in the conversation, by displaying the `title` as the message (with a `payload` if set).
<br/>
<br/>
- `title` is a string that sets the text on the button. It also is the message displayed in the conversation when clicked.
<br/>
<br/>
- `payload` is a string that sets the payload sent to the server with the message.

<aside class="notice">
<b><u>Default:</u></b> `none`
</aside>
<br/>
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
