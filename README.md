# OldCordV3
Current code for OldCord (Rewritten) as typescript sucks for this kinda project.

# Credits
ziad - token generation, permissions, and some middleware references <br>
noia - everything else <br>
discord.js - snowflake <br>

# Setup
Download and setup a postgreSQL server with the database name of your choice.
Create a config.json file in the root directory, with the example contents:

```js
{
    "token_secret": "35c8...",
    "gateway": "",
    "use_wss": false,
    "base_url": "127.0.0.1",
    "local_deploy": true,
    "use_same_port": true,
    "port": 1337,
    "cache404s": false,
    "serveSelector": true,
    "gateway_has_no_port": false,
    "instance_name": "Staging",
    "instance_description": "An oldcord v3 instance",
    "instance_flags": [
        "NO_FLAGS"
    ],
    "acknowledge_heartbeat_acks" : false,
    "cert_path": "",
    "key_path": "",
    "ws_port": 0,
    "db_config" : {
        "host": "localhost",
        "port": 5433,
        "database": "database_name",
        "user": "postgres_username",
        "password": "postgres_password"
    },
    "trusted_users" : [
        "1270287666822275072"
    ]
}
```
Run npm install and then node server.js to start Oldcord.

Since V3 is hosted on my own server at home, I use cloudflared to bypass CG-NAT and have enabled cloudflare's free SSL so the SSL stuff in the earlier configuration is kinda deprecated.

Trusted_users bypass short term rate-limits, use these to add specific users like bots from being blocked by the wacky rate-limits scattered across the project.
Instance_flags are kinda limited at the moment, but you can lock down an instance with these entries:

NO_REGISTRATION - Block all future users from creating an account on your instance.
NO_GUILD_CREATION - Block future guilds from being created.
NO_INVITE_USE - Block invites from being used.

More are to come with instance flags in the future. 

# Long term goals of this project
- Support 2015, 2016, 2017, 2018 and 2019 fully. Not supporting 2020 as its the year discord was no longer old imo.
- Allow for users to create guilds for specific years - where the maximum support on the backend for channels, messages, invites, etc is only limited to what was available for that year.
- This will stop users from 2017 coming into 2015 servers spamming custom emojis or whatnot - as the requests will be rejected by the backend and the gateway will not dispatch any events for it.

# Community
We also have a discord server! You can join it here: https://discord.gg/HcpmWDxmzf
