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

### Change stuff in pokeminer (web.py)

Add the the web.py following: (after that you should see http://ip/discord a json output.)
```python
@app.route('/discord')
def discord():
    """Gets all the PokeMarkers via REST"""
    return json.dumps(get_pokeDiscord())


def get_pokeDiscord():
    data = []

    # Get the Pokemon out of the Database
    session = db.Session()
    pokemons = db.get_sightings(session)
    session.close()

    for pokemon in pokemons:
        name = pokemon_names[str(pokemon.pokemon_id)]
        datestr = datetime.fromtimestamp(pokemon.expire_timestamp)
        dateoutput = datestr.strftime("%H:%M:%S")

        data.append({
            'type': 'pokemon',
            'name': name,
            'key': '{}-{}'.format(pokemon.pokemon_id, pokemon.spawn_id),
            'disappear_time': pokemon.expire_timestamp,
            'icon': 'static/icons/%d.png' % pokemon.pokemon_id,
            'lat': pokemon.lat,
            'lng': pokemon.lon,
            'pokemon_id': pokemon.pokemon_id
        })

    return data		
```

## Thanks to

imDevinC https://github.com/ImDevinC/pkgo-discord for the functions
modrzew https://github.com/modrzew/pokeminer for the main repo
