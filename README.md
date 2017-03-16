# homebridge-temperature-machine

[HomeBridge](https://github.com/nfarina/homebridge) plugin for the [temperature-machine](https://github.com/tobyweston/temperature-machine).

## Installation

You'll need one or more temperature-machines setup. These are Pi based temperature monitoring and tracking things using the software at [https://github.com/tobyweston/temperature-machine](https://github.com/tobyweston/temperature-machine).

Build you're own temperature data logger for around $12 ([instructions](http://baddotrobot.com/blog/2016/03/23/homebrew-temperature-logger/)) then add HomeKit support with this plugin.

1. Setup your temperature-machine(s), see the [blog post](http://baddotrobot.com/blog/2016/03/23/homebrew-temperature-logger/) for help
1. Install HomeBridge with `npm install -g homebridge`
1. Install this plugin with `npm install -g homebridge-temperature-machine`

## Plugin Development

For some general information on building your own plugin, see []PLUGIN.md](PLUGIN.md)