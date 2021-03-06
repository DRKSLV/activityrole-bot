# activityrole-bot
A Discord Bot that will assign roles based on the Games that a Member is currently playing.

The Bot needs the MANAGE_ROLES Permission on your Server, and only Members with Roles that are **lower** in the [Hierarchy](https://support.discordapp.com/hc/en-us/articles/214836687-Role-Management-101) will be assigned Activity-Roles(tm).

Roles are assigned to a member when a Game is opened, closed or refreshes it's Presence on Discord. 
Players that we're already playing when the bot looged in won't be assigned a role (yet).

## Security Considerations and Quirks
There are a few quirks too be considered:
- Games that are not registered as a [Discord Application](https://discordapp.com/developers/docs/intro) are ignored by the bot (most of the are dw)
  - this prevents members from giving themselves arbritrary roles by manipulating `Settings>Game Activity`
- The Bot will assign any role matching the Name of the Activity
  - Make sure no important Admin/Moderator Role has a name matching **any** game registered with Discord
  - If you have a role that should **never** be tampered with by the bot, make sure that it's above the Bot's Role in the [Hierarchy](https://support.discordapp.com/hc/en-us/articles/214836687-Role-Management-101)
- Some Games (annoyingly) register both their Launcher AND the actual Game with Discord, resulting in multiple roles being created and assigned to the ones playing it.
- You can instruct the bot to use a specific **alias** instead of the default name, by editing `config.json`
  - This way you can prevent Games from showing up twice and use creative Rolenames
  - the config file is already preconfigured to rename Rainbow Six Siege and it's annoying duplicate

## Optaining a Discord API token
You will need a token to run the bot.
1. Create a Discord [Application](https://discordapp.com/developers/applications)
2. Navigate to the `Bot` Tab on the right side.
3. Select "add Bot" and confirm.
4. And finally: Reveal and copy the token!

## Brief Setup Guide
1. Provide a Discord API access token in `config.json`
2. Install dependencies `npm install`
3. Run the bot with `node .`

Alternatively, to run as a docker:
1. Pull from [DockerHub](https://hub.docker.com/r/drkslv/activityrole-bot)
2. Set (docker)Enviroment Variable ACCESS_TOKEN to your token (duh)
3. Run Docker Container

> Note: When using the Docker Image from DockerHub, you won't easily be able to edit `config.json`.
>       You might have to build the Image yourself
