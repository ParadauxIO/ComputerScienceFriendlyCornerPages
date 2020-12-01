# The Computer Science Friendly Bot

The Computer Science Friendly Bot is a discord bot which oversees The Computer Science Friendly Corner. It serves as a key moderation tool to ensure the rules are upheld, and the moderators are able to moderate. 

## Development Process

The Bot is written in Java using [JDA](https://github.com/DV8FromTheWorld/JDA) (**J**ava **D**iscord **A**PI) version 4.2.0_214 shaded using [Maven](https://maven.apache.org), checked against [paradaux_checks.xml](https://cdn.paradaux.io/static/paradaux_checks.xml) via [checkstyle](https://github.com/checkstyle/checkstyle) and build using [JenkinsCI](https://ci.paradaux.io/job/Computer%20Science%20Friendly%20Bot/) to then be deployed to a [Hetzner Cloud](https://www.hetzner.com/cloud) [VPS](https://en.wikipedia.org/wiki/Virtual_private_server) as the production machine. 

Contribution from outside developers is not only welcomed, but highly requested. Please see [CONTRIBUTING.md](https://github.com/ParadauxIO/ComputerScienceFriendlyBot/blob/main/CONTRIBUTING.md) for more information. 

The Project can be found on GitHub [here](https://github.com/ParadauxIO/ComputerScienceFriendlyBot). 


## Features
- Domain-restricted email verification, with database-backed verification profiles.
- Comprehensive Moderation logging, with ID-driven schema, for future lookups and responses
- Mod-mail system for messaging a moderation team as a single unit, and creating a ticket-like process, allowing the moderation team and the particular user to respond. 
- Warning, kick and ban logging. 
- Privacy-first logging. No personally identifiable information is intentionally stored, and is removed when we are made aware of such information. 

## Planned Features
Planned features are controlled via the [github issues page](https://github.com/ParadauxIO/ComputerScienceFriendlyBot/issues).
- Chat filter preventing the use of highly sensitive language. 
- Bot-controlled announcements via embeds
- Code Quality checks, github badges and contribution instructions
- Ability for users to request a copy of the data stored on them. 
- Ban appeal process
- Lockdown command to prevent a user's access to the discord for a period of time. 
- Reaction-roles. 
- Project-wide javadocs

