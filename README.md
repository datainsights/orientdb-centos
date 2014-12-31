# orientdb-docker

A `Dockerfile` for creating an OrientDB image on top of the official CentOS distribution (`centos:latest`).

Multiple tag exist for different versions of OpenJDK:

- `2.0-rc1` to build OrientDB version 2.0-rc1 (unstable)

## How to Build

    git clone https://github.com/kadishmal/orientdb-docker.git
    cd orientdb-docker
    docker built -t lighthopper/orientdb-docker:2.0-rc1 .

## How to Run

    docker run --name orientdb -d -p 2480:2480 -p 2424:2424 lighthopper/orientdb-centos:<tag>

Replace `<tag>` with any of the available tags.

## License

MIT