# Timbot
[![Discord server](https://img.shields.io/discord/411670416269115394?color=%237289da&label=discord%20server&logo=discord)](https://discord.gg/qmtXjrQ)

🤖 **A simple, customizable Discord bot that announces Twitch streams going live (plus a bunch of silly extras).**

![Timbot](https://user-images.githubusercontent.com/6772638/36305243-09930efe-1313-11e8-98b1-fabf0aacde88.JPG)

## Features

 - 📢 Monitor and announce Twitch channels going live with customizable `@mentions`.
 - 🔴 Live stream card that is automatically updated with the stream status, current game and viewership statistics.

## Using the bot

You have two options:

1. You can [invite the instance I'm running](https://discordapp.com/oauth2/authorize?client_id=411670773330345984&scope=bot) to your server for monotonetim's twitch channels (it announces to `#stream-announcements`). This bot may not always be available, and it may do silly extra things sometimes.

2. Or, run your own copy by following the instructions below, and customize it however you want.

## Installation and setup

### Prerequisites

This bot is built on Node.js. If you do not yet have Node installed, download and install the latest LTS version from the official website for your platform:

https://nodejs.org/en/download/

**I recommend Node v10+.**

### Installation

To set up Timbot, download the latest [repository ZIP](https://github.com/roydejong/timbot/archive/master.zip) or clone it using `git`:

    git clone git@github.com:roydejong/timbot.git
    
Once installed, enter the directory and install the dependencies:

    cd timbot
    npm install

### Getting required tokens

Note that you will need to set up some external applications: 

#### Discord bot application
Your Discord bot needs to be registered as an application, and you will need a bot token  (`discord_bot_token` in Timbot config).

Follow [this guide](https://github.com/reactiflux/discord-irc/wiki/Creating-a-discord-bot-&-getting-a-token) for more information.

#### Twitch application
To connect to the Twitch API, you will need to register a new application in the [Twitch Developers Console](https://dev.twitch.tv/console/apps).

You will need to grab the Client ID (`twitch_client_id` in Timbot config).

#### Twitch OAuth token
To make things more complicated, all requests  to the Twitch API need to be authenticated with an OAuth grant generated by your own application.

To begin the authorization flow, you'll need to complete the authorization prompt yourself:
 
```
https://id.twitch.tv/oauth2/authorize?client_id=<YOUR_CLIENT_ID_HERE>&response_type=token&redirect_uri=http://localhost
```

You can grab the `access_token` from the redirect URL in your browser, and store it as `twitch_oauth_token` in Timbot config. 

### Configuration
 
To configure Timbot, copy the included `config-sample.json` to `config.json` and enter or customize the values in the file.

    {
      "discord_bot_token": "<SET_ME>",
      "discord_announce_channel": "stream-announcements",
      "discord_fooduse_channel": "",
      "discord_mentions": {
        "channel_sample_1": "everyone",
        "channel_sample_2": "here"
      },
      "twitch_client_id": "<SET_ME>",
      "twitch_oauth_token": "<SET_ME>",
      "twitch_check_interval_ms": 60000,
      "twitch_channels": "some,channel,names",
    }

### Starting Timbot

Once the application has been configured, start it using `node` from the installation directory:

    node .
  
### Inviting Timbot

Send the following link to the admin of a Discord server to let them invite the Bot:

  `https://discordapp.com/oauth2/authorize?client_id=BOT_CLIENT_ID&scope=bot`
  
Swap `BOT_CLIENT_ID` in the URL above for your Discord app's client id, which you can find in the app details.