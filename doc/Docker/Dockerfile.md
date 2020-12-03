# Dockerfile
## Introduce
Dockerfile is text file that contains all the commands/set of instructions a user to create an image

![Dockerfile image](/images/1_344Hiafp_XQXYVmuTOQzHA.png)
## Format of Dockerfile
### ADD
Copies new files, directories or remote file URLs from ```<src>``` and adds them tho the filesystem of image at the path ```<dest>```.

Form:
```
ADD [--chown=<user>:<group>] <src>....<dest>
ADD [--chown=<user>:<group>] ["<src>",...."<dest>"]
```
Note:
```
The --chowm is only supported on Dockerfile used to build Linux containers
```
Ex:
```
ADD test.txt relativeDir/
```
### COPY
The COPY instruction copies new files or directories from ```<src>``` and adds them to the filesystem of the container at the path ```<dest>```.

Form:
```
COPY [--chown=<user>:<group>] <src>... <dest>
COPY [--chown=<user>:<group>] ["<src>",... "<dest>"]
```

### ENV
Instruction sets the environment variable ```<key>``` to the value ```<value>```. This value will be in the environment for all subsequent instructions in the build stage.

Form:
```
ENV <key>=<value>
```
Ex:
```
ENV MY_NAME="John Doe" MY_DOG=Rex\ The\ Dog \
    MY_CAT=fluffy
```
Note:

You can view values using command ```docker inspect```, and change them using ```docker run --env <key>=<value>```

### EXPOSE
The EXPOSE instructions informs Docker that the container listens on the specified ports at runtime. You can specify whether the port listions on CP or UDP, and default is TCP.

The EXPOSE does not actually publish the port. If you want to publish port, you can using ```docker run -d```

Form:
```
EXPOSE 80/tcp
EXPOSE 80/udp
```

### FROM
The FROM instruction initializes a new build stage and set the ```Base image``` for subsequent instructions.

Form:
```
FROM [--platform=<platform>] <image> [AS <name>]
or
FROM [--platform=<platform>] <image>[:<tag>] [AS <name>]
or
FROM [--platform=<platform>] <image>[@<digest>] [AS <name>]
```

### LABEL
The LABEL instruction adds metadata to an image. A LABEL is a key-value pair.

Form:
```
LABEL <key>=<value> <key>=<value> <key>=<value> ...
```

### STOPSIGNAL
### USER
### VOLUME
### WORKDIR
### RUN
### CMD
### ENTRYPOINT
### ARG
### SHELL