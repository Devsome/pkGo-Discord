# pkGo Discord Bot

Based on the [modrzew/pokeminer](https://github.com/modrzew/pokeminer).

## For what ?

Sending you a Discord Message for Pokémon you want.

### Config

token: Discord Bot token
app_id: Your Discord Application ID
channelID: The ChannelID the bot should write the message
getServer: The Server IP pokeminer is running on.

```json
{
	"token": "",
	"app_id": "",
	"channelID": "",
	"getServer": "localhost",
	"CheckMinutes": 2,
	"pokeShow": [3, 6, 9, 26, 38, 40, 51, 76, 94, 95, 104, 107, 110, 115, 122, 123, 128, 132, 139, 141, 142, 143, 148, 149, 150, 151],
	"games": ["Pokémon Go","Pikachu"]
}

```

### Installing

```javascript
npm install discord.js
npm install request
```

## Thanks to

imDevinC https://github.com/ImDevinC/pkgo-discord for the functions
modrzew https://github.com/modrzew/pokeminer for the main repo
