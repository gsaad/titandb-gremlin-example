# titandb-gremlin-example
gremlin script pour initialiser une db sous titan-cassandra

##Téléchargement
[Titan 1.0.0 - hadoop 1](http://s3.thinkaurelius.com/downloads/titan/titan-1.0.0-hadoop1.zip)

## Script

- Titan shell : 
  
```
cd titan-1.0.0-hadoop1
./bin/titan.sh start
Forking Cassandra...
Running `nodetool statusthrift`. OK (returned exit status 0 and printed string "running").
Forking Elasticsearch...
Connecting to Elasticsearch (127.0.0.1:9300). OK (connected to 127.0.0.1:9300).
Forking Gremlin-Server...
Connecting to Gremlin-Server (127.0.0.1:8182). OK (connected to 127.0.0.1:8182).
Run gremlin.sh to connect.
```
- Gremlin shell - initialisation d'un graphe titan/cassandra   : 
``` 
./bin/gremlin.sh

         \,,,/
         (o o)
-----oOOo-(3)-oOOo-----
plugin activated: aurelius.titan
plugin activated: tinkerpop.server
plugin activated: tinkerpop.utilities
plugin activated: tinkerpop.hadoop
plugin activated: tinkerpop.tinkergraph
gremlin> graph = TitanFactory.open('conf/titan-cassandra-es.properties')
==>standardtitangraph[cassandrathrift:[127.0.0.1]]
```
- Ajout d'un noeud : 
``` 
gremlin> rerA = graph.addVertex( "name", "RER A", "type", "RER");
==>v[4224]
gremlin> g = graph.traversal()
==>graphtraversalsource[standardtitangraph[cassandrathrift:[127.0.0.1]], standard]
gremlin> g.V(4224).properties()
==>vp[name->RER A]
==>vp[type->RER] 
``` 
