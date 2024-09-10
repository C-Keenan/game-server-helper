# Game Server Helper

## Announcements

### Announcement 09/10/2024

Working on getting bugs worked out for the Satisfactory 1.0 release. I will have the updated files push to this repo asap.

### Announcement 08/28/2024

- Idea still WIP and currently stalled due to personal reasons, however, I am planning to start it back up within a month or so. I'll keep you informed as best as I can.

- Please see 'Release 08/28/2024' for newly added features and changes to the current implementation.

### Announcement 07/26/2024

- Working on an idea to run a postgresql database, or potentially nosql/sqlite, as I would prefer not having to run sudo in the main script for the donation ticker. Donation message will not be moving to sql database and database will NOT be getting synced with anything outside of your local network if/when implemented.

- Potential use cases for the database are, currently, as follows

    1. Non-'sudo' implementation of donation-ticker to show a donation reminder message when you've run the 'command' if '$dt' is evenly divisible by '30'

    1. User logging to show when a user runs the command and what game or service they interacted with so server admins can facilitate support to users

- No other ideas are currently in the works but I will keep this announcement section up to date with progress. If you have any suggestions or ideas please don't hesitate to contact me at dev+gsh-feature-requests@lollypopstealer.com as I don't really go on github unless I'm merging the 'nightly' branch to the main branch.

## Release Notes

### Release 08/28/2024

- Added "restart" and "recreate" options to all game server commands

- Changed to Jquery processing for timer function for 'Factorio' as I realized the limitations of the colrm command as I had it configured before

- Changed to acl control of env instead of sudo. The command, if you need to set up more users for access, is `setfacl -m u:${USER}:rw /usr/gsh/environment/donation-ticker.env` . Replace `${USER}` with the username of the user. If not running as root you will need 'sudo' privledges to edit the acl rules, as set forth by the acl package. If adding more than the installing user you may want to add the alias to their `.bashrc` or `.bash_aliases` with the command `"alias gsh='bash /usr/gsh/script-files/gsh'" >> ~/.bashrc` .

- A more in depth installer shall be released soon that will account for system-wide aliasing for this script

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