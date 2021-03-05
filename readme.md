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
* `!alexa (message)` Says message through alexa. Instalation: Look <#alexa>

## Installation

### Requirments

* Node.js
* NPM
* [Alexa Media Player in Home Assistant](https://github.com/custom-components/alexa_media_player) (only if you want to use !alexa)

### Installation

You must go into the folder with the files and then execute the following commands

* `npm install` To install the Packages
* You must replace line 132 in /node_modules/node-homeassistant/index.js with `this.ws.send(JSON.stringify(data).replace('"[', '[').replace(']"', "]"))` for the light_on_color command to work
* Edit config.json
* `npm start` To start the bot

### Alexa

You need two helpers and one automation for !alexa to work

#### Helpers

1. Toggle Helper with the name: alexa_say
2. Text Helper with the name: alexa_say

#### Automation

Create an automation and open the automation yaml editor and paste in the code below

```alias: Alexa_Say
description: ''
trigger:
  - platform: state
    entity_id: input_boolean.alexa_say
    to: 'on'
condition: []
action:
  - service: notify.alexa_media_NAME
    data:
      data:
        type: tts
      target:
        - media_player.NAME
      message: '{{ states(''input_text.alexa_say'') }}'
  - service: input_boolean.turn_off
    data:
      entity_id: input_boolean.alexa_say
mode: single
```

Replace "NAME" with the name of your alexa