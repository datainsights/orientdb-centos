# orientdb-centos

A `Dockerfile` for creating an OrientDB image on top of the official CentOS distribution (`centos:latest`).

Multiple tag exist for different versions of OpenJDK:

- `latest` to build the latest OrientDB (same as `2.0.2-SNAPSHOT`)
- `2.0.2` to build OrientDB version 2.0.2 (stable)
- `2.0-rc1` to build OrientDB version 2.0-rc1 (unstable)

## How to Pull from Docker Hub

    docker pull lighthopper/orientdb-centos:latest

## How to Build

    git clone https://github.com/kadishmal/orientdb-centos.git
    cd orientdb-centos
    docker built -t lighthopper/orientdb-centos:latest .

## How to Run

    docker run --name orientdb -d -p 2480:2480 -p 2424:2424 lighthopper/orientdb-centos:<tag>

Replace `<tag>` with any of the available tags.

#### Root password

When the OrientDB server is started for the first time, it sets an autogenerated password for the `root` user. You need to know this password in order to manage the server and/or create new databases. In order to get this `root` password run the following commands after the container is started.

    $ docker ps
    CONTAINER ID        IMAGE                                 COMMAND                CREATED             STATUS              PORTS                                            NAMES
    4768f68e7f64        lighthopper/orientdb-centos:2.0.2   "/usr/local/bin/serv   8 seconds ago       Up 6 seconds        0.0.0.0:2424->2424/tcp, 0.0.0.0:2480->2480/tcp   orientdb

Copy the container ID `4768f68e7f64`, then execute the following command in order to print out the root password.

    $ docker exec 4768f68e7f64 cat /opt/orientdb/config/orientdb-server-config.xml | grep "password="
        <user resources="*" password="E56A77F90A8735B005DE743294C35CB9264B3B17183A2B354AF54E3D3599065A" name="root"/>
        <user resources="connect,server.listDatabases,server.dblist" password="guest" name="guest"/>

Here `E56A77F90A8735B005DE743294C35CB9264B3B17183A2B354AF54E3D3599065A` is the password for the `root` user.

## License

MIT