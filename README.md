# Running an RClone Mount at MacOS System Startup

Here's my plist (property list) example for mounting your RClone remote to MacOS as a system drive/folder. I've implemented local caching to allow for failures and a 40M bandwidth limit which you can easily change.

* First ensure that you've installed RClone and have configured your remote that you wish to mount to MacOS. 
* Also make sure you have installed OSXFUSE: http://osxfuse.github.io


## Usage

1. Take my plist file and place it in `/Library/LaunchDaemons`
2. Edit the file as nescesarry, changing the remote name (`gdrive:`) and any references to `<USER>`
3. Create a folder `/Users/<USER>/Encrypted` (or something else of your chosing)
4. Add the property list file into launchctl: `sudo launchctl load -w /Library/LaunchDaemons/com.gdrive.plist`
5. Start the service you just created: `sudo launchctl start -w /Library/LaunchDaemons/com.gdrive.plist`

You can stop the service using the `stop` command or remove it from your system using `unload`

Check `Users/<USER>/Documents/logs` for error logging.
