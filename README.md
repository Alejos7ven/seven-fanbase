# seven-fanbase
This is a simple Fanbase tool for the STEEM Blockchain to upvote x accounts each 24 hours.

# Requeriments

* NodeJS: "dotenv", "moment", "mysql", "node-fetch", "steem"
* PhpMyAdmin
* PM2

# Installation

Create a new MySql Database and import ```fanbase.sql``` in your phpmyadmin.

You will see 3 tables:

* Queue
* Settings
* Trailers

Go to ```settings``` table and add a new row. You will can set an STEEM username, a posting key, enable (0/1, where 1 is enabled) and the min voting power to vote. This account will be the curator account.

On the ```trailers``` table you will can add as much accounts as you want and set a fixed percentage, these accounts will be voted once 24 hours with the percentage used.

Create a ```.env``` file with the following structure:

> DB_USER=root 
> DB_PASSWORD=password
> DB_NAME=fanbase
> DB_HOST=localhost

and set your MySql Db connection.

Run the script using PM2 just do:

```pm2 start index.js --cron "*/15 * * * *"```

You are done