# wait_tcp

It lets explicit ordering of container startup. Like wait-for-it.sh, but smaller and specifically made for alpine images :). Some more info here: https://docs.docker.com/compose/startup-order/ .


## Usage example

Add this somewhere in Dockerfile:

```Dockerfile
RUN    wget -O /bin/wait_tcp https://raw.githubusercontent.com/kopchik/wait_tcp/master/wait_tcp \
    && chmod +x /bin/wait_tcp
```

Then predent your command with `wait_tcp <host to wait> <port>`:
```yml
version: "3"
services
  some_service:
  ...
  command: >-
      wait_tcp somehost 1194
      && echo iptables ...
```
