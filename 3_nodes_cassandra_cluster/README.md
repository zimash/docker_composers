Cassandra uses a lot of memory by default. OOM Killer events are possible.

Configuration files from base image for editing:

```
$ git clone https://github.com/zimash/docker_composers
$ cd docker_composers/3_nodes_cassandra_cluster
$ mkdir -p files/{data,etc}
$ docker run --name cassandra -d --rm cassandra:4
$ docker cp cassandra:/etc/cassandra files/etc/cassandra0x01
$ docker cp cassandra:/etc/cassandra files/etc/cassandra0x02
$ docker cp cassandra:/etc/cassandra files/etc/cassandra0x03
$ docker stop cassandra
```

```
$ docker-compose up -d
$ docker exec cassandra0x01 nodetool status
... doing something with Cassandra cluster
$ docker-compose down
```
