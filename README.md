# ti-autobahn

[Appcelerator Titanium Mobile](http://www.appcelerator.com) autobahn.js port to support WAMP protocol.

See [AutobahnJS](https://github.com/tavendo/AutobahnJS) for further information.

##Installation

You need to install the [tiws Module](https://github.com/iamyellow/tiws) in order to enable websocket support in your application.

Then in your library folder add the ti-autobahn code (eg. for alloy project it is `app/lib/`)

##Example

With this sample code you should see in the log the comunication made with a WAMP compatible server

```
    // your WAMP compatible server
    var wsuri = 'ws://127.0.0.1:8080/';

    var ab = require("ti-autobahn/autobahn");

    ab.debug(true, true, true, true);
    ab.connect(wsuri,

        function (session) {

           // asynchronous RPC, returns promise object
           session.call("sample/add_func", 23, 7).then(

              // RPC success callback
              function (res) {
                 console.log("got result: " + res);
              },

              // RPC error callback
              function (error, desc) {
                 console.log("error:");
                 console.log(desc);
              }
           );
        },

        // WAMP session is gone
        function (code, reason) {
           console.log("Session gone!");
           console.log(reason);
        }
    );

```

##License

MIT
