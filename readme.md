# Home-Assistant-Discord-bot

## Commands

Replace ! with your prefix  
() = Required   [] = Optional

* `!state (entity_id)` Shows the state of the entity
* `!light_on (entity_id without light.)` Turns the light on
* `!light_on_color (entity_id without light.) (R) (G) (B) (Brightness)` Turns the light on with the given RGB values
* `!light_off (entity_id without light.)` Turns the light off
* `!switch_on (entity_id without switch.)` Turns the switch on
* `!switch_off (entity_id without switch.)` Turns the switch off
* `!alexa (message)` Currently in development

## Installation

### Requirments

* Node.js
* NPM

### Installation

You must go into the folder with the files and then execute the following commands

* `npm install` To install the Packages
* You must replace line 132 in /node_modules/node-homeassistant/index.js with `this.ws.send(JSON.stringify(data).replace('"[', '[').replace(']"', "]"))` for the light_on_color command to work
* Edit config.json
* `npm start` To start the bot
