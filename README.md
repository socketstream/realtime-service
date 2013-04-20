# Realtime Service

**Status: Usable, but a work in progress. Feedback encouraged!**

An open standard describing a mix of client and server-side code designed to communicate over a persistent connection. This will usually be a WebSocket connection, but any [Realtime Transport](https://github.com/socketstream/realtime-transport) module is compatible.

Realtime Services are designed to be very easy to understand, write, test and share on `npm`.

Each service is defined in the simplest possible way: as a plain old JavaScript object. Here's a simple example:

```js
var service = {
  client: function(client) {
    client.onmessage = function(msg) {
      console.log('Message in from server:', msg);
    }
  },

  server: function(server) {
    setInterval(function(){
      server.broadcast('Hello!');  
    }, 1000);
  }
}
```

## Examples Services

(all alpha quality for now)

[**rts-rpc**](https://github.com/socketstream/rts-rpc)  
[**rts-pubsub**](https://github.com/socketstream/rts-pubsub)  
[**rts-livereload**](https://github.com/socketstream/rts-livereload)


## Features

* super-simple: services are just JavaScript objects
* client and server code can expose APIs to be called by the app
* easy to write tests
* the [realtime-service-client](https://github.com/socketstream/realtime-service-client) can run in a browser or separate node process
* each service has it's own directory to store files (e.g. model definitions)
* efficiently handles callbacks, even for non-JSON messages
* services can optionally use Sessions (provided by the server)
* server is notified when a client connect/disconnect (allowing cleanup)
* services can send JavaScript assets to the browser
* optionally handles JSON encoding/decoding for you
* provides a standard logging API
* ultra light weight client-side code (for sending to browser)


Realtime Services **do not** care about:

* the underlying transport layer (abstracted away by [Realtime Transport](https://github.com/socketstream/realtime-transport))
* how code is delivered to the browser (left to the framework or app to implement)


## Implementations

Realtime Services are currently implemented in [**Prism**](https://github.com/socketstream/prism), the realtime server component of SocketStream 0.4. 

As other frameworks / toolkits implement them, they will be listed here.


## Contents

Realtime Services consist of

1. This - the server-side library
2. The [realtime-service-client](https://github.com/socketstream/realtime-service-client) module
3. The Realtime Server Spec (Coming soon!)


## API

Coming soon!


## History

Realtime Services are the evolution of an idea called "Request Responders" which first appeared in SocketStream 0.3. Despite a horribly clunky API, the idea proved to be popular with third-party modules for Backbone and Angular soon appearing.

Realtime Services will be one of the key features of SocketStream 0.4. However, I hope by ensuring the spec is a simple as possible (with minimal dependencies), other frameworks will support Realtime Services in the future. The ultimate goal is an ecosystem of reusable components using 100% standard `npm` packages.


## Licence

MIT