## couch_ws

couch websocket proxy via socket-pouch. 

this will setup a couchdb os daemon (see: http://docs.couchdb.org/en/2.1.1/config/externals.html) that's a simple nodejs proxy server for http(s):// ws(s):// connections! couchdb will start (and keep alive) an external process (couch_ws.js) that will listen/proxy on port 8888. 

*note*: a route for `/up` (like couchdb does) because i use a loadbalancer and this is a health-check. i route traffic from a https subdomain to a port (e.g. https://couch.my.domain goes to 5984 and couchws.my.domain goes to 8888). 


### docker notes:

```sh
docker build -t 3dwardsharp/couch_ws .
docker run -t -i -p 5984:5984 -p 8888:8888 3dwardsharp/couch_ws
docker login
docker push 3dwardsharp/couch_ws
```

