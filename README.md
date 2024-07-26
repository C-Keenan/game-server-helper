# Game Server Helper

## Announcements

### Announcement 07/26/2024

- Working on an idea to run a postgresql database, or potentially nosql/sqlite, as I would prefer not having to run sudo in the main script for the donation ticker. Donation message will not be moving to sql database and database will NOT be getting synced with anything outside of your local network if/when implemented.

- Potential use cases for the database are, currently, as follows

    1. Non-'sudo' implementation of donation-ticker to show a donation reminder message when you've run the 'command' if '$dt' equals '30'

    1. User logging to show when a user runs the command and what game or service they interacted with so server admins can facilitate support to users

- No other ideas are currently in the works but I will keep this announcement section up to date with progress. If you have any suggestions or ideas please don't hesitate to contact me at dev+gsh-feature-requests@lollypopstealer.com as I don't really go on github unless I'm merging the 'nightly' branch to the main branch.

## Release Notes

### Release 07/25/2024

- Added a donation reminder statement to the main 'gsh' function. You can disable it by editing the "/usr/gsh/environment/donation-ctrl.env" file and setting the "$donationmessage" variable to '1'. This file will never be overwritten as it is created at install or at the latest update.

- Docker container environment files will no longer be overwritten either as they are made and set at install/update if they do not exist, hopefully this saves you the frustration of needing to reset your minecraft rcon password every time there is an update. Apologies for the frustrations.

### Release 07/21/2024 P2

- Updated timer component of factorio down command to be more accurate to the actual second no promises that it will be completely accurate but is definitely closely accurate with the clock timer on my phone

### Release 07/21/2024

- Added minecraft to the list of supported game servers

- Has the ability to be used with rcon. Please set a secure RCON Password in the minecraft.env file located at /usr/gsh/docker/minecraft and also uncomment the "# - 25575:25575" found in the docker-compose.yml located in the same directory

- If you set the RCON Password after updating to this version please be sure to ALWAYS say yes when running the update script in the future as it will be over-written by the script

- Symbols in RCON Password not supported when setting environment variable please use alpha-numerics only (letters and numbers)

- factorio help text updated to show new '--now' option

### Release 07/20/2024

- Added a '--now' function to gsh script, use it to immediately stop the factorio container without waiting. Useful if you've just had an autosave happen or you have had something happen that you don't want to be saved to your save file.