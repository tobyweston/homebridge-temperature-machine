# HomeBridge Plugin Development

## Bootstrap a Platform Plugin

For a Platform plugin, you can copy the [example](https://github.com/nfarina/homebridge/tree/master/example-plugins/homebridge-samplePlatform) from the [nfarina/homebridge](https://github.com/nfarina/homebridge) into a new Git repository.

So you'll see something like this at the terminal

    $ mkdir homebridge-example-plugin
    $ cd homebridge-example-plugin
    $ cp ../homebridge/example-plugins/homebridge-samplePlatform/* .
    $ git init
    $ ll
    drwxr-xr-x  10 toby  staff   340 16 Mar 18:43 ./
    drwxr-xr-x  26 toby  staff   884 16 Mar 18:28 ../    
    drwxr-xr-x  26 toby  staff   884 16 Mar 18:30 .git    
    -rw-r--r--   1 toby  staff  7397 16 Mar 18:30 index.js
    -rw-r--r--   1 toby  staff   467 16 Mar 18:30 package.json


## Test the Sample Platform 

At this point, let's see if we can start the plugin up on the HomeBridge server.

    $ npm install -g homebridge
    
You'll need full fat xcode installed else you'll see things like this building dependencies.

    > mdns@2.3.3 install /Users/toby/.npm-global/lib/node_modules/homebridge/node_modules/mdns
    > node-gyp rebuild
    
    xcode-select: error: tool 'xcodebuild' requires Xcode, but active developer directory '/Library/Developer/CommandLineTools' is a command line tools instance
    
HomeBridge may look like it's installed but you'll likely have problems. Run `npm uninstall -g homebridge` if you get the above and install xcode before continuing.


### Setup Development Environment

From your new plugin's folder, run the following.

    $ DEBUG=* homebridge -D -P .

You should see something like this (don't bother trying to connect iOS to it yet).

cheetah:homebridge-temperature-machine toby$ DEBUG=* homebridge -D -P .
[3/16/2017, 8:08:09 PM] Loaded plugin: homebridge-example-plugin
homebridge API version: 2.1
[3/16/2017, 8:08:09 PM] Registering platform 'homebridge-samplePlatform.SamplePlatform'
[3/16/2017, 8:08:09 PM] ---
[3/16/2017, 8:08:09 PM] config.json (/Users/toby/.homebridge/config.json) not found.
Load homebridge-samplePlatform.SamplePlatform
[3/16/2017, 8:08:09 PM] [homebridge-samplePlatform.SamplePlatform] SamplePlatform Init
Scan this code with your HomeKit App on your iOS device to pair with Homebridge:
                       
    ┌────────────┐     
    │ 031-45-154 │     
    └────────────┘     
                       
  Accessory [Homebridge] Creating new AccessoryInfo for our HAP server +0ms
  Accessory [Homebridge] Creating new IdentifierCache +5ms
[3/16/2017, 8:08:10 PM] [homebridge-samplePlatform.SamplePlatform] DidFinishLaunching
[3/16/2017, 8:08:10 PM] [homebridge-samplePlatform.SamplePlatform] Server Listening...
  EventedHTTPServer Server listening on port 51015 +13ms
[3/16/2017, 8:08:10 PM] Homebridge is running on port 51015.

Success!

## The Sample Platform Plugin

The sample plugin registers as `homebridge-samplePlatform.SamplePlatform` above and starts up a HTTP server that will accept `GET` requests to the following.

    http://localhost:51015/add
    http://localhost:51015/reachability
    http://localhost:51015/remove

If you fire a request from the terminal like this (or from your favorite browser).

    curl -X GET "http://localhost:18081/add"

You should see something like the following in the terminal.

    [3/16/2017, 8:10:35 PM] [homebridge-temperature-machine.TemperatureMachinePlatform] Server received [object Object]
    [3/16/2017, 8:10:35 PM] [homebridge-temperature-machine.TemperatureMachinePlatform] Add Accessory
      EventedHTTPServer [::1] Client connection closed +2m
      EventedHTTPServer [::1] HTTP connection was closed +1ms
      EventedHTTPServer [::1] HTTP server was closed +0ms


## Start Hacking

1. Hack
1. ?
1. Profit

## Development Cycle

Whilst HomeBridge is running, it won't reload your plugin as you hack. Assuming you're using the `DEBUG=*` trick above.

Instead, you'll have to `ctrl + x` and restart for changes to take affect.