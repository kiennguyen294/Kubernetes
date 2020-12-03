# Dockerfile
## Introduce
Dockerfile is text file that contains all the commands/set of instructions a user to create an image
![Dockerfile image](/images/dockerfile.png)

## Format of Dockerfile
### ADD
Copies new files, directories or remote file URLs from **src** and adds them tho the filesystem of image at the path **dest**.

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
The COPY instruction copies new files or directories from <src> and adds them to the filesystem of the container at the path <dest>.

Form:
```
COPY [--chown=<user>:<group>] <src>... <dest>
COPY [--chown=<user>:<group>] ["<src>",... "<dest>"]
```

### ENV
Instruction sets the environment variable
### EXPOSE
### FROM
### LABEL
### STOPSIGNAL
### USER
### VOLUME
### WORKDIR
### RUN
### CMD
### ENTRYPOINT
### ARG
### SHELL