# Approova Discord Bot

[![Build Status](https://travis-ci.com/alex4108/Approova.svg?branch=master)](https://travis-ci.com/alex4108/Approova)
[![GitHub issues](https://img.shields.io/github/issues/alex4108/Approova)](https://github.com/alex4108/Approova/issues)
[![GitHub forks](https://img.shields.io/github/forks/alex4108/Approova)](https://github.com/alex4108/Approova/network)
[![GitHub stars](https://img.shields.io/github/stars/alex4108/Approova)](https://github.com/alex4108/Approova/stargazers)
![GitHub contributors](https://img.shields.io/github/contributors/alex4108/Approova)
[![GitHub license](https://img.shields.io/github/license/alex4108/Approova)](https://github.com/alex4108/Approova/blob/master/LICENSE)
![GitHub All Releases](https://img.shields.io/github/downloads/alex4108/Approova/total)
![Docker Pulls](https://img.shields.io/docker/pulls/alex4108/approova)
[![Discord](https://img.shields.io/discord/742969076623605830)](https://discord.gg/FpDjFEQ)

[![Join Us in Discord](https://user-images.githubusercontent.com/7796475/89976812-2628c080-dc2f-11ea-92a1-fe87b6a9cf92.jpg)](https://discord.gg/FpDjFEQ)
## Purpose

Let existing users of a Discord guild approve new joins

Did I save you some time?  [Buy me a :coffee::smile:](https://venmo.com/alex-schittko)

# Bot workflow 

1. User joins Discord guild
1. Approvals Team will be messaged via Approvals Channel
1. A member of the approvals team will confirm their approval
1. The user who joined will be given the public role

# Configure the bot

_Bot will listen with prefix * and will only listen to the Guild owner!__

1. [Join the bot to your server](https://discord.com/api/oauth2/authorize?client_id=743249218491121695&permissions=268635200&scope=bot)
1. Run the following commands in any text channel Approova can see, **as the guild owner**
1. `*setApproverChannel <name of channel>` to set the text channel where Approvers will receive requests.
1. `*setApproverRole <name of role>` to set the role required to approve a request.
1. `*setPublicChannel <name of channel>` to set the public room that Approova will talk to new members in.
1. `*setPublicRole <name of role>` to set the public role to assign after approval.
1. Move `Approova` role to top of roles list in Discord Guild Settings

At this point, Approova will monitor for new joins to the Guild and execute the flow as outlined above.

# Running in Development

* Create a Discord Bot Token as outlined in the [Production Notes](#Production-Notes) section.

## First Time Setup

`virtualenv env && source env/bin/activate && pip install -r requirements.txt`

## Returning to an existing project

Be sure to activate the virtalenv, and set needed environment variables

```
source env/bin/activate
export APPROOVA_DISCORD_TOKEN=9999
export APPROOVA_DB_PATH=$(pwd)/sqlite.db
python src/bot.py
```

# Running in Production

## From Online Sources

You should install [Docker Compose](https://docs.docker.com/compose/install/) if you haven't already.

Then, modify the docker-compose.yml to include your Discord Bot Token.  

Finally, run: `docker-compose up -d`

In production, the application will default to using `/content` to store the sqlite database.

## From Local Sources

Replace `image: alex4108/approova` with `build: .` in the docker-compose.yml file.

Replace the `9999` Discord Bot Token with your own

Run: `docker-compose up -d`

## Production Notes

* [This guide](https://www.writebots.com/discord-bot-token/) seems to have a good write up on how to generate a bot token.
* Note that during the creation of the bot, you will need to enable the "Server Members Intent" flag on the Bot page in the Discord developers portal.
* Once you have the token in step 5, replace "9999" in the `docker-compose.yml` file with your bot's token.
* Finally, craft your authorization URL.  You can copy the authorization URL from the Discord developers portal as mentioned in step 5.  
* Once the authorization URL is copied, replace the permissions integer with that from the URL given above to join the public bot to your server.
* You should now be able to visit your authorization URL and join your own bot to your Discord guild.



# Contributing

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request
