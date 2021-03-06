# lorebot
Lorebot is a Discord bot written in JS to support a text-based RPG called [Arctic](http://mud.arctic.org).  
The bot will respond to commands prefixed by the prefix '!' specified in config.json.  
The original Lorebot was written in 2003 for IRC by Troggs and subsequently ported to Skype.  
Lorebot will also capture lores pasted in Discord chat, either singly or pasted in bulk.  
Lorebot was developed on Ubuntu Linux and is intended to run on Linux, however it can run on Windows.

## Messaging Lorebot on Discord
Discord is case sensitive so capitalize the B in LoreBot to message and use LoreBot.  
Lorebot can be found on the following Discord server: https://discord.gg/vNuGEpA


```
@LoreBot#2504
```

## Installation
```
git clone https://github.com/longhorn09/lorebot.git
cd lorebot
mv config-sample.json config.json
npm install
npm start
```



## Commands
* !stat
* !brief
* !help
* !roll
* !query
* !version
* !who  
* !whoall
* !recent

## Dependencies
```
# NodeJS, a javascript runtime and package manager
sudo apt-get update -y
sudo apt-get install nodejs
sudo apt-get install npm

# MySQL database required
sudo apt-get install mysql-server
sudo mysql_secure_installation

# For timestamp formatting in MySQL format, moment().format("YYYY-MM-DD HH:mm:ss")
npm install moment

# For ES6+ functionality, primarily used for string.padEnd()
npm install --save babel-polyfill


```

## Run Lorebot as a service

The following will daemonize lorebot.  
This will allow lorebot to continue running even after logging off the terminal.  
It's not required to run lorebot, but highly recommended. 

```
npm install -g forever
forever start lorebot.js
```
## Loading the SQL database

Lorebot uses MySQL on the backend.   
Currently lorebot has over 4,800 lores.   
The easiest way to populate the Lorebot database with lores is to run the following SQL script:  

```./lorebot/sql/load_lorebot_db.sql```

The SQL script will populate the `Person` and `Lore` tables.      
You may still need to load the stored procedures as well.  
Relevant scripts for stored procedures can be found in `./lorebot/sql/`

## Bulk loading lores from a text file

For lores accumulated in a plain text file, Lorebot has a utility [load_lores.js](https://github.com/longhorn09/lorebot/blob/master/utility/load_lores.js) to facilitate loading lores into Lorebot.  
Currently the specified lore text file to load is hard-coded near the bottom in [load_lores.js](https://github.com/longhorn09/lorebot/blob/master/utility/load_lores.js) and can be tweaked to suit your needs.  
```const INPUT_FILE = path.join(__dirname,'lores_2016_wipe.txt');```  
This utility will load lores directly from a text file into the MySQL database and bypass Discord parsing.  

## Examples
```
!brief bronze.shield
!stat bronze.shield
```
![Discord Lorebot](/lorebot.PNG?raw=true "Example of brief and stat")

## License
Lorebot is distributed under the [MIT license](https://github.com/longhorn09/lorebot/blob/master/LICENSE.md).
