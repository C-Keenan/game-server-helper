# Game Server Helper

## Announcements

### Announcement 10/09/2024

Added update function to the satisfactory branch of the gsh script. This will allow you to update the satisfactory game files easily if you have set the `SKIPUPDATE` variable to true in the `satisfactory.env` file. There are plans for the script to allow you to edit the respective files of the containers and environments with your editor of choice as well however there is currently no timeline by which this feature release is planned. I will keep you updated as to when this feature is released on the [kofi page](https://ko-fi.com/lollypopstealer).

Also added archive function to factorio branch of the gsh script. This allows the user to archive the save files of the factorio server for easy switching to another playthrough of factorio. NOTE: You will need to edit and/or remove any files necessary to change to the playthrough you want play next. There will be a future update containing a feature release to automatically edit certain files and delete the `.zip` files in the save directory however this will need to be deliberated on how best to implement those edits and file deletions to best suit the user.

### Announcement 09/15/2024

Apologies for the wait. The bug I was experiencing seems to have been because Satisfactory was running in a virtualized environment. This can be fixed by passing the name of your CPU to the virtual machine. Please follow your hypervisors documentation on changing how the virtual CPU is named.

In other news, the updated environment file and docker-compose.yml are also provided. Please save a backup of any files that have been changed since the installation as when you run the update script it will overwrite any file with changes, as currently it is just comparing the sha256 hashes of the environment files and since the new environment won't be the same as your changed environment it will overwrite to the defaults recommended by the docker image maintainer. The update script asks you if you'd like to save any changes before proceeding so any losses in data are on you the user to mitigate.

On to a more personal update...

Not long ago my fiance and I experienced a loss in the immediate family and we are currently recovering and realigning our household situation because of that. I apologize for any problems that may have came about, or may still come about, as we work through this tumultuous period in our lives. Please keep your loved ones close as you may never know when you'll see them again.

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

### Release 10/09/2024

- Added `update` function to satisfactory branch of the gsh script

- Added `archive` function to the factorio branch of the gsh script

### Release 08/28/2024

- Added "restart" and "recreate" options to all game server commands

- Changed to Jquery processing for timer function for 'Factorio' as I realized the limitations of the colrm command as I had it configured before

- Changed to acl control of env instead of sudo. The command, if you need to set up more users for access, is `setfacl -m u:${USER}:rw /usr/gsh/environment/donation-ticker.env` . Replace `${USER}` with the username of the user. If not running as root you will need 'sudo' privledges to edit the acl rules, as set forth by the acl package. If adding more than the installing user you may want to add the alias to their `.bashrc` or `.bash_aliases` with the command `echo "alias gsh='bash /usr/gsh/script-files/gsh'" >> ~/.bashrc` .

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