# ![colyseus](examples/logo.png?raw=true)

Minimalistic MMO Game Server for Node.js.

> Colyseus is in early stage development. Don't expect a mature and
> ready-to-scale piece of software here

## Features

- WebSocket-based communication
- Match-making
- Binary data transfer (through [msgpack](http://msgpack.org))
- Delta-encoding (through [fast-json-patch](https://github.com/Starcounter-Jack/JSON-Patch/) - [RFC6902](http://tools.ietf.org/html/rfc6902))

TODO:

- "area of interest" updates/broadcasts

## Room API

### Callbacks

- onJoin (client) - *when a client joins the room*
- onLeave (client) - *when a client leaves the room*
- onMessage (client, data) - *when a client send a message*
- update () - *update method, usually to broadcast patch state*
- dispose () - *cleanup callback, called after there's no more clients on the room*

### Methods

- lock() - *lock the room to new clients*
- unlock() - *unlock the room to new clients*
- send(client, data) - *send data to a particular client*
- broadcast(data) - *send data to all connected clients*
- sendState(client) - *send current state to a particular client*
- broadcastState() - *send current state to all clients*
- broadcastPatch() - *send patched (diff) state to all clients*

## Production usage

- [PM2](https://github.com/Unitech/pm2)

https://devcenter.heroku.com/articles/node-best-practices
http://pm2.keymetrics.io/docs/usage/specifics/#babeljs

## Options to consider

node --optimize_for_size --max_old_space_size=920 --gc_interval=100 server.js

Game Server inspiration implementation references:

- https://www.cs.cmu.edu/~ashu/papers/cmu-cs-05-112.pdf
- http://dev.louiz.org/projects/batajelo/wiki/Server_architecture
- https://cloud.google.com/solutions/gaming/dedicated-server-gaming-solution/

## License

MIT
