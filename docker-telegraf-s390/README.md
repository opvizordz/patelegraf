# Steps

## Clone git repository
`git clone`

## Build local docker container
`docker build -t opvizor/s390alpine-telegraf:latest . `

## Run Container without special setup
`docker run -d -v $(pwd)/config:/etc/telegraf --name s390telegraf opvizor/s390alpine-telegraf:latest`

## Run Container including docker information (if docker is running)

```shell
docker run -d -v $(pwd)/config:/etc/telegraf \
-v /var/run/utmp:/var/run/utmp:ro \
-v /var/run/docker.sock:/var/run/docker.sock -v /:/hostfs:ro \
-v /etc:/hostfs/etc:ro -v /proc:/hostfs/proc:ro -v /sys:/hostfs/sys:ro \
-e HOST_ETC=/hostfs/etc -e HOST_PROC=/hostfs/proc -e HOST_SYS=/hostfs/sys \
-e HOST_MOUNT_PREFIX=/hostfs \
--name s390telegraf \
opvizor/s390alpine-telegraf:latest
```
