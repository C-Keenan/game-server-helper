# Game Server Helper

## Release Notes

### Release 07/21/2024

- Added minecraft to the list of supported game servers

- Has the ability to be used with rcon. Please set a secure RCON Password in the minecraft.env file located at /usr/gsh/docker/minecraft and also uncomment the "# - 25575:25575" found in the docker-compose.yml located in the same directory

- If you set the RCON Password after updating to this version please be sure to ALWAYS say yes when running the update script in the future as it will be over-written by the script

- Symbols in RCON Password not supported when setting environment variable please use alpha-numerics only (letters and numbers)

- factorio help text updated to show new '--now' option

### Release 07/20/2024

- Added a '--now' function to gsh script, use it to immediately stop the factorio container without waiting. Useful if you've just had an autosave happen or you have had something happen that you don't want to be saved to your save file.