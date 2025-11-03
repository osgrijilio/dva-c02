# Docker notes

Tag your image with a name:

```bash
docker build -t tag-ubuntu-os .
```

Name your container:

```bash
docker run -it --name instance2 --rm tag-ubuntu-os
```

```text
CONTAINER ID   IMAGE           COMMAND       CREATED          STATUS          PORTS     NAMES
2294384829ca   tag-ubuntu-os   "/bin/bash"   6 seconds ago    Up 5 seconds              instance2
1628dc281283   tag-ubuntu-os   "/bin/bash"   29 seconds ago   Up 29 seconds             instance1
```

```bash
docker pull container-registry.oracle.com/database/free:23.9.0.0-lite-arm64
```

```bash
docker run --name oracle-free-23ai \
  -p 1521:1521 \
  -e ORACLE_PWD=OracleRatas \
  container-registry.oracle.com/database/free:23.9.0.0-lite-arm64
```
